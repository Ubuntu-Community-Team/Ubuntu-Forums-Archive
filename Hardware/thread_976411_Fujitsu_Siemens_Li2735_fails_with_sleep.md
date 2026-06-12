---
title: "Fujitsu Siemens Li2735 fails with sleep"
date: 2008-11-09
forum: Hardware
---

### Post by Will_munns on 2008-11-09
Hi, brought this laptop after checking that the internals all had suitable drivers. Already had to open it up to fit a piece of tape to get the wireless working, but this problem is more annoying:

when entering sleep the laptop appears to do the right thing (right noises followed by orange status light, but does not awake upon opening the lid. pushing the power button shuts the power off rather than awaking the machine.

Also, hibernate takes a long time (it has 3Gb of ram, so no huge surprise), but when restarting prompts for PW, ideally I want no passwords in normal use so other can use the laptop, but I keep a good secure password for sudo.

The BIOS is Phoenix

Any ideas?

---

### Post by Will_munns on 2008-11-09
Additional info 

will@Fujitsu-Siemens:~$ cat /proc/acpi/wakeup 
Device	S-state	  Status   Sysfs node
LID0	  S3	*enabled   
SLPB	  S3	*enabled   
LANC	  S4	 disabled  
HDEF	  S4	 disabled  pci:0000:00:1b.0
PXSX	  S4	 disabled  pci:0000:02:00.0
PXSX	  S4	 disabled  
PXSX	  S4	 disabled  pci:0000:08:00.0
PXSX	  S4	 disabled  
PXSX	  S4	 disabled  
PXSX	  S4	 disabled  
USB1	  S3	 disabled  pci:0000:00:1d.0
USB2	  S3	 disabled  pci:0000:00:1d.1
USB3	  S3	 disabled  pci:0000:00:1d.2
USB4	  S3	 disabled  pci:0000:00:1a.0
USB5	  S3	 disabled  pci:0000:00:1a.1
EHC1	  S3	 disabled  pci:0000:00:1d.7
EHC2	  S3	 disabled  pci:0000:00:1a.7

will@Fujitsu-Siemens:~$ uname -a
Linux Fujitsu-Siemens 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

---

