---
title: "How to set up a triple boot on 2 hard disks?!"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by Draconist on 2005-12-11
So, something like this..
on first IDE hard disk (primary master - hda) should go Window$, and on second IDE hard disk (primary slave - hdb) set up Ubuntu Breezy ofcourse.. :)  and SUSE 10 just for testing...

Question:
first install Win, then Ubuntu on second HD.. and then what to do, where to place Ubuntu's GRUB.. to /root partition on second HD, or to MBR on first HD with Win?
...after that (if all goes well) SUSE's bootloader should go also on SUSE /root partition (so that nothing is changed) and ofcourse that I can configure everything with my Ubuntu bootloader? :???: 

Thx everybody! :)

---

### Post by matthewv on 2005-12-11
I know one install of ubuntu will pick up another, but I'm not too sure whether it will pick up suse. I think that what u've described should work. I'm quad booting myself: WinXP, Ubuntu 5.10, ubuntu 6.04, and pc-bsd 0.8.2. I have grub on a floppy... so i remove the floppy to boot windows.. my install of 5.10 picked up the 6.04, and i edited the grub menu.lst to boot pc-bsd :D

---

### Post by metoo on 2005-12-12
Have a similar setting.
grub goes into mbr of hda (if your BIOS boot order is hd0 first).
On the 2nd drive (for you, its all on the 1st for me) I have a special /boot partition. 64MB, to hold several kernel (upgrade...) versions for both linux installs. 1 about 8MB each.
Install Win, ubuntu and suse10. On one machine I have now the suse grub bootloader installed. If I remember correctly, I had to add ubuntu manually after suse. For sure, I had to delete the entry "savedefault" in /boot/grub/menu.lst for the ubuntu entries with the suse grub loader (where there from the ubuntu grub. So small changes to the ubuntu grub loader in suse).
Better copy (or print) the /boot/grub/menu.lst after installing ubuntu. May be it is better at all to just have a /boot directory in each of the linux / partitions? Anyhow, the shared /boot partition is working here.

So on the 2nd hd you need at least 2 root partitions and one swap (can be shared). If wanted a /boot partition. And while you are at it, why not a 3rd spare / (root) partition, to play later with either suse 11 or ubuntu 6.04? The rest data or whatever.

---

### Post by hoodwink on 2005-12-12
[QUOTE=Draconist]So, something like this..
on first IDE hard disk (primary master - hda) should go Window$, and on second IDE hard disk (primary slave - hdb) set up Ubuntu Breezy ofcourse.. :)  and SUSE 10 just for testing...

Question:
first install Win, then Ubuntu on second HD.. and then what to do, where to place Ubuntu's GRUB.. to /root partition on second HD, or to MBR on first HD with Win?
...after that (if all goes well) SUSE's bootloader should go also on SUSE /root partition (so that nothing is changed) and ofcourse that I can configure everything with my Ubuntu bootloader? :???: 

Thx everybody! :)[/QUOTE]

Just my $.02.

I've run 3X+ boot systems for years, and the best approach is a combination of automatic and manual.

1. There really is no such thing as a Ubuntu or SUSE boot loader; it's just plain ole grub. Whichever grub installed itself to the MBR is the one in control.

2. Your setup of Windows on one hard drive, and the others on a second hard drive is just fine.

3. Presuming that you prefer Ubuntu as your primary Linux system, I would install the systems in this order:

(1). Windows (Windows always overwrites the MBR, and you would temporarily lose the ability to boot either linux if you do the windows install later.)

(2). SUSE (or other experimental system). You can let SUSE overwrite the MBR, too.

(3) Ubuntu. The Ubuntu/Debian installer does a fine job of making other Windows and Linux systems bootable thrugh its grub menu. I have an existing CentOS system that Ubuntu detected and made bootable with no problems.

4. Once you have everything in place, the /boot/grub/menu.lst (most other distros now use ...grub.conf) will be what's pointed to by the MBR and will control what systems you can boot. The Ubuntu system will be the default.

5. If you upgrade to a new kernel on Ubuntu, the menu.list will be udated automatically.

6. If you upgrade your SUSE kernel, you need to manually copy the changed lines from the /boot/grub/menu.lst or grub.conf on the SUSE system to the active /boot/grub/menu.lst on Ubuntu.

7. It's always a good idea to keep a Knoppix (or other rescue system) cdrom hand in case any changes you make overwrite the MBR. You can boot from cdrom, mount your Ubuntu system, and chroot to the mountpoint, then use grub to repair the mbr.

HTH,

---

### Post by Draconist on 2005-12-13
Ok guys, thank you all for answers! ;)

Everything is working great :) and I did the following in this order:

1. Installed Window$ (grrr..) on 1st HD
2. Installed my Ubuntu Breezy :) on 2nd HD
3. Installed SuSE 10 on 2nd partition at 2nd HD

After Ubuntu install was finished the GRUB was placed at MBR of 1st HD, Window$ was there as boot option, and after SuSE installation I just chose NOT! to install SuSE's GRUB at all, but instead configure my Ubuntu /boot/grub/menu.lst meaning add the SuSE's (hd1,1) parameters for boot up!

Thaz it, once again thx to ya all and..

Cheers! :D

---

