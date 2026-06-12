---
title: "apt-get update error with non-native packages"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by plato4me on 2009-07-15
When I do an apt-get update, the following messages appear at the end of the output:
-------------------
Reading package lists... Done
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/archive.canonical.com_ubuntu_dists_jaunty_main_binary-i386_Packages: No such file
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/archive.canonical.com_ubuntu_dists_jaunty_main_binary-i386_Packages: No such file
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/packages.medibuntu.org_dists_jaunty_main_binary-i386_Packages: No such file
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/packages.medibuntu.org_dists_jaunty_main_binary-i386_Packages: No such file
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/planet76.com_repositories_._main_binary-i386_Packages: No such file
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/planet76.com_repositories_._main_binary-i386_Packages: No such file
Ignoring security.ubuntu.com_ubuntu_dists_jaunty-security_main_source_Sources
mangle: ia32-libs-tools/mangle.cc:402: void mangle(Archlist&, Renamelist&): Assertion `buf_used > 1' failed.
Aborted
-------------------------------

It appears that I can no longer update anything non-native.  I have absolutely no idea why.

I'm running a System76 Wild Dog.  It's intel 64-bit.

Can anybody help?

---

### Post by JMac82 on 2009-07-29
what solved it for me was going into synaptic and removing two packages:
ia32-libs-tools
ia32-apt-get

I also have 64-bit system, ubuntu jaunty though.

---

