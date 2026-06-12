---
title: "Ubuntu 14.04 External USB Hard Drive not recognized"
date: 2014-07-08
forum: Hardware
---

### Post by jay47 on 2014-07-08
Earlier today I was downloading a file with Vuze onto my external hard drive, and I don't know why but the system must have gotten overloaded and my computer froze. I waited a while, with no response, so I powered off the computer and turned it back on. When I tried to access my external, I couldn't find it anywhere. The drive is running... The light is on, and it is spinning. 

'lsusb':
```
Bus 001 Device 002: ID 8087:8000 Intel Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 1058:0810 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 007: ID 1532:0009 Razer USA, Ltd 
Bus 002 Device 005: ID 12d1:1570 Huawei Technologies Co., Ltd. 
Bus 002 Device 004: ID 0cf3:311e Atheros Communications, Inc. 
Bus 002 Device 003: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 04f2:0976 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The drive is listed there under bus 3, device 5.

'dmesg' turns out this at the end:
```
[ 2309.817562] usb 3-2: new SuperSpeed USB device number 5 using xhci_hcd[ 2309.833965] usb 3-2: New USB device found, idVendor=1058, idProduct=0810
[ 2309.833975] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2309.833980] usb 3-2: Product: My Passport 0810
[ 2309.833984] usb 3-2: Manufacturer: Western Digital
[ 2309.833988] usb 3-2: SerialNumber: 575841314138334E33323935
[ 2309.836418] usb-storage 3-2:1.0: USB Mass Storage device detected
[ 2309.836560] scsi5 : usb-storage 3-2:1.0
[ 2310.833889] scsi 5:0:0:0: Direct-Access     WD       My Passport 0810 1042 PQ: 0 ANSI: 6
[ 2310.834164] scsi 5:0:0:1: Enclosure         WD       SES Device       1042 PQ: 0 ANSI: 6
[ 2310.835736] sd 5:0:0:0: [sdb] Spinning up disk...
[ 2310.837578] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 2310.839376] ses 5:0:0:1: Attached Enclosure device
[ 2310.841053] ses 5:0:0:1: Attached scsi generic sg2 type 13
[ 2311.836989] .ready
[ 2313.961745] sd 5:0:0:0: [sdb] 976707584 512-byte logical blocks: (500 GB/465 GiB)
[ 2313.962220] sd 5:0:0:0: [sdb] Write Protect is off
[ 2313.962224] sd 5:0:0:0: [sdb] Mode Sense: 53 00 10 08
[ 2313.962581] sd 5:0:0:0: [sdb] No Caching mode page found
[ 2313.962584] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2313.965795] sd 5:0:0:0: [sdb] No Caching mode page found
[ 2313.965801] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2313.977046]  sdb: sdb1
[ 2313.978211] sd 5:0:0:0: [sdb] No Caching mode page found
[ 2313.978217] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 2313.978221] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 2353.610265] usb 3-2: reset SuperSpeed USB device number 5 using xhci_hcd
[ 2353.626520] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88006b519380
[ 2353.626526] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff88006b5193c0

```

'sudo fdisk -l'
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.



Disk /dev/sda: 16.0 GB, 16013942784 bytes
256 heads, 63 sectors/track, 1939 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1    31277231    15638615+  ee  GPT

```

Did the filesystem get corrupted because the disk was in the middle of writing? Is there any way to fix this?

---

### Post by yancek on 2014-07-08
> Did the filesystem get corrupted because the disk was in the middle of writing? Is there any way to fix this?         

It's certainly likely that there was corruption in a case like this.  You could run a filesystem check on the partition and you will have better luck finding out which partition it is using GParted as indicated in the fdisk output.  You have GPT partitioning and you need to use gparted to get drive/partition info as the message says, fdisk doesn't support GPT.  Just type:  sudo gparted in a terminal to open it.

It would probably be a good idea to use the installation disk/flash drive as gparted is on it.

---

### Post by jay47 on 2014-07-09
> **yancek said:**
> It's certainly likely that there was corruption in a case like this.  You could run a filesystem check on the partition and you will have better luck finding out which partition it is using GParted as indicated in the fdisk output.  You have GPT partitioning and you need to use gparted to get drive/partition info as the message says, fdisk doesn't support GPT.  Just type:  sudo gparted in a terminal to open it.

It would probably be a good idea to use the installation disk/flash drive as gparted is on it.
I got GPT up and running, but the drive isn't showing up. I've never used gparted before so maybe I'm just not seeing it, but is there a way to find it?

---

### Post by vanadium on 2014-07-09
The problem is only with the external USB harddrive? Likely, you have it formatted with the ntfs file system. When an ntfs file system is not properly closed, Ubuntu will not automatically mount it in order not to further damage the file system. Resolution: connect the USB drive to a Windows system and to a file system scan/repair using the Windows tools. Then properly disconnect the drive from the Windows system (using the eject icon). After that, it will automount in your Ubuntu system as before.

---

### Post by jay47 on 2014-07-09
> **vanadium said:**
> The problem is only with the external USB harddrive? Likely, you have it formatted with the ntfs file system. When an ntfs file system is not properly closed, Ubuntu will not automatically mount it in order not to further damage the file system. Resolution: connect the USB drive to a Windows system and to a file system scan/repair using the Windows tools. Then properly disconnect the drive from the Windows system (using the eject icon). After that, it will automount in your Ubuntu system as before.

Is there a way I can mount it and repair it in Ubuntu? I can get to a windows system, but there isn't one readily accessible to me. I would do a vm or something of the sort, but I'm running Ubuntu on my chromebook and space/processing power is very limited.

---

### Post by oldfred on 2014-07-09
If it is NTFS, you have to run chkdsk from Windows or a Windows repair CD or flash drive. Linux has a minimal check but all it really does is turn on the chkdsk flag so the next time Windows boots it, it runs chkdsk.

If using NTFS formatting you really should have a Windows repairCD or flash drive. And like Ubuntu run chkdsk periodically. Ubuntu runs fsck on / every 40 or 60 reboots.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Some third party Windows CDs include various repairs which may do chkdsk. Not sure if in free versions or you have to upgrade to paid version.

 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

---

