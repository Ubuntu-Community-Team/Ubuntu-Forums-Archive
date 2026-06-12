---
title: "Packages won't upgrade"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by tokyo77 on 2008-12-28
Hi,
Whenever I try to upgrade my packages via Synaptic, I get the following error:

E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/openoffice.org-core/changelog.gz')
E: /var/cache/apt/archives/linux-headers-2.6.27-9-generic_2.6.27-9.19_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: corrupted filesystem tarfile - corrupted package archive

I tried running sudo apt-get install -f, but I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic localechooser-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-2.6.27-9-generic openoffice.org-core
The following NEW packages will be installed:
  linux-headers-2.6.27-9-generic
The following packages will be upgraded:
  openoffice.org-core
1 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
11 not fully installed or removed.
Need to get 0B/26.8MB of archives.
After this operation, 7610kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  openoffice.org-core linux-headers-2.6.27-9-generic
Authentication warning overridden.
(Reading database ... 103254 files and directories currently installed.)
Preparing to replace openoffice.org-core 1:2.4.1-11ubuntu2 (using .../openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-core ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/openoffice.org-core/changelog.gz')
Unpacking linux-headers-2.6.27-9-generic (from .../linux-headers-2.6.27-9-generic_2.6.27-9.19_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.27-9-generic_2.6.27-9.19_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb
 /var/cache/apt/archives/linux-headers-2.6.27-9-generic_2.6.27-9.19_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any suggestions? The main reason I want this to work is that I want language support, and whenever I open it, it says:

Software database is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Sorry if this post is a little lengthy. BTW, I have Linux Mint 6 (Felicia)

---

