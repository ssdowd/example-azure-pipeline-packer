# Packer Azure Example

This repo shows an example of using Packer to build a machine image for Azure.

The packer config starts from a base Ubuntu or RHEL image, applies all available updates and then installs ansible.

From there, packer copies the ansible files to the image and invokes ansible to run the playbook.  The playbook installs and starts nginx.  For RHEL, it opens port 80 in firewalld.

Packer then takes this and creates an image in Azure.  It is tagged and versioned.

The pipeline pulls secrets from the examplekeys vault in Azure to suply as variables to the packer config to allow it access to Azure.