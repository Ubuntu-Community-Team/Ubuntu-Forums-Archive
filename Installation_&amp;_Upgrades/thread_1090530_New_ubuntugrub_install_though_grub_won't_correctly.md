---
title: "New ubuntu/grub install though grub won't correctly boot windows."
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by Morphus on 2009-03-08
[SOLVED]This issue has been resolved.
The problem was despite device.map showing the devices were mapped to (hd0), (hd1) and (hd2) they were infact mapped to (hd0), (hd2) and (hd3) which became apparent when running the geometry command at the grub CLI. This explains the unable to read disk error as there was no disk mapped to (hd1) though i still have no idea why the device.map and actual mappings were inconsistent.


Hi,

I am having difficulty configuring windows to work correctly with grub and am currently getting Error 25: Disk Read error.
I have 3 HDD's all with NTFS partitions on them, one is bootable with XP on it and another has at the start also has ubuntu and swap partitions on it.

I have only today installed ubuntu and with it grub, and as a result placed the ubuntu drive into the first sata port, with xp in the second port and the 3rd disk in the 3rd port. I deliberately set it up like this as I did not want place grub near the XP disk, for risk of it causing problems when i later install vista.

My problem is that while ubuntu boots nicely, XP will not boot at all, citing Error 25: Disk Read error. At this point it halts, and pressing any key takes me back to grub. I know however there is nothing wrong with the XP disk, as when I remove sata0, XP (sata1) boots fine.

My configuration is as follows:

Ubuntu 8.10

menu.lst:

```
## ## End Default Options ##

# This entry automatically added by the Debian installer for Windows XP on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		30816baf-83e1-4420-be07-aecb80b6d309
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=30816baf-83e1-4420-be07-aecb80b6d309 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		30816baf-83e1-4420-be07-aecb80b6d309
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=30816baf-83e1-4420-be07-aecb80b6d309 ro  single
```

(continues with other linux versions)

/sbin/fdisk -l :

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd231b932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2112    16964608+  83  Linux
/dev/sda2            2113       30400   227223360    f  W95 Ext'd (LBA)
/dev/sda5            2612       30400   223215111    6  FAT16
/dev/sda6            2114        2611     4000153+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30393   244131741    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf088f46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2612       91201   711599175    f  W95 Ext'd (LBA)
/dev/sdc5            2612       91201   711599143+   7  HPFS/NTFS
```

device.map:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

Edit:

boot.ini:

```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

If anyone knows what I need to do to fix the bootloader that would be great, its not mission critical as I can boot windows w/o the linux drive then hotplug it to get it in windows, though it would be really nice to get it working properly.

I have since tried manually editing the menu.lst to other values of drives, partitions. Combinations tried are (hd1,1) (hd1,10) which are both partitions which don't exist. I also tried (hd3,0) which is a SATA port which exists though is disbled with no connected device, this also gave the same error. I tried hd(4,0) which would be a 5th SATA port, which my machine does not have, this gave a different error.

It would seem that I am getting the same error as you would get if you specified a hdd or partition which does not exist, or does not have a boot sector. Hopefully this might help people in locating the problem I'm facing.

---

### Post by Morphus on 2009-03-08
I have just found this a link which mentions the problem, so so far as I can see since I am running SATA disks in AHCI mode, only suggests you check the cables are plugged in correctly, which if they were not they would not run in ubuntu/windows anyhow.
[http://users.bigpond.net.au/hermanzone/p15.htm#25](http://users.bigpond.net.au/hermanzone/p15.htm#25)


Quoted from the GNU/GRUB manual

    25 : Disk read error
        This error is returned if there is a disk read error when trying to probe or read data from a particular disk.

GRUB Error 25 is most likely to happen right after someone has added a new drive of some kind to their computer.  This error message usually indicates some kind of BIOS or hardware problem.
Normally this error has something to do with the way the hard drives and CD/DVD drives are plugged in.
Most often the IDE jumper settings will be found to be incorrect.

It might be necessary to open your computer case and maybe shine a light in there to take a look around.

There are two kinds of hard disk drives,

    * IDE hard drives, (also called 'PATA')
    * SATA hard drives, (classed as SCSI drives)

IDE drives have very wide ribbon cable, usually about 50mm wide.
An IDE ribbon cable normally has three plugs on it, one plug for plugging into the motherboard port and two other plugs. The other two plugs are for hard disc drives, or a hard drive and a CD/DVD drive.
Most motherboards have two IDE ports, one called 'primary', and another called 'secondary'.
Two IDE ports, each with a cable for two drives means you can normally have up to four IDE drives.

There are two kinds of IDE ribbon cable, the older, 40 conductor cable, and the newer, finer 80 conductor ribbon cable.

    * Normally, the older kind of ribbon cable is grey, with a red stripe in one edge, and had three black plugs. With the older type of ribbon cable, the way to tell the computer which should be the first and which should be the second hard drive was to use jumper settings to set one hard drive as 'master', and the other as 'slave' on the primary ribbon cable, and one hard drive as 'master', and the other as 'slave' on the secondary ribbon cable.
    * With the newer, finer 80 conductor ribbon cable, normally there's a blue plug for the motherboard socket, and a grey plug halfway for the slave drive, and a black plug at the end for the master hard drive. This type of IDE ribbon cable is the 'cable select' type of IDE ribbon cable. The jumper settings for this type of cable should be set on 'cable select'. Look for a sticker on top of the hard drive, (if you can see it), which will tell you how to set the hard dirve jumpers. Most of the time you need to physically remove one or more hard drives to see the stickers.

Sata hard drives are the newer kind and those are connected to the motherboard by a narrow ribbon cable which is about 8mm wide and 2mm thick, normally red in color. There is one port on the motherboard for each SATA cable, so SATA drives don't need jumper settings. Normally, the SATA drive that's plugged into the number 1 port will be number 1, and number 2 SATA drive is plugged into the number 2 SATA port on the motherboard, and so on. 

Check to make sure your hard drive cables are plugged into the right ports
If you have IDE drives, make sure the jumper settings are correct, even for the optical drive (CD/DVD drive).
Also, don't forget to check that the power cable from the power supply is connected. (It seems obvious).

Also, check your BIOS settings and make sure all your hard drives are set to 'auto', and to 'LBA' mode, and are detected and set up correctly by the BIOS.

Guide to Installing IDE/ATA devices - Free PC Tech

Hard Drive Installation Guide -PC Stats

Pin Assignments for the 40-pin IDE standard - [www.ele.uri.edu](www.ele.uri.edu)

---

### Post by Morphus on 2009-03-08
[SOLVED]This issue has been resolved.
The problem was despite device.map showing the devices were mapped to (hd0), (hd1) and (hd2) they were infact mapped to (hd0), (hd2) and (hd3) which became apparent when running the geometry command at the grub CLI. This explains the unable to read disk error as there was no disk mapped to (hd1) though i still have no idea why the device.map and actual mappings were inconsistent.

---

