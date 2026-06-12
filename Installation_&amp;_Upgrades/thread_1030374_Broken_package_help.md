---
title: "Broken package help?"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by batfink1 on 2009-01-04
i installed a video editing peice of software called kino and scince that i cannot open the add remove programs app, when i start i get the following error
> 
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

and im also unable to install the updates
when i try to i get the following error

> You have 1 broken package on your system!

Use the "Broken" filter to locate it.

then i click close and it trys to install it and then says...
> 
E: /var/cache/apt/archives/libmjpegtools0c2... subprocess dpkg-deb --fsys-tarfile returned error exit status 2

and also when i type "sudo apt-get install -f" i get this...

> elliot@laptop-blud:~$ sudo apt-get install -f
[sudo] password for elliot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  guile-1.8 linux-headers-2.6.27-7 guile-1.8-dev libgmp3-dev
  linux-headers-2.6.27-7-generic guile-cairo libtool libgmpxx4ldbl
  libreadline5-dev autotools-dev libltdl7-dev libncurses5-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmjpegtools0c2a
The following NEW packages will be installed
  libmjpegtools0c2a
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/219kB of archives.
After this operation, 557kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 137424 files and directories currently installed.)
Unpacking libmjpegtools0c2a (from .../libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu5_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu5_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

how can i fix this problem , im really stuck  :(:confused:

---

