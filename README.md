# sig-atomic-buildscripts

This contains metadata and build scripts for the CentOS Atomic Host
Images.  For more information, see
http://wiki.centos.org/SpecialInterestGroup/Atomic

This branch contains a few scripts and metadata to get you started
building your own Atomic Host repo, and images.

### Doing a custom build

Clone this repo, checkout the 'custombuild' branch.
- edit the custom-atomic-host.json file to meet your requirements
- edit the atomic-7.1-cloud.ks to suite your requirements for a cloud
  image
- edit the atomic-7.1-vagrant.ks file to suite your vagrant box
  requirements

run the build_ostree-repo.sh script, eg: 
  bash build_ostree-repo.sh /srv

once done, in /srv/repo you should have the ostree repo. At this point
you can run the build_stage2.sh script to get the delivery media. By
detault this is setup to build cloud image, vagrant images and an 
installer iso file - most people will want to edit this script to only
produce the format they need. 

As a first effort, its recommended the entire set be produced and work
back from there. To run this script :
  bash build_stage2.sh /srv

This script uses libvirt and docker on the CentOS Linux 7 machine, so its
best run either on bare metal with virt capabilities, or in a VM with 
nested virt.

Typically, expect to consume about 2 to 3 GB of total data space, and
expect the process to run end to end in about 20 minutes.

### Contributing

Discuss on http://lists.centos.org/pipermail/centos-devel/

