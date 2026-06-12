---
title: "Pre fresh Ubuntu install hardware concerns."
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by DarkSideofOZ on 2009-07-01
I tried ubuntu about 2 years ago, but I wasn't quite ready to take the plunge because of driver issues (nvidia). 

I am being forced to go from XP to Vista because I just ordered components for an upgrade, and those parts included 6GB of ram, which xp won't support.  I've always hated Vista so I've decided to give Ubuntu another shot. Now, I'm ready to try this again, though I can't seem to find a hardware support list. So I figured I'd give it a try here. 

**Processor: **Core i7 920
**Mobo: **[Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813188046")[SIZE=1]  EVGA E758-TR 3-Way SLI (x16/x16/x8) LGA 1366 Intel X58 ATX Intel Motherboard[/SIZE]
 This is what I need help with. 
**Vid Card: **[Link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130398") [SIZE=1]EVGA 896-P3-1265-AR GeForce GTX 260  Core 216 896MB 448-bit GDDR3 PCI Express 2.0 x16
**RAID card:** [Link]("http://www.adaptec.com/en-US/support/sata/sataii/AAR-1430SA/")[/SIZE]  Adaptec SATA II RAID 1430SA  
[SIZE=1]



I need to know if all the onboard stuff on my mobo is supported as well as the vid card and SATA controller card. I have 9 hard drives and plan on expanding further which is why I need the card working.

Any insight would be greatly appreciated.

Also, should I install vista THEN ubuntu or vice versa?

[/SIZE]

---

### Post by hansdown on 2009-07-01
Hi DarkSideofOZ.

I'm not sure of the hardware, but here's a guide to dual booting
if you decide to do so.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by mikewhatever on 2009-07-01
GeForce GTX 260 is on the list of supported cards for the newer nvidia driver for Jaunty. See for yourself [http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180).

---

### Post by DarkSideofOZ on 2009-07-01
Thanks, both of you, now if only I could find out if the mobo components will work  

North Bridge      Intel X58
South Bridge     Intel ICH10R

Integrated sound (Intel)

---

### Post by mikewhatever on 2009-07-01
You should probably try running Ubuntu from the cd. It runs entirely in RAM so that no changes are made to the HDD. Given the fact you have 6 GB, I'd suggest trying a 64 bit version.

PS: You may be interested in this review. [http://www.phoronix.com/scan.php?page=article&item=intel_core_i7&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_core_i7&num=1)

---

