---
title: "Seagate External HDD won't mount"
date: 2009-04-09
forum: Hardware
---

### Post by aw4lly on 2009-04-09
Hello,

I have just bought a Seagate 1.5 TB HDD which I put it an Xcraft External Hard drive case. I had some troubles getting it work format initially so I used Vista to format the drive to NTFS as I'm not good enough with the command line to do it properly in Ubuntu.

Anyway I go the drive to format under Vista, moved my files from my old HDD over and it was working fine. I then decided to ditch windows and go back to ubuntu. But now I can't find out how to mount the drive properly. I have read the forums but have been unable to find out what I need to do, if someone could help me get this mounted it would be great

(I am using a Dell M1530 running Ubuntu Hardy)


********************************************************
The output of fdisk -l:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       22244   178622297+   7  HPFS/NTFS
/dev/sda3           22345       38913   133090492+   f  W95 Ext'd (LBA)
/dev/sda5           38522       38913     3148708+  dd  Unknown
/dev/sda6           22345       23339     7992274+  82  Linux swap / Solaris
/dev/sda7           23340       27074    30001356   83  Linux
/dev/sda8           27075       38521    91947996   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3af884ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182402  1465136128    7  HPFS/NTFS


************************************************
Output of df -h

Filesystem            Size Used Avail Use% Mounted on
/dev/sda7              29G  4.0G   23G  15% /
varrun                1.8G  124K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G   88K  1.8G   1% /dev
devshm                1.8G   12K  1.8G   1% /dev/shm
lrm                   1.8G   39M  1.7G   3% /lib/modules/2.6.24-23-generic/volatile
/dev/sda8              87G   39G   45G  47% /home
gvfs-fuse-daemon       29G  4.0G   23G  15% /home/XXXXXX/.gvfs

**************************************************
Output of dmesg | tail after I plug in drive

[  214.777752] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  474.224166] wlan0: CTS protection enabled (BSSID=00:60:64:1c:5c:ec)
[  476.464861] wlan0: CTS protection disabled (BSSID=00:60:64:1c:5c:ec)
[ 1532.760945] usb 7-1: USB disconnect, address 2
[ 1858.437721] usb 7-2: USB disconnect, address 6
[ 1874.591930] usb 7-2: new high speed USB device using ehci_hcd and address 7
[ 1874.659148] usb 7-2: configuration #1 chosen from 1 choice
[ 1874.660035] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1874.660507] usb-storage: device found at 7
[ 1874.660513] usb-storage: waiting for device to settle before scanning
andrew@Andrews-Laptop:~$ dmesg|tail
[ 1877.411911] sd 8:0:0:0: [sdb] Write Protect is off
[ 1877.411919] sd 8:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 1877.411923] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1877.413285] sd 8:0:0:0: [sdb] 2930277168 512-byte hardware sectors (1500302 MB)
[ 1877.414031] sd 8:0:0:0: [sdb] Write Protect is off
[ 1877.414037] sd 8:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 1877.414042] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1877.414048]  sdb: sdb1
[ 1877.442244] sd 8:0:0:0: [sdb] Attached SCSI disk
[ 1877.442322] sd 8:0:0:0: Attached scsi generic sg2 type 0

---

### Post by taurus on 2009-04-09
```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

