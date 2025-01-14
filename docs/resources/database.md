---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "snowflake_database Resource - terraform-provider-snowflake"
subcategory: ""
description: |-
  
---

# snowflake_database (Resource)



## Example Usage

```terraform
resource "snowflake_database" "test" {
  name                        = "testing"
  comment                     = "test comment"
  data_retention_time_in_days = 3
}

resource "snowflake_database" "test2" {
  name    = "testing_2"
  comment = "test comment 2"
  replication_configuration {
    accounts             = [ "test_account1", "test_account_2"]
    ignore_edition_check = true
  }
}

resource "snowflake_database" "test3" {
  name                        = "testing_3"
  comment                     = "test comment"
  data_retention_time_in_days = 3
  from_replica = "org1\".\"account1\".\"primary_db_name"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String)

### Optional

- `comment` (String)
- `data_retention_time_in_days` (Number)
- `from_database` (String) Specify a database to create a clone from.
- `from_replica` (String) Specify a fully-qualified path to a database to create a replica from. A fully qualified path follows the format of "<organization_name>"."<account_name>"."<db_name>". An example would be: "myorg1"."account1"."db1"
- `from_share` (Map of String) Specify a provider and a share in this map to create a database from a share.
- `replication_configuration` (Block List, Max: 1) When set, specifies the configurations for database replication. (see [below for nested schema](#nestedblock--replication_configuration))
- `tag` (Block List) Definitions of a tag to associate with the resource. (see [below for nested schema](#nestedblock--tag))

### Read-Only

- `id` (String) The ID of this resource.

<a id="nestedblock--replication_configuration"></a>
### Nested Schema for `replication_configuration`

Required:

- `accounts` (List of String)

Optional:

- `ignore_edition_check` (Boolean)


<a id="nestedblock--tag"></a>
### Nested Schema for `tag`

Required:

- `name` (String) Tag name, e.g. department.
- `value` (String) Tag value, e.g. marketing_info.

Optional:

- `database` (String) Name of the database that the tag was created in.
- `schema` (String) Name of the schema that the tag was created in.

## Import

Import is supported using the following syntax:

```shell
terraform import snowflake_database.example name
```
