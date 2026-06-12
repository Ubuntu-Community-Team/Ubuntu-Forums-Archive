---
title: "Wake up on USB problem - new install"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by raincity on 2007-08-13
Hi,

I'm attempting to switch to ubuntu from Windows and have been unable to get the machine to wake from S3 by any method other than hitting the power button.  I'm trying to get it to wake on USB USB keyboard or mouse.  I've spent about 4 hours going through various posts I've found online regarding acpi issues, but had no luck addressing the problem.  I know the hardware is capable of this because it works just fine with Windows XP.

Some things I've checked:

USB ports do retain power when in S3.

Bios settings - wake on USB and wake on LAN are enabled.

acpi settings - I've enabled wakeup as follows:

Device      Sleep state          Status
PCI0              5                    disabled
USB0             3                     enabled 
USB1             3                     enabled 
USB2             3                     enabled 
USB3             3                     enabled 
USB4             3                     enabled 
USB5             3                     enabled 
USB6             3                     enabled 
USB7             3                     enabled 
LAN0             5                     disabled 

I've used Windows for many years and am new to Linux but I'd really like to resolve this issue because I'd like to move away from Microsoft products.  Their "Genuine Advantage Validation" program has been the last straw.  

Any help would be appreciated.

---

### Post by arturj on 2007-09-16
Same problem for me:

before I used a MSI Mainboard for Athlon XP CPUs and wake-on-keyboard just worked for me fine. After migrating to an ASUS AMDx2 Mainboard it stopped working in the following manner:
Windows still works for all modes (poweroff, hibernate, suspend) but Ubuntu only wake ups by key press when powered off. All suspend modes do not longer wake on keyboard press....

Any suggestions? Which package is responsible (for further investigation or bug-reports)?

---

