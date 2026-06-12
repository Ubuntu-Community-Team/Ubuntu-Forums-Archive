---
title: "Problems compiling module with new Kernel from Kernel PPA"
date: 2010-06-13
forum: Hardware
---

### Post by lapalorky on 2010-06-13
I had trouble getting my Laptop to suspend with the current Kernel in Lucid (2.6.32-22-generic). So I installed a newer Kernel from PPA (2.6.34-5-generic) and suspend now works fine!

But now I can't get the module *acerhk* installed with the module-assistant. I have installed the Kernel headers and even the whole Source. The m-a prepare command tries to install the Kernel headers, but they are already installed.[INDENT]> 
**sudo m-a prepare**
Getting source for kernel version: 2.6.34-5-generic
apt-get install linux-headers-2.6.34-5-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.34-5-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

Done!
If I then try to build the module the following error comes up:

> Bad luck, the kernel headers for the target kernel version could not be found and you did not specify other valid kernel headers to use.I then specify the source directory with m-a:

> **sudo m-a -k /usr/src/linux-source-2.6.34**The Dialog gives me this warning:

> Warning /usr/src/linux-source-2.6.34 seems to contain unconfigured kernel source
And quits with this error:

> Bad kernel version specification at /usr/bin/m-a line 566.
[/INDENT]I have no trouble installing this module with the current Kernel in the Repository. Why is the module-assistant having problems with this newer Kernel?

I appreciate any ideas!

---

### Post by lapalorky on 2010-06-15
anyone?

---

