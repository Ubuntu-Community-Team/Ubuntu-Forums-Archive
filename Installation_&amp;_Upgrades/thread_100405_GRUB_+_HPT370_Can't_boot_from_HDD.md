---
title: "GRUB + HPT370: Can't boot from HDD"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by cwinata on 2005-12-07
Hi! I got stucked installing Ubuntu on my desktop. It is using HPT370 controller card and the 2 HDDs on it are not configured as RAID, but as stand alone HDD. Once I installed Ubuntu, it can't boot from the HDD. However, if I use GRUB floppy to boot and I can boot fine from it. After awhile, I got sick of typing the GRUB commands and I copied the menu.lst from the HDD to Floppy and the machine can boot perfectly from floppy. Once booted I've tried to install GRUB again, and it still won't boot from HDD, failing on Stage 2.

I figure the MBR is corrupted, so I boot a Win98 boot disc and did an 'fdisk /mbr'. Boot using GRUB Floppy and try to install GRUB on MBR again using "grub-install '(hd0)'", reboot and didn't work. Did a "grub-install /dev/hde", reboot and didn't work. Run GRUB on command line did a "setup (hd0)", reboot and it didn't work either. Except now after the "fdisk /mbr" it keeps on looking for CD-ROM to boot while the BIOS setting only specified to boot from HPT and Floppy.

current device.map is
hd0 /dev/hde
hd1 /dev/hdg

I have a DVD reader on /dev/hda and a DVD burner on /dev/hdc.

I even re-order the boot sequence in the BIOS in many combinations to see if it may work and it didn't.

I've read dozens of howtos on GRUB, FAQ, man grub, info grub, forums and none of them seems to give me anymore ideas of what I may need to try. If anyone can be kind enough to shed me some light, of what I may have messed up, please pleas do. Thank you.

Chuck

---

### Post by malentas on 2006-11-02
It's work: [http://lists.gnu.org/archive/html/bug-grub/2004-07/msg00113.html](http://lists.gnu.org/archive/html/bug-grub/2004-07/msg00113.html)

---

