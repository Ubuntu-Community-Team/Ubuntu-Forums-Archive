---
title: "cannot mount/find USB HDD (Fat32)"
date: 2009-01-18
forum: Hardware
---

### Post by TheBronxisGrey on 2009-01-18
Hi,
I read every relevant thread I could find, but I think I need some 'custom' help. I am a recent convert and unfortunately HAVE to get this working if I want to stay with Ubuntu (and I do).

The Ubuntu is 8.10, gnome is the desktop.
The hdd in question is a 160gb ximeta netdisk. Please, I am not even attempting to do anything NDAS. I simply want to be able to plug the USB disk into my laptop (toshiba x205) or my wife's laptop.
Neither works!

The hdd is fine, and works wonderfully under win2003,winxp,OSX and Vista...
fstab simply does not show the drive when plugged in. It only displays:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f41dcdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       19458   154753024    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79f32b96

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6708    53881978+   5  Extended
/dev/sdb2            6709       19458   102400000    7  HPFS/NTFS
/dev/sdb5               1        6079    48829504+  83  Linux
/dev/sdb6            6080        6708     5052411   82  Linux swap / Solaris

These are the two 160gb internal drives of the laptop:(

ntfs3g is installed (not that it applies here)
I did try to disable USb 2.0 like this: sudo rmmod ehci_hcd
lsusb brings the following list:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 12c8:1f03  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

(The only plugged usb device was the hdd, which was turned on)

Being a bloody beginner I did try mounting it as "sdc" as I figured that would be next in line, but obviously that did not fly.
I am pretty desperate and would appreciate any help. I think I would be able to manually mount if the system recognized it was there!
Thank you in advance

PS: This is my first post and I am sure i butchered implementing the nice scroll windows for the output, if someone wants to tell me how that is done I would be happy to use it in the future.

---

### Post by s_carter2000 on 2009-01-22
Same issue ++ Here

Kubuntu Intrepid. Acer 5100. 

I love kubuntu and I think this drive worked well on hardy and earlier versions.

I have both Laptop and server installs so its unlikely a hardware issue
there were other solutions out there for oth the webam and drive BUT after trying those I have reinstalled from scratch +Firefox +

root@ACER5100:~# lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 12c8:1f03
Bus 001 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ACER5100:~#

dmesg output
multiple copies of the following

[33520.647837] sd 4:0:0:0: [sdb] Sense Key : No Sense [current]
[33520.647844] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[33520.650599] sd 4:0:0:0: [sdb] Sense Key : No Sense [current]
[33520.650608] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information

The USB Drive is freshly formatted so its no great loss other than I cant backup to it

Also as you can see I have an acer orbicam which also doesnt work Again tried a few things but that was also cleared out

Cheers
And thanks overall for a really good product.

SteveC

---

### Post by kevinbeard on 2009-05-13
I didn't think Ximeta devices could be used as an external USB?

I know my Rapsody N35 can't:

[http://www.divxtech.com/forum/index.php?method=showhtmllist&list=message&rollid=8,543&clearoff=1](http://www.divxtech.com/forum/index.php?method=showhtmllist&list=message&rollid=8,543&clearoff=1)

---

