---
title: "Linux-kernel-headers"
date: 2005-12-17
forum: Installation &amp; Upgrades
---

### Post by coderasm on 2005-12-17
I cannot find the linux-kernel-headers-2.6.12.  All I can find is the 2.6.11.  I need the 2.6.12 headers to match my kernel to install the rt2570 drivers.  Anyone know where to find them.  They aren't in synaptic.  Thanks for any help.

---

### Post by kaamos on 2005-12-17
```
sudo apt-get install linux-headers-$(uname -r)
```
The package names don't currently match descriptions.. I think this is due to to the way apt chooses to upgrade packages
> 
~$ apt-cache search 2.6.12 | grep header
linux-headers-2.6.12-9 - Header files related to Linux kernel version 2.6.12
linux-headers-2.6.12-9-386 - Linux kernel headers 2.6.12 on 386
linux-headers-2.6.12-9-686 - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.12-9-686-smp - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.12-9-k7 - Linux kernel headers 2.6.12 on AMD K7
linux-headers-2.6.12-9-k7-smp - Linux kernel headers 2.6.12 on AMD K7 SMP
linux-headers-2.6.12-10 - Header files related to Linux kernel version 2.6.12
linux-headers-2.6.12-10-386 - Linux kernel headers 2.6.12 on 386
linux-headers-2.6.12-10-686 - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.12-10-686-smp - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.12-10-k7 - Linux kernel headers 2.6.12 on AMD K7
linux-headers-2.6.12-10-k7-smp - Linux kernel headers 2.6.12 on AMD K7 SMP


---

### Post by coderasm on 2005-12-17
Here's my output:

root@ubuntu:/usr/local# sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.12-10
The following NEW packages will be installed:
  linux-headers-2.6.12-10 linux-headers-2.6.12-10-686
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 6724kB of archives.
After unpacking 70.0MB of additional disk space will be used.
Do you want to continue [Y/n]?

Thanks for the help.  Where did you learn about the $(uname -r) at the end?
I've been reading around on the guides and didn't see anything about that.

---

### Post by kaamos on 2005-12-17
You can use $(command here) to use the output of other commands when using the terminal.

"uname -r" shows you your current kernel version. "uname -a" shows a this and other info as well. You can find out more my typing "man uname". The man command is often a very handy way to find out about some command if know just the name..

---

### Post by coderasm on 2005-12-17
Thankyou so very much, I was finally able to compile my driver for my usb wifi adapter.  I thought I was going nuts trying to find the correct source and kernel headers.

---

