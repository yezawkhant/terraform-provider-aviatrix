---
subcategory: "Useful Tools"
layout: "aviatrix"
page_title: "Aviatrix: aviatrix_vpc"
description: |-
  Gets an Aviatrix VPC's details.
---

# aviatrix_vpc

The **aviatrix_vpc** data source provides details about a specific VPC created by the Aviatrix Controller.

This data source can prove useful when a module accepts any form of VPC detail as an input variable. For example, requiring a subnet CIDR specification when creating a gateway.

## Example Usage

```hcl
# Aviatrix VPC Data Source
data "aviatrix_vpc" "test" {
  name = "vpc-test"
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) Name of the Aviatrix VPC.
* `route_tables_filter` - (Optional) Filters the `route_tables` list to contain only public or private route tables. Valid values are 'private' or 'public'. If not set `route_tables` is not filtered.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `cloud_type` - Type of cloud service provider.
* `account_name` - Account name of the VPC created.
* `region` - Region of the VPC created.
* `cidr` - Subnet of the VPC created.
* `region` - Region of the VPC created.
* `aviatrix_transit_vpc` - Switch if the VPC created is an Aviatrix Transit VPC or not.
* `aviatrix_firenet_vpc` - Switch if the VPC created is an Aviatrix FireNet VPC or not.
* `vpc_id` - ID of the VPC created.
* `route_tables` - List of AWS route table ids associated with this VPC. Only populated for AWS vpc.
* `subnets` - List of subnet of the VPC created.
  * `cidr` - Subnet CIDR.
  * `name` - Subnet name.
  * `subnet_id` - Subnet ID.
* `public_subnets` - List of public subnet of the VPC created.
  * `cidr` - Public subnet CIDR.
  * `name` - Public subnet name.
  * `subnet_id` - Public subnet ID.
* `private_subnets` - List of private subnet of the VPC created.
  * `cidr` - Private subnet CIDR.
  * `name` - Private subnet name.
  * `subnet_id` - Private subnet ID.
