---
title: "formatting usb drive"
date: 2010-10-05
forum: Hardware
---

### Post by leg on 2010-10-05
I have some usb flash drives that I need to reformat but am having a problem with. The drives are 4gb in size and have been divided into two partitions of 1.5gb and 2.5gb the 1.5gb partition has an isofs file system on it. I need to reformat the drive so that it is one 4gb partition but I cannot get at the 1.5gb partition at all. Even though it shows up fine when you plug the drive in gparted can't see it at all and I can't repartition the drive. Any ideas as to how I can do this please.

Thanks

---

### Post by dabl on 2010-10-05
*** WARNING:  The "dd" command is also known as "data-destroyer" -- be very careful that you know the device ID before you run "dd" ***

1. Insert a USB stick in your running *buntu system.  If it is automatically mounted, you will need to unmount it ("eject" from your file manager, the "umount" command, click the lock in the GParted view, or whatever).

2. With it unmounted, verify its device designation with ```
sudo fdisk -lu
```

Let's say it is /dev/sd_f_

3. ```
sudo dd if=/dev/zero of=/dev/sdf bs=512 count=1
```

4. Now it is "zeroised" -- there is no partition table on it.  So, you need to start GParted, and browse to the USB device.  Choose "Device > New Partition Table" and choose "MS-DOS" as the table type.

5. Now you can set the partition -- sounds like you want a single partition, so that's what you choose, and choose the filesystem type (FAT or ext2, probably), and "Apply" and you'll be done.

---

### Post by leg on 2010-10-06
Ok yes it is mounted automatically and I can browse that partition and unmount it the problem is that it does not show up in gparted at all. I know the device is sdc as that is what the second partition will show up as. Will your instructions still work? Also is there a method to do this on a Windows machine also as I have a few people with these drives and not all of them are Ubuntu users.

Thanks for replying.

---

### Post by leg on 2010-10-07
```
[  698.930081] usb 2-3: new high speed USB device using ehci_hcd and address 2
[  699.081582] usb 2-3: configuration #1 chosen from 1 choice
[  699.082246] scsi7 : SCSI emulation for USB Mass Storage devices
[  699.082431] usb-storage: device found at 2
[  699.082435] usb-storage: waiting for device to settle before scanning
[  704.080234] usb-storage: device scan complete
[  704.080718] scsi 7:0:0:0: CD-ROM            usb      flash drive      1.00 PQ: 0 ANSI: 2
[  704.081193] scsi 7:0:0:1: Direct-Access     usb      flash drive      1.00 PQ: 0 ANSI: 2
[  704.085414] sr1: scsi3-mmc drive: 15x/15x writer cd/rw xa/form2 cdda tray
[  704.085623] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  704.085740] sr 7:0:0:0: Attached scsi generic sg3 type 5
[  704.086024] sd 7:0:0:1: Attached scsi generic sg4 type 0
[  704.086804] sd 7:0:0:1: [sdc] 5251072 512-byte logical blocks: (2.68 GB/2.50 GiB)
[  704.087509] sd 7:0:0:1: [sdc] Write Protect is off
[  704.087516] sd 7:0:0:1: [sdc] Mode Sense: 0b 00 00 08
[  704.087520] sd 7:0:0:1: [sdc] Assuming drive cache: write through
[  704.089289] sd 7:0:0:1: [sdc] Assuming drive cache: write through
[  704.089299]  sdc:
[  704.181540] sd 7:0:0:1: [sdc] Assuming drive cache: write through
[  704.181548] sd 7:0:0:1: [sdc] Attached SCSI removable disk
[  704.495545] ISO 9660 Extensions: Microsoft Joliet Level 3
[  704.532076] ISOFS: changing to secondary root
lg@apollo:~$ sudo fdisk -lu
[sudo] password for lg: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x983f7c98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS
/dev/sda3        30801920   519848651   244523366    7  HPFS/NTFS
/dev/sda4       519863400   976768064   228452332+   5  Extended
/dev/sda5       519863463   958164794   219150666   83  Linux
/dev/sda6       958164858   976768064     9301603+  82  Linux swap / Solaris

Disk /dev/sdc: 2688 MB, 2688548864 bytes
83 heads, 62 sectors/track, 1020 cylinders, total 5251072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2fec

   Device Boot      Start         End      Blocks   Id  System

```
This is the dmesg after plugging the drive in and the output of the command sudo fdisk -lu.

sda is my internal hard drive and I think the drive I am after is sr1. If I check in /dev/ the file sr1 states that there is no attached disk. Running the dd command you gave me on sdr has no affect. Can you help me please.

---

