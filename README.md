# AWS Infrastructure Project with Terraform

## Project Overview

This repository demonstrates infrastructure management on Amazon Web Services (AWS) using Terraform. It is organized around a small EC2-focused project and its supporting configuration files.

The repository structure separates Terraform configuration, output information, visual reference material, and project documentation. This makes the codebase easier to navigate and provides a clear starting point for learning cloud infrastructure management.

## Project Structure

```text
.
├── expression-guide.md
├── main.tf
├── Output.png
├── output.tf
├── terraform.tfstate
└── variable.tf
```

### Repository Contents

| File | Purpose |
|---|---|
| `expression-guide.md` | Detailed project documentation maintained separately from this README. |
| `main.tf` | Main Terraform configuration file for the AWS infrastructure. |
| `variable.tf` | Defines configurable input values used by the Terraform configuration. |
| `output.tf` | Defines values Terraform exposes after evaluating the configuration. |
| `Output.png` | Visual reference image associated with the project. |
| `terraform.tfstate` | Local Terraform state file that records information about managed infrastructure. It should be treated as sensitive operational data. |

## Infrastructure as Code

Infrastructure as Code (IaC) is the practice of defining infrastructure through configuration files instead of relying only on manual console changes. Terraform uses providers to communicate with supported platforms and resources to describe infrastructure that it manages.

Keeping infrastructure configuration in files makes changes easier to review, maintain, and track with version control. It also encourages repeatable workflows and helps teams understand how infrastructure is represented.

## AWS Authentication

Terraform's AWS provider authenticates API requests using credentials available to the Terraform process. It does not normally require an interactive login to the AWS Management Console.

In a local development environment, Terraform can often use AWS CLI credentials already configured for the same operating-system user. Common AWS CLI configuration files are:

```text
~/.aws/credentials
~/.aws/config
```

Other supported credential sources may include environment variables, named profiles, IAM roles, and IAM Identity Center. The credential source depends on the environment and the AWS SDK credential resolution process.

### Credential Security

- Never write AWS access keys, secret keys, or session tokens directly into Terraform configuration files.
- Do not commit credentials to GitHub.
- Use least-privilege IAM permissions.
- Prefer temporary credentials or IAM roles where practical.
- If credentials are exposed, rotate them promptly and review repository history.

## State File Security

The `terraform.tfstate` file records Terraform's view of the resources it manages. It is important for Terraform's planning and resource-tracking operations and may contain sensitive infrastructure details.

- Do not publish state files in a public repository.
- Restrict access to local state data.
- Exclude local state files from version control unless a deliberate, secure workflow requires otherwise.
- For team or production environments, consider a remote backend with appropriate access controls and encryption.
- Avoid manually editing the state file.

A `.gitignore` file can include the following entries for common local Terraform artifacts:

```gitignore
.terraform/
*.tfstate
*.tfstate.*
*.tfplan
crash.log
crash.*.log
```

The `.terraform.lock.hcl` file, if generated, is generally useful to keep under version control.

## Cloud Cost Awareness

AWS resources may incur charges based on the selected Region, instance configuration, storage, data transfer, and applicable account offers. Check current AWS pricing and monitor billing while using cloud resources for practice.

Use only the resources you need, review their configuration, and remove unused resources through the workflow that manages them.

## Visual Reference

The repository includes `Output.png` as a visual reference. Keep the image in the same directory as this README if you want it to render below.

![Project output screenshot](Output.png)

## Learning Objectives

This project provides experience with:

- Organizing Terraform files in a small infrastructure repository.
- Understanding how IaC supports repeatable cloud management.
- Recognizing how Terraform accesses AWS credentials.
- Maintaining source-control hygiene for infrastructure projects.
- Protecting Terraform state and sensitive configuration.
- Considering security and cost when working with cloud resources.

## Official References

- [Terraform Documentation](https://developer.hashicorp.com/terraform/docs)
- [AWS Provider Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- [AWS CLI Configuration Files](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)
- [AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
- [Amazon EC2 Documentation](https://docs.aws.amazon.com/ec2/)

---

**Project category:** Cloud Infrastructure / Infrastructure as Code  
**Cloud platform:** Amazon Web Services (AWS)  
**Infrastructure tool:** Terraform
