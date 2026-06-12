---
title: "Does this output make sense for Ubuntu 8.04?"
date: 2008-10-04
forum: General Help
---

### Post by vinaykagarwal on 2008-10-04
Hello,

I have installed a pre-built Ubuntu 8.04 64 bit on my openvz vps. Do the following two outputs make sense?

root@server:~# cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

root@server:~# uname -a
Linux server.pico-car.com 2.6.18-53.1.19.el5.028stab053.14 #1 SMP Thu May 8 16:29:13 MSD 2008 x86_64 GNU/Linux

Specifically, should there be "el5" in the kernel version display? 

And aren't Ubuntu 64bit versions tagged with AMD64 even for Intel's processors?

Thanks in advance.
Vinay Agarwal

---

### Post by Sef on 2008-10-04
> Specifically, should there be "el5" in the kernel version display? 

And aren't Ubuntu 64bit versions tagged with AMD64 even for Intel's processors?

The el5 indicates it is a redhat kernel, so that's a openvz thing.  Nothing to worry about.

This is Ubuntu's uname -a:

> Linux sef-desktop 2.6.27-4-generic #1 SMP Wed Sep 24 01:29:06 UTC 2008 x86_64 GNU/Linux


---

