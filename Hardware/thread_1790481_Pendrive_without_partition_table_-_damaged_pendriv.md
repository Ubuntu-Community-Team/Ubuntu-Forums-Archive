---
title: "Pendrive without partition table - damaged pendrive?"
date: 2011-06-25
forum: Hardware
---

### Post by slotwek on 2011-06-25
Hi all,

I tried to solve the problem myself, however I couldn't find solution in Google or in Ubuntu Forum. So, hope this topic will be interesting to you.

The problem is that I wanted to install linux distribution from live-CD to a pendrive (as you normally do for hard drives). So, I divided 32GB into following partitions:
- 16GB vfat (FAT32) - so, I could use it to copy files from windows,
- 10GB ext3 - for main partition /
- 6GB ext3 - for /home partition.

However, during partition process I received an error that system couldn't create FAT32 partition. And from this moment everything fails - I tried to use fdisk, cfdisk, gparted, mkfs to recreate partition table but without luck. The pendrive is new (less than 24hours of purchase) and I managed to brake it. So, there is no worry about recovering data. I just need to make pendrive usable again.

Here are some outputs from terminal - to get you started:

```

#fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0cc30cc3

Device Boot Start End Blocks Id System
/dev/sda1 1 1658 13312000 27 Unknown
/dev/sda2 * 1658 1671 102400 7 HPFS/NTFS
/dev/sda3 1671 11274 77141336 7 HPFS/NTFS
/dev/sda4 11275 65917 438917121 f W95 Ext'd (LBA)
/dev/sda5 11275 36771 204800000 7 HPFS/NTFS
/dev/sda6 36772 41352 36796851 83 Linux
/dev/sda7 41353 65668 195315712 83 Linux
/dev/sda8 65668 65917 1998848 82 Linux swap / Solaris

Disk /dev/sdb: 33.6 GB, 33554432000 bytes
64 heads, 32 sectors/track, 32000 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc1b86192

Disk /dev/sdb doesn't contain a valid partition table

```Yep, my pendrive is /dev/sdb. There is no /dev/sdb1 to do something smart with it

```

#dmesg

[ 1069.126036] usb 2-1.2: USB disconnect, address 5
[ 1078.781927] usb 2-1.2: new high speed USB device using ehci_hcd and address 6
[ 1078.879462] usb 2-1.2: configuration #1 chosen from 1 choice
[ 1078.879775] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1078.880015] usb-storage: device found at 6
[ 1078.880019] usb-storage: waiting for device to settle before scanning
[ 1083.869742] usb-storage: device scan complete
[ 1083.870264] scsi 7:0:0:0: Direct-Access USB 2.0 Flash Disk 1.00 PQ: 0 ANSI: 2
[ 1083.871670] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 1083.872685] sd 7:0:0:0: [sdb] 65536000 512-byte logical blocks: (33.5 GB/31.2 GiB)
[ 1083.873178] sd 7:0:0:0: [sdb] Write Protect is off
[ 1083.873184] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1083.873190] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1083.875050] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1083.875060] sdb: unknown partition table
[ 1085.130177] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1085.130224] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 1248.828304] usb 2-1.2: reset high speed USB device using ehci_hcd and address 6

``````

fdisk /dev/sdb

Unable to open /dev/sdb

``````
# cfdisk /dev/sdb
FATAL ERROR: Cannot open disk drive
Press any key to exit cfdisk

``````

# mkfs.vfat -F 32 /dev/sdb
mkfs.vfat 3.0.7 (24 Dec 2009)
mkfs.vfat: Device partition expected, not making filesystem on entire device '/dev/sdb' (use -I to override)
# mkfs.vfat -F 32 -I /dev/sdb
mkfs.vfat 3.0.7 (24 Dec 2009)
mkfs.vfat: failed whilst writing FAT

``````

# gparted
======================
libparted : 2.2
======================
/dev/sdb: unrecognised disk label
/dev/sdb: unrecognised disk label
/dev/sdb: unrecognised disk label

```Hope you have better ideas to wipe out everything and force pendrive to work again.

---

### Post by coffeecat on 2011-06-25
Clearly you have a corrupted partition table but, unless the hardware has failed, I can't think of a reason why you cannot create a new partition table. This...

> **slotwek said:**
>  And from this moment everything fails - I tried to use fdisk, cfdisk, gparted, mkfs to recreate partition table but without luck.

You don't use mkfs to create a partition table - mkfs creates filesystems.

What did you do in Gparted to try to create a partition table? For the record, this is what you do in Gparted. Show your pendrive in the main pane by choosing it from the drop-down top right. Now, Device menu -> Create partition table. Is that what you've tried already? What happens when you do that? Do you get an error message?

---

### Post by prshah on 2011-06-25
> **slotwek said:**
> 
```

[ 1248.828304] usb 2-1.2: reset high speed USB device using ehci_hcd and address 6

```

That very last line is the clue that the pendrive has not been recognized and made available to the system. Any USB device (Especially Mass Storage Devices) go through a reset when a problem has occurred.

Typically, the problems are power-related; sometimes USB ports (especially self powered hubs) do not output enough power for the device's requirement. 

I'd suggest to you first eliminate this; try connecting your device to one of the back USB ports, rather than through a hub, extender or front USB.

---

### Post by slotwek on 2011-06-25
Quote coffeecat:
> 
Device menu -> Create partition table. Is that what you've tried  already? What happens when you do that? Do you get an error message?     Yes, I did like you said. And then gparted gave:
```
# gparted
======================
libparted : 2.2
======================
/dev/sdb: unrecognised disk label
/dev/sdb: unrecognised disk label
/dev/sdb: unrecognised disk label
```Quote prshah:
> I'd suggest to you first eliminate this; try connecting your device to  one of the back USB ports, rather than through a hub, extender or front  USB. Nice idea. I will try it as soon as I find a spare desktop - probably on Monday at work :-/. All of my laptops (3 in total) have problem with power. It is surprising that in 21st century we have those problems.

Is there any chance to increase power using some linux commands? Or is it purely hardware issue?

---

### Post by prshah on 2011-06-26
> **slotwek said:**
> 
```
/dev/sdb: unrecognised disk label
/dev/sdb: unrecognised disk label
```

I will try it as soon as I find a spare desktop - probably on Monday at work :-/. All of my laptops (3 in total) have problem with power.

Is there any chance to increase power using some linux commands? Or is it purely hardware issue?

Nope, USB power is purely under hardware control.

However, if you are facing the problem in all 3 laptops, then I doubt the power is the issue.

As for "unrecognized disk label" error, in gparted, if you can select "/dev/sdb", then you can write in a fresh disklabel by clicking the "Device" menu, and then selecting the "Set Disklabel" option. MAKE SURE YOU SELECT THE CORRECT DEVICE BEFORE DOING THIS! Then click "Apply" and then try to make your partitions.

---

### Post by slooksterpsv on 2011-06-26
Did you try a different USB port? It sounds strange, but I only ask cause I've had an issue where one of my flash drives partition table corrupts if it's in one port (port is damaged, but I keep forgetting to mark it so I don't use it).

---

### Post by slotwek on 2011-06-26
Thank you guys for your interest in the topic. I think I messed up things a bit more.

Yesterday, I went to my colleague to try some stuff and he tried to format the drive under Windows 7. The outcome is that Windows 7 wants to format the pendrive with lower size 14.8 MB instead 32GB. And of course, it fails because pendrive is in read-only mode.

dmesg shows:
```
#dmesg
[  473.087383] sd 6:0:0:0: [sdb] Unhandled error code
[  473.087387] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  473.087391] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  473.087403] end_request: I/O error, dev sdb, sector 0
[  473.092149] sd 6:0:0:0: [sdb] Unhandled error code
[  473.092153] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  473.092159] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  473.092171] end_request: I/O error, dev sdb, sector 8
[  473.097118] sd 6:0:0:0: [sdb] Unhandled error code
[  473.097123] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  473.097127] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  473.097140] end_request: I/O error, dev sdb, sector 128
[  473.101630] sd 6:0:0:0: [sdb] Unhandled error code
[  473.101635] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  473.101639] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  473.101651] end_request: I/O error, dev sdb, sector 0
[  473.106480] sd 6:0:0:0: [sdb] Unhandled error code
[  473.106485] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  473.106490] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  473.106503] end_request: I/O error, dev sdb, sector 0
[  473.111111] sd 6:0:0:0: [sdb] Unhandled error code
[  473.111115] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  473.111119] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[  473.111132] end_request: I/O error, dev sdb, sector 4096
[  473.122176] sd 6:0:0:0: [sdb] Unhandled error code
[  473.122181] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  473.122187] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  473.122201] end_request: I/O error, dev sdb, sector 0
[  473.126682] sd 6:0:0:0: [sdb] Unhandled error code
[  473.126687] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  473.126692] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  473.126704] end_request: I/O error, dev sdb, sector 0
[  473.131324] sd 6:0:0:0: [sdb] Unhandled error code
[  473.131328] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  473.131333] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  473.131345] end_request: I/O error, dev sdb, sector 0
[  474.438309] sd 6:0:0:0: [sdb] Unhandled error code
[  474.438315] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.438321] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 76 80 00 00 08 00
[  474.438335] end_request: I/O error, dev sdb, sector 30336
[  474.442864] sd 6:0:0:0: [sdb] Unhandled error code
[  474.442867] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.442872] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 76 80 00 00 08 00
[  474.442884] end_request: I/O error, dev sdb, sector 30336
[  474.447357] sd 6:0:0:0: [sdb] Unhandled error code
[  474.447362] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.447368] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 10 00 00 08 00
[  474.447381] end_request: I/O error, dev sdb, sector 30480
[  474.451888] sd 6:0:0:0: [sdb] Unhandled error code
[  474.451892] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.451897] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 10 00 00 08 00
[  474.451909] end_request: I/O error, dev sdb, sector 30480
[  474.456477] sd 6:0:0:0: [sdb] Unhandled error code
[  474.456481] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.456485] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.456498] end_request: I/O error, dev sdb, sector 0
[  474.461023] sd 6:0:0:0: [sdb] Unhandled error code
[  474.461027] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.461032] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.461044] end_request: I/O error, dev sdb, sector 0
[  474.465637] sd 6:0:0:0: [sdb] Unhandled error code
[  474.465641] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.465646] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  474.465658] end_request: I/O error, dev sdb, sector 8
[  474.469607] sd 6:0:0:0: [sdb] Unhandled error code
[  474.469611] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.469616] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[  474.469628] end_request: I/O error, dev sdb, sector 30496
[  474.473454] sd 6:0:0:0: [sdb] Unhandled error code
[  474.473458] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.473462] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[  474.473475] end_request: I/O error, dev sdb, sector 30496
[  474.477329] sd 6:0:0:0: [sdb] Unhandled error code
[  474.477335] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.477341] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[  474.477358] end_request: I/O error, dev sdb, sector 30496
[  474.481173] sd 6:0:0:0: [sdb] Unhandled error code
[  474.481179] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.481185] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[  474.481201] end_request: I/O error, dev sdb, sector 30496
[  474.485054] sd 6:0:0:0: [sdb] Unhandled error code
[  474.485059] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.485065] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[  474.485082] end_request: I/O error, dev sdb, sector 30496
[  474.488897] sd 6:0:0:0: [sdb] Unhandled error code
[  474.488902] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.488908] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[  474.488931] end_request: I/O error, dev sdb, sector 30496
[  474.493425] sd 6:0:0:0: [sdb] Unhandled error code
[  474.493430] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.493434] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 76 e0 00 00 08 00
[  474.493447] end_request: I/O error, dev sdb, sector 30432
[  474.497286] sd 6:0:0:0: [sdb] Unhandled error code
[  474.497290] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.497295] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 18 00 00 03 00
[  474.497307] end_request: I/O error, dev sdb, sector 30488
[  474.497312] __ratelimit: 4032 callbacks suppressed
[  474.497315] Buffer I/O error on device sdb, logical block 30488
[  474.497319] Buffer I/O error on device sdb, logical block 30489
[  474.497323] Buffer I/O error on device sdb, logical block 30490
[  474.497327] Buffer I/O error on device sdb, logical block 30491
[  474.497330] Buffer I/O error on device sdb, logical block 30492
[  474.497334] Buffer I/O error on device sdb, logical block 30493
[  474.497338] Buffer I/O error on device sdb, logical block 30494
[  474.497341] Buffer I/O error on device sdb, logical block 30495
[  474.501908] sd 6:0:0:0: [sdb] Unhandled error code
[  474.501912] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.501916] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  474.501929] end_request: I/O error, dev sdb, sector 8
[  474.501933] Buffer I/O error on device sdb, logical block 8
[  474.501937] Buffer I/O error on device sdb, logical block 9
[  474.506525] sd 6:0:0:0: [sdb] Unhandled error code
[  474.506529] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.506534] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  474.506546] end_request: I/O error, dev sdb, sector 8
[  474.510395] sd 6:0:0:0: [sdb] Unhandled error code
[  474.510399] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.510403] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[  474.510415] end_request: I/O error, dev sdb, sector 30496
[  474.514262] sd 6:0:0:0: [sdb] Unhandled error code
[  474.514266] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.514270] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[  474.514282] end_request: I/O error, dev sdb, sector 30496
[  474.518236] sd 6:0:0:0: [sdb] Unhandled error code
[  474.518240] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.518245] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 18 00 00 03 00
[  474.518257] end_request: I/O error, dev sdb, sector 30488
[  474.522705] sd 6:0:0:0: [sdb] Unhandled error code
[  474.522709] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.522714] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.522726] end_request: I/O error, dev sdb, sector 0
[  474.527236] sd 6:0:0:0: [sdb] Unhandled error code
[  474.527241] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.527245] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.527257] end_request: I/O error, dev sdb, sector 0
[  474.531889] sd 6:0:0:0: [sdb] Unhandled error code
[  474.531893] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.531898] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.531910] end_request: I/O error, dev sdb, sector 0
[  474.536479] sd 6:0:0:0: [sdb] Unhandled error code
[  474.536483] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.536488] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.536500] end_request: I/O error, dev sdb, sector 0
[  474.541071] sd 6:0:0:0: [sdb] Unhandled error code
[  474.541075] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.541080] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.541092] end_request: I/O error, dev sdb, sector 0
[  474.545569] sd 6:0:0:0: [sdb] Unhandled error code
[  474.545573] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.545578] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.545590] end_request: I/O error, dev sdb, sector 0
[  474.550211] sd 6:0:0:0: [sdb] Unhandled error code
[  474.550215] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.550220] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.550232] end_request: I/O error, dev sdb, sector 0
[  474.554762] sd 6:0:0:0: [sdb] Unhandled error code
[  474.554766] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.554771] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 00 00 00 08 00
[  474.554783] end_request: I/O error, dev sdb, sector 2048
[  474.559253] sd 6:0:0:0: [sdb] Unhandled error code
[  474.559257] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.559261] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.559273] end_request: I/O error, dev sdb, sector 0
[  474.563911] sd 6:0:0:0: [sdb] Unhandled error code
[  474.563915] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.563920] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.563932] end_request: I/O error, dev sdb, sector 0
[  474.568428] sd 6:0:0:0: [sdb] Unhandled error code
[  474.568432] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.568437] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.568449] end_request: I/O error, dev sdb, sector 0
[  474.573013] sd 6:0:0:0: [sdb] Unhandled error code
[  474.573018] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.573022] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.573034] end_request: I/O error, dev sdb, sector 0
[  474.577619] sd 6:0:0:0: [sdb] Unhandled error code
[  474.577623] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.577628] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.577640] end_request: I/O error, dev sdb, sector 0
[  474.582098] sd 6:0:0:0: [sdb] Unhandled error code
[  474.582102] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.582106] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.582118] end_request: I/O error, dev sdb, sector 0
[  474.586615] sd 6:0:0:0: [sdb] Unhandled error code
[  474.586619] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.586624] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.586636] end_request: I/O error, dev sdb, sector 0
[  474.591243] sd 6:0:0:0: [sdb] Unhandled error code
[  474.591247] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.591251] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.591263] end_request: I/O error, dev sdb, sector 0
[  474.595847] sd 6:0:0:0: [sdb] Unhandled error code
[  474.595851] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.595856] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.595868] end_request: I/O error, dev sdb, sector 0
[  474.600446] sd 6:0:0:0: [sdb] Unhandled error code
[  474.600450] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.600455] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.600467] end_request: I/O error, dev sdb, sector 0
[  474.604950] sd 6:0:0:0: [sdb] Unhandled error code
[  474.604954] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.604959] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.604971] end_request: I/O error, dev sdb, sector 0
[  474.609541] sd 6:0:0:0: [sdb] Unhandled error code
[  474.609545] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.609549] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.609561] end_request: I/O error, dev sdb, sector 0
[  474.614017] sd 6:0:0:0: [sdb] Unhandled error code
[  474.614020] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.614025] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  474.614037] end_request: I/O error, dev sdb, sector 8
[  474.618549] sd 6:0:0:0: [sdb] Unhandled error code
[  474.618553] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.618557] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  474.618569] end_request: I/O error, dev sdb, sector 8
[  474.622999] sd 6:0:0:0: [sdb] Unhandled error code
[  474.623002] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.623007] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  474.623019] end_request: I/O error, dev sdb, sector 8
[  474.627530] sd 6:0:0:0: [sdb] Unhandled error code
[  474.627534] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.627538] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  474.627550] end_request: I/O error, dev sdb, sector 8
[  474.632131] sd 6:0:0:0: [sdb] Unhandled error code
[  474.632135] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.632140] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[  474.632152] end_request: I/O error, dev sdb, sector 24
[  474.636634] sd 6:0:0:0: [sdb] Unhandled error code
[  474.636638] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.636643] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[  474.636655] end_request: I/O error, dev sdb, sector 24
[  474.641226] sd 6:0:0:0: [sdb] Unhandled error code
[  474.641230] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.641234] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[  474.641246] end_request: I/O error, dev sdb, sector 24
[  474.645751] sd 6:0:0:0: [sdb] Unhandled error code
[  474.645755] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.645760] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[  474.645772] end_request: I/O error, dev sdb, sector 24
[  474.650374] sd 6:0:0:0: [sdb] Unhandled error code
[  474.650378] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.650383] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  474.650395] end_request: I/O error, dev sdb, sector 56
[  474.655059] sd 6:0:0:0: [sdb] Unhandled error code
[  474.655063] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.655067] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  474.655079] end_request: I/O error, dev sdb, sector 56
[  474.659559] sd 6:0:0:0: [sdb] Unhandled error code
[  474.659563] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.659568] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  474.659580] end_request: I/O error, dev sdb, sector 56
[  474.664040] sd 6:0:0:0: [sdb] Unhandled error code
[  474.664044] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.664048] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  474.664060] end_request: I/O error, dev sdb, sector 56
[  474.668574] sd 6:0:0:0: [sdb] Unhandled error code
[  474.668579] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.668583] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  474.668596] end_request: I/O error, dev sdb, sector 120
[  474.673165] sd 6:0:0:0: [sdb] Unhandled error code
[  474.673169] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.673173] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  474.673185] end_request: I/O error, dev sdb, sector 120
[  474.677651] sd 6:0:0:0: [sdb] Unhandled error code
[  474.677655] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.677659] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  474.677671] end_request: I/O error, dev sdb, sector 120
[  474.682142] sd 6:0:0:0: [sdb] Unhandled error code
[  474.682146] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.682151] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  474.682163] end_request: I/O error, dev sdb, sector 120
[  474.686635] sd 6:0:0:0: [sdb] Unhandled error code
[  474.686639] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.686644] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.686656] end_request: I/O error, dev sdb, sector 0
[  474.691110] sd 6:0:0:0: [sdb] Unhandled error code
[  474.691114] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.691119] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.691131] end_request: I/O error, dev sdb, sector 0
[  474.695616] sd 6:0:0:0: [sdb] Unhandled error code
[  474.695620] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.695625] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  474.695637] end_request: I/O error, dev sdb, sector 8
[  474.700092] sd 6:0:0:0: [sdb] Unhandled error code
[  474.700096] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.700100] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  474.700112] end_request: I/O error, dev sdb, sector 8
[  474.704634] sd 6:0:0:0: [sdb] Unhandled error code
[  474.704638] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.704643] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[  474.704655] end_request: I/O error, dev sdb, sector 24
[  474.709215] sd 6:0:0:0: [sdb] Unhandled error code
[  474.709219] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.709223] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[  474.709235] end_request: I/O error, dev sdb, sector 24
[  474.713714] sd 6:0:0:0: [sdb] Unhandled error code
[  474.713718] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.713722] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  474.713734] end_request: I/O error, dev sdb, sector 56
[  474.718195] sd 6:0:0:0: [sdb] Unhandled error code
[  474.718199] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.718203] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  474.718215] end_request: I/O error, dev sdb, sector 56
[  474.722712] sd 6:0:0:0: [sdb] Unhandled error code
[  474.722716] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.722720] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  474.722732] end_request: I/O error, dev sdb, sector 120
[  474.727162] sd 6:0:0:0: [sdb] Unhandled error code
[  474.727166] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.727170] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[  474.727182] end_request: I/O error, dev sdb, sector 120
[  474.731710] sd 6:0:0:0: [sdb] Unhandled error code
[  474.731713] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.731718] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.731730] end_request: I/O error, dev sdb, sector 0
[  474.736416] sd 6:0:0:0: [sdb] Unhandled error code
[  474.736421] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.736425] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.736437] end_request: I/O error, dev sdb, sector 0
[  474.740915] sd 6:0:0:0: [sdb] Unhandled error code
[  474.740919] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.740924] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.740936] end_request: I/O error, dev sdb, sector 0
[  474.745375] sd 6:0:0:0: [sdb] Unhandled error code
[  474.745379] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.745384] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.745396] end_request: I/O error, dev sdb, sector 0
[  474.749894] sd 6:0:0:0: [sdb] Unhandled error code
[  474.749898] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.749903] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.749915] end_request: I/O error, dev sdb, sector 0
[  474.754409] sd 6:0:0:0: [sdb] Unhandled error code
[  474.754413] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.754418] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.754430] end_request: I/O error, dev sdb, sector 0
[  474.759027] sd 6:0:0:0: [sdb] Unhandled error code
[  474.759031] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.759036] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[  474.759048] end_request: I/O error, dev sdb, sector 16
[  474.763642] sd 6:0:0:0: [sdb] Unhandled error code
[  474.763647] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.763651] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  474.763663] end_request: I/O error, dev sdb, sector 128
[  474.768220] sd 6:0:0:0: [sdb] Unhandled error code
[  474.768224] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.768228] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  474.768240] end_request: I/O error, dev sdb, sector 128
[  474.772860] sd 6:0:0:0: [sdb] Unhandled error code
[  474.772864] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.772869] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  474.772881] end_request: I/O error, dev sdb, sector 128
[  474.777450] sd 6:0:0:0: [sdb] Unhandled error code
[  474.777454] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.777459] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[  474.777471] end_request: I/O error, dev sdb, sector 16
[  474.781952] sd 6:0:0:0: [sdb] Unhandled error code
[  474.781956] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.781960] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  474.781972] end_request: I/O error, dev sdb, sector 128
[  474.786442] sd 6:0:0:0: [sdb] Unhandled error code
[  474.786446] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.786451] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  474.786463] end_request: I/O error, dev sdb, sector 64
[  474.790933] sd 6:0:0:0: [sdb] Unhandled error code
[  474.790937] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.790942] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  474.790954] end_request: I/O error, dev sdb, sector 64
[  474.795424] sd 6:0:0:0: [sdb] Unhandled error code
[  474.795428] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.795432] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  474.795444] end_request: I/O error, dev sdb, sector 64
[  474.799934] sd 6:0:0:0: [sdb] Unhandled error code
[  474.799938] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.799943] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  474.799955] end_request: I/O error, dev sdb, sector 64
[  474.804543] sd 6:0:0:0: [sdb] Unhandled error code
[  474.804547] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.804552] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  474.804564] end_request: I/O error, dev sdb, sector 64
[  474.809178] sd 6:0:0:0: [sdb] Unhandled error code
[  474.809182] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.809187] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  474.809199] end_request: I/O error, dev sdb, sector 64
[  474.813762] sd 6:0:0:0: [sdb] Unhandled error code
[  474.813766] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.813771] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  474.813783] end_request: I/O error, dev sdb, sector 64
[  474.818251] sd 6:0:0:0: [sdb] Unhandled error code
[  474.818255] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.818259] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  474.818271] end_request: I/O error, dev sdb, sector 64
[  474.822745] sd 6:0:0:0: [sdb] Unhandled error code
[  474.822749] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.822753] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  474.822765] end_request: I/O error, dev sdb, sector 64
[  474.827234] sd 6:0:0:0: [sdb] Unhandled error code
[  474.827238] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.827242] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.827255] end_request: I/O error, dev sdb, sector 0
[  474.831733] sd 6:0:0:0: [sdb] Unhandled error code
[  474.831737] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.831742] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.831754] end_request: I/O error, dev sdb, sector 0
[  474.836229] sd 6:0:0:0: [sdb] Unhandled error code
[  474.836233] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.836238] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.836250] end_request: I/O error, dev sdb, sector 0
[  474.840808] sd 6:0:0:0: [sdb] Unhandled error code
[  474.840812] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.840817] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.840829] end_request: I/O error, dev sdb, sector 0
[  474.845297] sd 6:0:0:0: [sdb] Unhandled error code
[  474.845301] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.845305] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.845317] end_request: I/O error, dev sdb, sector 0
[  474.849788] sd 6:0:0:0: [sdb] Unhandled error code
[  474.849792] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.849796] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[  474.849808] end_request: I/O error, dev sdb, sector 16
[  474.854348] sd 6:0:0:0: [sdb] Unhandled error code
[  474.854352] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.854356] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.854368] end_request: I/O error, dev sdb, sector 0
[  474.858938] sd 6:0:0:0: [sdb] Unhandled error code
[  474.858942] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.858947] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.858959] end_request: I/O error, dev sdb, sector 0
[  474.863455] sd 6:0:0:0: [sdb] Unhandled error code
[  474.863459] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.863464] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.863476] end_request: I/O error, dev sdb, sector 0
[  474.868001] sd 6:0:0:0: [sdb] Unhandled error code
[  474.868005] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.868009] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.868022] end_request: I/O error, dev sdb, sector 0
[  474.872644] sd 6:0:0:0: [sdb] Unhandled error code
[  474.872648] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.872653] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.872665] end_request: I/O error, dev sdb, sector 0
[  474.877108] sd 6:0:0:0: [sdb] Unhandled error code
[  474.877112] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.877116] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.877128] end_request: I/O error, dev sdb, sector 0
[  474.881613] sd 6:0:0:0: [sdb] Unhandled error code
[  474.881617] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.881622] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.881634] end_request: I/O error, dev sdb, sector 0
[  474.886101] sd 6:0:0:0: [sdb] Unhandled error code
[  474.886105] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.886110] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.886122] end_request: I/O error, dev sdb, sector 0
[  474.890594] sd 6:0:0:0: [sdb] Unhandled error code
[  474.890598] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.890603] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.890615] end_request: I/O error, dev sdb, sector 0
[  474.895113] sd 6:0:0:0: [sdb] Unhandled error code
[  474.895117] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.895122] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.895134] end_request: I/O error, dev sdb, sector 0
[  474.899700] sd 6:0:0:0: [sdb] Unhandled error code
[  474.899704] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.899708] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.899720] end_request: I/O error, dev sdb, sector 0
[  474.904218] sd 6:0:0:0: [sdb] Unhandled error code
[  474.904222] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.904226] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.904239] end_request: I/O error, dev sdb, sector 0
[  474.908823] sd 6:0:0:0: [sdb] Unhandled error code
[  474.908827] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.908831] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.908843] end_request: I/O error, dev sdb, sector 0
[  474.913287] sd 6:0:0:0: [sdb] Unhandled error code
[  474.913291] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.913296] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.913308] end_request: I/O error, dev sdb, sector 0
[  474.917776] sd 6:0:0:0: [sdb] Unhandled error code
[  474.917780] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.917785] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.917797] end_request: I/O error, dev sdb, sector 0
[  474.922266] sd 6:0:0:0: [sdb] Unhandled error code
[  474.922270] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.922275] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.922287] end_request: I/O error, dev sdb, sector 0
[  474.926798] sd 6:0:0:0: [sdb] Unhandled error code
[  474.926802] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.926807] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.926819] end_request: I/O error, dev sdb, sector 0
[  474.931290] sd 6:0:0:0: [sdb] Unhandled error code
[  474.931294] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.931299] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.931311] end_request: I/O error, dev sdb, sector 0
[  474.935878] sd 6:0:0:0: [sdb] Unhandled error code
[  474.935882] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.935887] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[  474.935906] end_request: I/O error, dev sdb, sector 8
[  474.940520] sd 6:0:0:0: [sdb] Unhandled error code
[  474.940524] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.940529] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[  474.940541] end_request: I/O error, dev sdb, sector 128
[  474.945096] sd 6:0:0:0: [sdb] Unhandled error code
[  474.945100] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.945104] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.945116] end_request: I/O error, dev sdb, sector 0
[  474.949602] sd 6:0:0:0: [sdb] Unhandled error code
[  474.949607] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.949612] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  474.949625] end_request: I/O error, dev sdb, sector 0
[  474.954076] sd 6:0:0:0: [sdb] Unhandled error code
[  474.954080] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  474.954085] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[  474.954097] end_request: I/O error, dev sdb, sector 4096

```Linux does not shot the drive any more using fdisk -l

cfdisk shows:
```

cfdisk /dev/sdb
Opened disk read-only - you have no permission to write
FATAL ERROR: Cannot read disk drive
Press any key to exit cfdisk

```After those commands dmesg shows:
```

[  925.997025] sd 6:0:0:0: [sdb] Unhandled error code
[  925.997032] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  925.997040] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  925.997057] end_request: I/O error, dev sdb, sector 0
[  925.997063] __ratelimit: 796 callbacks suppressed
[  925.997068] Buffer I/O error on device sdb, logical block 0
[  925.997074] Buffer I/O error on device sdb, logical block 1
[  925.997079] Buffer I/O error on device sdb, logical block 2
[  925.997083] Buffer I/O error on device sdb, logical block 3
[  925.997088] Buffer I/O error on device sdb, logical block 4
[  925.997092] Buffer I/O error on device sdb, logical block 5
[  925.997097] Buffer I/O error on device sdb, logical block 6
[  925.997101] Buffer I/O error on device sdb, logical block 7
[  926.001643] sd 6:0:0:0: [sdb] Unhandled error code
[  926.001648] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  926.001653] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  926.001665] end_request: I/O error, dev sdb, sector 0
[  926.001670] Buffer I/O error on device sdb, logical block 0
[  926.001674] Buffer I/O error on device sdb, logical block 1
[  926.008983] sd 6:0:0:0: [sdb] Unhandled error code
[  926.008989] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  926.008995] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 20 00
[  926.009011] end_request: I/O error, dev sdb, sector 0
[  926.013597] sd 6:0:0:0: [sdb] Unhandled error code
[  926.013605] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  926.013612] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  926.013629] end_request: I/O error, dev sdb, sector 0
[  926.017501] sd 6:0:0:0: [sdb] Unhandled error code
[  926.017507] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  926.017514] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[  926.017532] end_request: I/O error, dev sdb, sector 30496
[  926.021497] sd 6:0:0:0: [sdb] Unhandled error code
[  926.021504] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  926.021511] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[  926.021528] end_request: I/O error, dev sdb, sector 30496
[  926.029641] sd 6:0:0:0: [sdb] Unhandled error code
[  926.029648] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  926.029654] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 20 00
[  926.029668] end_request: I/O error, dev sdb, sector 0
[  926.033734] sd 6:0:0:0: [sdb] Unhandled error code
[  926.033738] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  926.033744] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  926.033757] end_request: I/O error, dev sdb, sector 0
[  926.038220] sd 6:0:0:0: [sdb] Unhandled error code
[  926.038224] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  926.038228] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 07 00
[  926.038241] end_request: I/O error, dev sdb, sector 1
[ 1094.890094] sd 6:0:0:0: [sdb] Unhandled error code
[ 1094.890100] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1094.890105] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 20 00
[ 1094.890116] end_request: I/O error, dev sdb, sector 0
[ 1094.890122] __ratelimit: 92 callbacks suppressed
[ 1094.890125] Buffer I/O error on device sdb, logical block 0
[ 1094.890130] Buffer I/O error on device sdb, logical block 1
[ 1094.890133] Buffer I/O error on device sdb, logical block 2
[ 1094.890136] Buffer I/O error on device sdb, logical block 3
[ 1094.890139] Buffer I/O error on device sdb, logical block 4
[ 1094.890142] Buffer I/O error on device sdb, logical block 5
[ 1094.890145] Buffer I/O error on device sdb, logical block 6
[ 1094.890148] Buffer I/O error on device sdb, logical block 7
[ 1094.890153] Buffer I/O error on device sdb, logical block 8
[ 1094.890156] Buffer I/O error on device sdb, logical block 9
[ 1094.894693] sd 6:0:0:0: [sdb] Unhandled error code
[ 1094.894697] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1094.894702] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1094.894714] end_request: I/O error, dev sdb, sector 0
[ 1094.898595] sd 6:0:0:0: [sdb] Unhandled error code
[ 1094.898601] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1094.898607] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[ 1094.898623] end_request: I/O error, dev sdb, sector 30496
[ 1094.902425] sd 6:0:0:0: [sdb] Unhandled error code
[ 1094.902430] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1094.902434] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 77 20 00 00 01 00
[ 1094.902447] end_request: I/O error, dev sdb, sector 30496
[ 1094.907040] sd 6:0:0:0: [sdb] Unhandled error code
[ 1094.907044] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1094.907048] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1094.907060] end_request: I/O error, dev sdb, sector 0

```

---

### Post by slotwek on 2011-06-26
> Did you try a different USB port? It sounds strange, but I only ask  cause I've had an issue where one of my flash drives partition table  corrupts if it's in one port (port is damaged, but I keep forgetting to  mark it so I don't use it).

I tried 3 of 4 ports on my main laptop. On other ones I check on 1-2 each. I don't think the port would be an issue.

---

### Post by slooksterpsv on 2011-06-26
In windows you'd need to go to:

diskmgmt.msc

Or right-click on Computer -> Manage -> Disks and... something -> Right-click on the disk and delete it.

The port idea, yeah I just know that sometimes when copying data or anything with one port on mine, the port is damage to where it works, but it either has slow data rate or it corrupts the data (not sure how exactly, but the port is damaged that bad, yet it still works).

Anyways when I had this problem with my 2GB Flash drive, I think, if I remember correctly, I took an ISO I had ripped and did the following:

sudo dd if=/home/shawn/Downloads/ISO/ubuntu-10.10-amd64.iso of=/dev/sdb

Just some random iso I had, and overwrote the device that way, after that I took out the drive, put it back in and was able to redo the partition scheme on it. So I'd try that.

---

### Post by slotwek on 2011-06-26
On windows:
> In windows you'd need to go to:

diskmgmt.msc

Or right-click on Computer -> Manage -> Disks and... something -> Right-click on the disk and delete it.
Unfortunately this impossible - option is greyed out. 

On linux:
> Anyways when I had this problem with my 2GB Flash drive, I think, if I  remember correctly, I took an ISO I had ripped and did the following:

sudo dd if=/home/shawn/Downloads/ISO/ubuntu-10.10-amd64.iso of=/dev/sdb

Just some random iso I had, and overwrote the device that way, after  that I took out the drive, put it back in and was able to redo the  partition scheme on it. So I'd try that.     This gives:
```
# dd if=BT5-GNOME-32.iso of=/dev/sdb
dd: opening `/dev/sdb': Read-only file system
```

---

### Post by prshah on 2011-06-27
> **slotwek said:**
> The outcome is that Windows 7 wants to format the pendrive with lower size 14.8 MB instead 32GB. 

Heh, sorry, looks to me like you got rooked. This looks similar to the typical china+ebay 32GB/64GB cheap flash drive scam. 

Basically, the controller is reprogrammed to report a higher limit than the actual memory.

Read about a similar problem: [Punter bags 500GB SSD, finds 128MB Flash inside]("http://www.reghardware.com/2011/04/11/russian_duped_by_chinese_ssd_scammers/")

Is your purchase source reliable? Most pendrives come with 5 year to "lifetime" warranties. I'd suggest you attempt to get a replacement.

---

### Post by slotwek on 2011-07-02
@prshah - I think you're right. I've checked some on-line sources about fake pendrives. Basically, I had almost all of the problems mentioned there. So, I sent my pendrive back and I'm waiting for reply and refund. 

Thank you guys for your time and support. 

PS. How I can change post to solved?

---

