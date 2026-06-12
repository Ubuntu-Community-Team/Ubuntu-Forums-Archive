---
title: "Please help with Grub Error 17 and Sata disk"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by Mariachi on 2007-09-04
I think I'm having a newbie problem :lolflag:   

The Master HD has XP, I installed a second one and installed Ubuntu.  However, I have a third Sata disk where I store all my music, pics, etc and I realize that because of this disk I was getting the "Grub Error 17".

When I boot from Live Cd, it recognizes all three disks, I can even navigate through them.  The thing is that when I boot normally it gives me "Grub Error 17".  If I unplug the Sata disk it won't give me any errors, it displays the options to boot either from my first HD (WinXP) or my second HD (Ubuntu) but the Sata disk has to be unplugged in order for the Grub to boot correctly, and obviously the disk won't be available on any of the OS.

How can I make the Grub recognize my Sata disk and boot normally, or at least to give me the option to use it in WinXP.


Thanks for all your help!!

---

### Post by agemon on 2007-09-05
hello, seem to me like a lot of people has got 'error 17: can not mount selected parition', you can try googleing the problem, or, post the contents of /boot/grub/menu.lst (without commented lines) and /boot/grub/device.map.
Also, post info about your hdd and partitions, to do that, enter ubuntu from the live cd (with your third hdd installed) and from the console type `sudo parted /dev/sda`, then, from the parted console type 'print' and copy the info it gives you here, then 'quit'. Do the same for the other hdd (`sudo parted /dev/sdb` and `sudo parted /dev/sdc`).

PS: there is something i don't understand: you had 3 sata disks, one with windows, one empty and one with muzic and pics, then you installed ubuntu on your second drive, right? During the instalation a message was probably shown asking you if you wanted to install grub on you MBR, what did you answer?

---

### Post by Mariachi on 2007-09-05
Here's some more info, this was done by using Live Cd

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4862 39053983+ 7 HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 2327 18691596 83 Linux
/dev/sdb2 2328 2434 859477+ 5 Extended
/dev/sdb5 2328 2434 859446 82 Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdc1 1 19457 156288321 7 HPFS/NTFS



Here you go "sudo lspci" still with live cd:
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
01:01.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
__________________

---

### Post by agemon on 2007-09-06
error 17 appears when grub tries to mount a partition but it does not recognize the file system. My guess is that a 'kernel' entry in your /boot/grub/menu.lst is pointing to either your swap partition or some ntfs one, or maybe devices.map is wrong...
oh by the way, fdisk says that sda and sdb are bootable, to witch one are you booting?

---

### Post by Mariachi on 2007-09-14
I'm booting with hda which has windows on ...

---

