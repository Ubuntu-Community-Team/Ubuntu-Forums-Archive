---
title: "Card Reader on MSI Wind"
date: 2009-02-07
forum: Hardware
---

### Post by mcbride_62 on 2009-02-07
I can't enable my SD card reader on a headless MSI Wind running Ubuntu Server 8.04.2. From the outputs below, sda is where my OS lives and sdb is a storage drive.  I've inserted the SD card and ran the following commands.  But can't find anything.

test@server:/dev$ sudo fdisk -l

Disk /dev/sda: 4076 MB, 4076642304 bytes
255 heads, 63 sectors/track, 495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00142022

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         495     3976056   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005673e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       53523   429923466    7  HPFS/NTFS
/dev/sdb2           53524       54176     5245222+   c  W95 FAT32 (LBA)
/dev/sdb3           54177       60255    48829567+  83  Linux


test@server:/dev$ cat /etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sdb1 /mnt/share fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0


test@server:/dev$ dmesg | tail -25
[ 6413.325749] sd 6:0:0:0: [sde] Assuming drive cache: write through
[ 6413.325783]  sde: sde1
[ 6413.326897] sd 6:0:0:0: [sde] Attached SCSI removable disk
[ 6413.326972] sd 6:0:0:0: Attached scsi generic sg4 type 0
[ 6740.080332] usb 5-7: USB disconnect, address 4
[ 7545.586963] usb 5-6: USB disconnect, address 3
[ 8513.264587] usb 5-7: new high speed USB device using ehci_hcd and address 5
[ 8513.415540] usb 5-7: configuration #1 chosen from 1 choice
[ 8513.415919] scsi7 : SCSI emulation for USB Mass Storage devices
[ 8513.416248] usb-storage: device found at 5
[ 8513.416254] usb-storage: waiting for device to settle before scanning
[ 8518.410141] usb-storage: device scan complete
[ 8518.410659] scsi 7:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[ 8518.412707] sd 7:0:0:0: [sdd] 4013710 512-byte hardware sectors (2055 MB)
[ 8518.413828] sd 7:0:0:0: [sdd] Write Protect is off
[ 8518.413839] sd 7:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 8518.413844] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 8518.417186] sd 7:0:0:0: [sdd] 4013710 512-byte hardware sectors (2055 MB)
[ 8518.418179] sd 7:0:0:0: [sdd] Write Protect is off
[ 8518.418189] sd 7:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 8518.418195] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 8518.418234]  sdd: sdd1
[ 8518.419983] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[ 8518.420092] sd 7:0:0:0: Attached scsi generic sg3 type 0
[ 8550.849693] usb 5-7: USB disconnect, address 5


Any thoughts?

Thanks in advance.

---

### Post by mcbride_62 on 2009-02-10
Bump

---

### Post by bandofmercy on 2009-07-25
bump

---

