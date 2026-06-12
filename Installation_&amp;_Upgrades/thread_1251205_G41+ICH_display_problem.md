---
title: "G41+ICH/ display problem"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by alenis on 2009-08-27
I installed Jaunty on a computer with an ASRock G41m-LE motherboard, based on Intel G41+ICH7 chipsets and everything seemed to work fine, although I couldn't activate desktop effects. After the massive post-installation upgrade, however, after restarting the system, a box in the center of the screen appeared saying "Ubuntu is running in low graphics mode. The following error was encountered. You may need to update your configuration to solve this. (EE) intel(0): failed to initialize kernel memory manager"

I installed the system again and, just to check which package was to blame, I upgraded only the xserver-xorg-video-intel package. Everything worked fine after this upgrade. Then I upgraded all the others package with the exclusion of linux-generic (which I thought was the only other candidate culprit) but the low-graphics mode problem described above appeared again. 

Searching the net I read that the G41 chipset is still not fully supported by the Linux kernel, so we can't get optimum performances, but in my case it just doesn't work. I don't care very much about desktop effects.  I would be happy with a full resolution screen. I guess I should not upgrade some packages, but my problem is: which packages should I   not upgrade to keep the system running at full resolution?

---

### Post by gaspros on 2010-03-22
I have just installed a newly burnt version of 9.04 which worked, I performed a full upgrade to 9.10 and now I have the same issue. Did anybody sort out a solution for this. I have spent hours searching the forums and trying various things. About to give up and reinstall 9.04 as I dont know how to rollback the upgrade.

---

### Post by gaspros on 2010-03-24
By the way, I re-installed 9.04 then went to upgrade only security upgrade and options and not selecting 9.10 upgrade and it now has an error on reboot saying
Ubuntu is running in low graphics mode: 
(EE) intel(0): Failed to initialize kernal memory manager

Any suggestions on this?

My specs are as follows:
Intel  Pentium Dual Core E6500 CPU, 2.93 GHz, FSB 1066MHz, Socket    LGA775
ASRock  G41C-VS M/board - Intel G41+ICH7, COMBO DDR2+DDR3, 1333 MHz FSB,   PCIE,  int VGA, SATAII, 5.1Ch
2GB  DDR3 PC-10600 (1333MHz)
500GB Hitachi 7200rpm PATA HD

I have loaded 9.04 Jaunty linux kernal 2.6.28-11 generic Gnome 2.26.1

Then I alled updates.

---

### Post by gaspros on 2010-03-28
I changed some settings in the BIOS and then clean installed 9.10 Karmic then performed updates from there and the problem went away.

---

