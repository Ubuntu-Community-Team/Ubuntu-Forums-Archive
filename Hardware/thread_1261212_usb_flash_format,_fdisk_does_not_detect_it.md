---
title: "usb flash format, fdisk does not detect it"
date: 2009-09-08
forum: Hardware
---

### Post by etlpkby on 2009-09-08
Hi All,

Today I stupidly aborted a 'gparted' task on my USB FLASH (Maxell) whilst installing Puppy Linux.It's completely hosed and I would like to re-format the whole thing. I'm not bothered about data on it at all. Inserting the drive and looking at 'dmesg' it detects the drive:-


```
Sep  8 18:22:24 patb-desktop kernel: [375255.500549] usb 1-9: new high speed USB device using ehci_hcd and address 32
Sep  8 18:22:24 patb-desktop kernel: [375255.634019] usb 1-9: configuration #1 chosen from 1 choice
Sep  8 18:22:24 patb-desktop kernel: [375255.634704] scsi24 : SCSI emulation for USB Mass Storage devices
Sep  8 18:22:29 patb-desktop kernel: [375260.633066] scsi 24:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2
Sep  8 18:22:29 patb-desktop kernel: [375260.636265] sd 24:0:0:0: [sdd] Attached SCSI removable disk
Sep  8 18:22:29 patb-desktop kernel: [375260.636395] sd 24:0:0:0: Attached scsi generic sg5 type 0

```

I'm running Ubuntu 9.04 (x64_86), BTW...However, "sdd" which the kernel *appears* to assign the device, is not available:

```
root@patb-desktop:~# fdisk /dev/sdd

Unable to open /dev/sdd
```

Nor is it seen with "fdisk -l". It is seen with "lsusb" 

```
oot@patb-desktop:~# lsusb
**Bus 001 Device 032: ID 1307:0163 Transcend Information, Inc. 512MB USB Flash Drive**
Bus 001 Device 004: ID 059f:0527 LaCie, Ltd 
Bus 001 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04b8:0110 Seiko Epson Corp. Perfection 1650
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

...but it is NOT Transcend Manuf. It is a 16Gb MAXELL stick (!)

Is there any way, (I thought of 'dd' but I need a /dev/something at least, right?) to re-format this usb stick? BTW: If I try to plug it into windoze, it give me a drive allocation ("E:" etc) but a list of hex numbers when I try to access it with explorer.

Anyone got any idea's or have I hosed it beyond recovery :(

Patrick.

---

### Post by cak3 on 2009-09-08
So, is it assigned to /dev/sdd, just not accessible (and no partitions accessible/detected)? If that's the case, you might be able to write a new partition table with gparted (though I think that probably uses fdisk, it might be able to do some magic).

What is the (relevant) output of fdisk -l?

---

### Post by etlpkby on 2009-09-08
> **cak3 said:**
> So, is it assigned to /dev/sdd, just not accessible (and no partitions accessible/detected)? If that's the case, you might be able to write a new partition table with gparted (though I think that probably uses fdisk, it might be able to do some magic).

What is the (relevant) output of fdisk -l?

Yeah. "gparted" just lists sda, sdb and sdc partitions and does not detect sdd. This is also what 'fdisk -l' is telling me:-

```
root@patb-desktop# fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d87f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2189    17583111   83  Linux
/dev/sda3            2295        2555     2096482+  82  Linux swap / Solaris
/dev/sda4            2556       14946    99530707+   5  Extended
/dev/sda5            2556       10204    61440561   83  Linux
/dev/sda6           10205       11479    10241406   83  Linux
/dev/sda7           11480       12754    10241406   83  Linux
/dev/sda8           12755       14946    17607208+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 500.1 GB, 500118700032 bytes
255 heads, 63 sectors/track, 60802 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x454c3352

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488392033+  83  Linux

```

Basically, sda is my SATA HDD (bootable) - sdb and sdc are my USB Hard Disk drives.

I'm googling around to see if there's anything that I can do - I can see the (usb flash) device in "dmesg" but because the actual filesystem is corrupted on it, it will not be mounted. **So why can't I "fdisk /dev/sdd"?**

I just want to re-format the damn thing! ](*,)

---

### Post by etlpkby on 2009-09-08
Postscript...

If I remove the usb flash, it is also detected - thus...

```
Sep  8 23:01:32 patb-desktop kernel: [392004.479288] usb 1-10: USB disconnect, address 37
```

..and the /dev/sdd entry is also removed...

```
root@patb-desktop:~# ls -l /dev/sdd
ls: cannot access /dev/sdd: No such file or directory
```

Re-attached the usb flash...messages are again seen...

```
Sep  8 23:04:14 patb-desktop kernel: [392166.368037] usb 1-10: new high speed USB device using ehci_hcd and address 38
Sep  8 23:04:15 patb-desktop kernel: [392166.500976] usb 1-10: configuration #1 chosen from 1 choice
Sep  8 23:04:15 patb-desktop kernel: [392166.503534] scsi30 : SCSI emulation for USB Mass Storage devices
Sep  8 23:04:20 patb-desktop kernel: [392171.500798] scsi 30:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2
Sep  8 23:04:20 patb-desktop kernel: [392171.503081] sd 30:0:0:0: [sdd] Attached SCSI removable disk
Sep  8 23:04:20 patb-desktop kernel: [392171.503207] sd 30:0:0:0: Attached scsi generic sg5 type 0

```
...and the /dev/sdd entry is created...

```
root@patb-desktop:~# ls -l /dev/sdd
brw-rw---- 1 root disk 8, 48 2009-09-08 23:04 /dev/sdd
root@patb-desktop:~# 
```

But fdisk still won't allow me to open the device...

```
root@patb-desktop:~# fdisk /dev/sdd

Unable to open /dev/sdd
```


:confused:
Will have to sleep on this one....
Patrick/

---

### Post by etlpkby on 2009-09-13
Update: Still not working ](*,)

I did a "strace fdisk /dev/sdd" and got more information than fdisk's "Unable to open /dev/sdd"
```

<snipped>
open("/dev/sdd", O_RDONLY|O_LARGEFILE)  = -1 ENOMEDIUM (No medium found)
open("/dev/sdd", O_RDWR|O_LARGEFILE)    = -1 ENOMEDIUM (No medium found)
open("/dev/sdd", O_RDONLY|O_LARGEFILE)  = -1 ENOMEDIUM (No medium found)
<snipped>
```

"No Medium Found"...Using "parted" I get that message too. gparted doesn't even list the device.

Can't even do this (last chance saloon)
```

root@patb-desktop:~# dd if=/dev/zero of=/dev/sdd
dd: opening `/dev/sdd': No medium found
```

I've tried in several USB ports (read external usb hubs can be a problem) and also tried on my laptop running Fedora 9 - same problem.

Other than opening up the stick and de-soldering/re-soldering etc, I am at a loss as to idea's now. Basically don't remove flash sticks whilst doing a format operation on them :-\"

---

