# My Personal Blog

# Content on this website is still as the same as shown on the template, I am going to modify in the future.

**Live Site:** [https://wuweb.westeurope.cloudapp.azure.com](https://wuweb.westeurope.cloudapp.azure.com)

Welcome to the source code repository for my personal website and blog! This site is built using the static site generator [Hugo](https://gohugo.io/) and is a space where I share my learning experience.

Beyond the content itself, this project also serves as a practical learning ground for implementing DevOps principles. The entire server infrastructure for this blog is managed as code.

## About This Site

*   **Content:** Blog posts, articles, and pages written in Markdown.
*   **Static Site Generator:** Hugo
*   **Deployment:** This site is automatically built and deployed to a self-managed Azure Virtual Machine. The server environment is configured entirely with Ansible and deployment is triggered via a `git push` to a custom hook.

## DevOps & Infrastructure as Code

The real magic behind this site (from a technical perspective) is its **fully automated server setup and deployment pipeline**. I've codified the entire server configuration into a reusable **Ansible Role** in a separate repository.

👉 **[View the Ansible Role for this Server's Configuration](https://github.com/wusshit/my-hugo-vps-deploy-setup.git)** 👈

That repository provides a complete "Infrastructure as Code" solution that:
*   Uses an Ansible playbook to configure a fresh Ubuntu VM from scratch.
*   Installs and configures Nginx, Hugo, and Certbot.
*   Automates HTTPS setup with Let's Encrypt.
*   Creates the server-side `post-receive` Git hook used for the CI/CD pipeline.

This separation helps keep this repository focused on the site's **content**, while the other repository handles the **operational infrastructure**.

## Technologies Used (Site Content - This Repo)

*   **Static Site Generation:** Hugo
*   **Content Management:** Markdown, Git
*   **Version Control:** Git & GitHub

*(For technologies related to deployment, server, and CI/CD, such as **Ansible, Nginx, and Let's Encrypt**, please see the [Server Configuration Repository](https://github.com/wusshit/my-hugo-vps-deploy-setup.git).)*

## Local Development

To run or contribute to the content of this site locally:

1.  Clone this repository:
    ```bash
    git clone https://github.com/wusshit/My-Blog.git
    ```
2.  Navigate into the project directory:
    ```bash
    cd My-Blog
    ```
3.  Ensure you have [Hugo (Extended version)](https://gohugo.io/installation/) installed.
4.  If the theme is managed as a Git submodule:
    ```bash
    git submodule update --init --recursive
    ```
5.  Run the local Hugo server:
    ```bash
    hugo server -D
    ```
    The site will typically be available at `http://localhost:1313`.

## How to Deploy (Overview)

The server that hosts this site was configured using the linked Ansible repository. That setup created a custom Git hook for deployment.

Deployment of *this site's content* is triggered via a `git push` to a specific remote on my Azure VM. The server then automatically builds and deploys the latest version.

1.  Commit local changes to this repository.
2.  Push to `origin` (GitHub).
3.  Push to the `vps-deploy` remote to trigger the live deployment.

## Future Plans

I plan to continue developing both the content of this blog and enhancing its underlying infrastructure:

*   Adding more articles about my understanding and learning experience in my practical exploration.
*   Further exploring DevOps tools like Docker to containerize the application and build process. *(Refer to the [Server Configuration Repository](https://github.com/wusshit/my-hugo-vps-deploy-setup.git) for more specific infrastructure plans.)*
