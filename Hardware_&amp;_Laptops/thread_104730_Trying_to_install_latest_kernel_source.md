---
title: "Trying to install latest kernel source"
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by coderasm on 2005-12-16
I have the 2.6.12-10-686 kernel.  And would like to download and install the kernel source, but when I issue the command I get this:

root@ubuntu:/usr/src# sudo apt-get install kernel-source
Reading package lists... Done
Building dependency tree... Done
Package kernel-source is a virtual package provided by:
  kernel-source-2.6.11 2.6.11-7
  kernel-source-2.6.10 2.6.10-6
  kernel-source-2.4.27 2.4.27-10
You should explicitly select one to install.

I know I need to specify which kernel version number, but mine is not listed.  Does anyone have another source in their source.lst to download my kernel version?
Thanks for any help.

---

### Post by ranf on 2005-12-17
Use `linux-source' not `kernel-source'.

---

