---
title: "USB Drive works in Knoppix and Win  XP but not Ubuntu"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by digital21c on 2005-02-09
My trusty USB drive works fine in Knoppix 3.7 and Windows XP, but I can't get it working in Ubuntu (Warty).  When I attempt any mount operation with it, I get the message "Can't read superblock".  

I've tried reformatting the device as FAT and FAT32 in Win XP, and deleting and re-creating partitions and filesystems with parted.  Nothing I tried has helped.

Where have I gone wrong?  What should I try next?

When I use the device under Knoppix ...

...dmesg shows:
hub.c: new USB device 00:1d.1-2, assigned address 2
scsi2 : SCSI emulation for USB Mass Storage devices
  Vendor: 256MB     Model: HardDrive         Rev: 1.88
  Type:   Direct-Access                      ANSI SCSI revision: 02
Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
sda: Write Protect is off
 sda: sda1
WARNING: USB Mass Storage data integrity not assured
USB Mass Storage device found at 2

... mount shows:
/dev/sda1 on /mnt/sda1 type vfat (rw,nosuid,nodev,umask=000,uid=1000,gid=1000)

... cat /etc/mtab shows:
/dev/sda1 /mnt/sda1 vfat rw,nosuid,nodev,umask=000,uid=1000,gid=1000 0 0


Thanks.

---

