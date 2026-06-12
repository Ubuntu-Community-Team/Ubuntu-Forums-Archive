---
title: "Boot problems with amd64 recent kernels"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by lneves on 2009-09-09
Hi,
 
When I first tried to install ubuntu and kubuntu (and other variants of linux) in my Asus R1E laptop I found that I cannot "boot" recent versions of 64 bit kernels.
 
I was able to boot live ubuntu 8.10 32 bit kernel, but only 8.04 let me boot and then install the amd64 version, which I wanted to make use of 4Gb of RAM.
Then I tried to upgrade to 8.10 and then to 9.04 and I was successful, except for the kernel. I still can't "boot" the 2.6.28 kernels. Only the 2.6.24 from ubuntu 8.04.
 
Well, the 2.6.28 kernel boots, after a long long time, but the the X server fails to launch.
 
Does anyone has a clue on what to do?
 
Best regards,
 
Luís Neves

---

### Post by dstew on 2009-09-09
Probably some kernel module (driver) is not working well with your hardware. Boot in Recovery Mode and look for error messages, or after you boot, on a command line, use the the **dmesg** command to look at kernel messages. Maybe you can get a clue as to what the problem is.

---

