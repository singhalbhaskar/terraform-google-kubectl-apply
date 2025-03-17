# terraform-google-kubectl-apply

## Description
### Tagline
This is an auto-generated module.

### Detailed
This module was generated from [terraform-google-module-template](https://github.com/terraform-google-modules/terraform-google-module-template/), which by default generates a module that simply creates a GCS bucket. As the module develops, this README should be updated.

The resources/services/activations/deletions that this module will create/trigger are:

- Create a GCS bucket with the provided name

### PreDeploy
To deploy this blueprint you must have an active billing account and billing permissions.

## Architecture
![alt text for diagram](https://www.link-to-architecture-diagram.com)
1. Architecture description step no. 1
2. Architecture description step no. 2
3. Architecture description step no. N

## Documentation
- [Hosting a Static Website](https://cloud.google.com/storage/docs/hosting-static-website)

## Deployment Duration
Configuration: X mins
Deployment: Y mins

## Cost
[Blueprint cost details](https://cloud.google.com/products/calculator?id=02fb0c45-cc29-4567-8cc6-f72ac9024add)

## Usage

Basic usage of this module is as follows:

```hcl
module "kubectl_apply" {
  source  = "terraform-google-modules/kubectl-apply/google"
  version = "~> 0.1"

  project_id  = "<PROJECT ID>"
  bucket_name = "gcs-test-bucket"
}
```

Functional examples are included in the
[examples](./examples/) directory.

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| additional\_networks | Additional network interface details for GKE, if any. Providing additional networks enables multi networking and creates relevat network objects on the cluster. | <pre>list(object({<br>    network            = string<br>    subnetwork         = string<br>    subnetwork_project = string<br>    network_ip         = string<br>    nic_type           = string<br>    stack_type         = string<br>    queue_count        = number<br>    access_config = list(object({<br>      nat_ip       = string<br>      network_tier = string<br>    }))<br>    ipv6_access_config = list(object({<br>      network_tier = string<br>    }))<br>    alias_ip_range = list(object({<br>      ip_cidr_range         = string<br>      subnetwork_range_name = string<br>    }))<br>  }))</pre> | `[]` | no |
| apply\_manifests | A list of manifests to apply to GKE cluster using kubectl. For more details see [kubectl module's inputs](kubectl/README.md). | <pre>list(object({<br>    content           = optional(string, null)<br>    source            = optional(string, null)<br>    template_vars     = optional(map(any), null)<br>    server_side_apply = optional(bool, false)<br>    wait_for_rollout  = optional(bool, true)<br>  }))</pre> | `[]` | no |
| cluster\_id | An identifier for the gke cluster resource with format projects/<project\_id>/locations/<region>/clusters/<name>. | `string` | n/a | yes |
| jobset | Install [Jobset](https://github.com/kubernetes-sigs/jobset) which manages a group of K8s [jobs](https://kubernetes.io/docs/concepts/workloads/controllers/job/) as a unit. | <pre>object({<br>    install = optional(bool, false)<br>    version = optional(string, "v0.5.2")<br>  })</pre> | `{}` | no |
| kueue | Install and configure [Kueue](https://kueue.sigs.k8s.io/docs/overview/) workload scheduler. A configuration yaml/template file can be provided with config\_path to be applied right after kueue installation. If a template file provided, its variables can be set to config\_template\_vars. | <pre>object({<br>    install              = optional(bool, false)<br>    version              = optional(string, "v0.8.1")<br>    config_path          = optional(string, null)<br>    config_template_vars = optional(map(any), null)<br>  })</pre> | `{}` | no |
| project\_id | The project ID that hosts the gke cluster. | `string` | n/a | yes |

## Outputs

No outputs.

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Requirements

These sections describe requirements for using this module.

### Software

The following dependencies must be available:

- [Terraform][terraform] v0.13
- [Terraform Provider for GCP][terraform-provider-gcp] plugin v3.0

### Service Account

A service account with the following roles must be used to provision
the resources of this module:

- Storage Admin: `roles/storage.admin`

The [Project Factory module][project-factory-module] and the
[IAM module][iam-module] may be used in combination to provision a
service account with the necessary roles applied.

### APIs

A project with the following APIs enabled must be used to host the
resources of this module:

- Google Cloud Storage JSON API: `storage-api.googleapis.com`

The [Project Factory module][project-factory-module] can be used to
provision a project with the necessary APIs enabled.

## Contributing

Refer to the [contribution guidelines](./CONTRIBUTING.md) for
information on contributing to this module.

[iam-module]: https://registry.terraform.io/modules/terraform-google-modules/iam/google
[project-factory-module]: https://registry.terraform.io/modules/terraform-google-modules/project-factory/google
[terraform-provider-gcp]: https://www.terraform.io/docs/providers/google/index.html
[terraform]: https://www.terraform.io/downloads.html

## Security Disclosures

Please see our [security disclosure process](./SECURITY.md).
