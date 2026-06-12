---
title: "SATA Via VT8237 Boot problems"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by richjoyce on 2007-04-20
Hi everyone,

I recently updated my pundit p2-ae2 (running as a server) from a 250GB IDE drive to a 500GB SATA drive.  I originally couldn't install 6.06 server since it didn't recognize the drive, and after some research found out that my VT8237 southbridge was not supported by kernels before 2.6.19 (or 20, I can't remember).  Either way, I had to use feisty server to get it to see my hard drive.  So after installing feisty, I have no problems once the machine is booted.  The problem is getting it to boot.

There are three scenarios that happen when I try to boot the machine:
1) It boots fine.
2) Grub goes through fine, and it shows the line "Starting Up..." and then shows a kernel message to the likes of "sata_via master/slave not supported [0xa2]"  This problem seems to be a problem with loading the sata_via module or something?
3) Grub loads fine, and it shows the line "Starting Up..." and it hangs.  I believe that this is a problem with grub, and it has not correctly handed off the boot to the kernel for some reason.

There seems to be no pattern around the problems I get.  Sometimes I get it to boot up quickly with only one or two attempts, sometimes it will take me a half hour of turning on and off before I can get it to boot.

Luckily this is a server, so it should have long uptimes and I don't need to reboot that often, but I will need to move it a few times a year at the least, and I need to be able to rely on it to boot up headless, so these problems are going to be annoying.

Any help on how to work on these problems would be appreciated.
Thanks

---

