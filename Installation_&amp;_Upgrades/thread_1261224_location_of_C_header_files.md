---
title: "location of C header files"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by brianmahler on 2009-09-08
I am in the process of installing VMware Server on Ubuntu 9.0.4 Server.  The installation script is complaining about the prebuilt vmmon modules for VMware Server are not suitable for my running kernal,   and do I want to try  to build the vmmon module for your system?  Yes I assume I do.

Then it has a problem with the following:

What is the location of the directory of C header files that match your running kernal ? [/usr/src/linux/include] is not existing directory.   

Does anybody know what I should put here?  Maybe I need to down load then but from where (URL)?

Thanks for your help as I earn my stripes with Linux.

Brian

---

### Post by niksonuk on 2009-09-16
I get this problem whenever the server runs an update???

To fix it try doing the following:

sudo apt-get install build-essential linux-headers-`uname -r`

run the install again this should fix it.

If you need good documentation for installing vmware go to:

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

