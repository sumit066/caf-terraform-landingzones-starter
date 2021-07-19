# Cloud Adoption Framework landing zones for Terraform - Starter template

## Generate the configuration files

```bash
cd /tf/caf/templates/platform

# Generate the contoso demo files (only this scenario is supported at the moment. More to come)
ansible-playbook e2e.yaml -e scenario=contoso -e model=demo

```

## Deploy the stack using symphony job

```bash

## Prerequisites

```bash
branch={{ config.eslz.private_lib[config.eslz.private_lib.version_to_deploy].caf_landingzone_branch }}
cd {{ config.destination_install_path }}
git clone --branch ${branch} https://github.com/Azure/caf-terraform-landingzones.git landingzones

# If you are planning to submit PR you can clone the a forked version instead
git clone --branch ${branch} git@github.com:Azure/caf-terraform-landingzones.git landingzones

# Or refresh an existing clone
cd {{ config.destination_install_path }}landingzones
git fetch origin
git checkout ${branch}
git status

cd {{ config.destination_install_path }}
git pull


```


# Only launchpad

 rover deploy \
  apply \
  -sc {{ config.destination_install_path }}{{ config.destination_relative_base_path }}/pipelines/symphony_e2e.yaml \
  -b /tf/caf/ \
  -env {{ config.launchpad.caf_environment }}

```

## Individual levels deployments

```bash

# Only launchpad

 rover deploy \
  plan \
  -sc /tf/caf/configuration/contoso/platform/demo/pipelines/symphony_e2e.yaml \
  -b /tf/caf \
  -env sandpit \
  -ct launchpad \
  -level level0

# Only launchpad

 rover deploy \
  plan \
  -sc /tf/caf/configuration/contoso/platform/demo/pipelines/symphony_e2e.yaml \
  -b /tf/caf \
  -env sandpit \
  -ct launchpad \
  -level level0

```