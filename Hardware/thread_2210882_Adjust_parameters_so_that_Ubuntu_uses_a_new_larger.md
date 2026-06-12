---
title: "Adjust parameters so that Ubuntu uses a new larger SSD?"
date: 2014-03-13
forum: Hardware
---

### Post by volkerbradley on 2014-03-13
Just installed a 960GB SSD.  Previously had a 160GB SSD.  After installing the new hard drive I restored Ubuntu 13.10 with a Conezilla image using the instructions at [http://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/advanced/09-advanced-param.php](http://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/advanced/09-advanced-param.php).  I used option "-k1" to create the partition table proportionally in the target disk and turned on option "-r" to resize the file file system in the partition automatically. This is useful to make use all of the target disk size.
My entire hard drive is encrypted.
sudo fdisk -l | grep Disk
Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
Disk /dev/sda: 960.2 GB, 960197124096 bytes
Disk identifier: 0x0001ee87
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
Disk identifier: 0x24c3710e
Disk /dev/mapper/sda5_crypt: 958.6 GB, 958638637056 bytes
Disk identifier: 0x00000000
Disk /dev/mapper/ubuntu--vg-root: 151.2 GB, 151200464896 bytes
Disk identifier: 0x00000000
Disk /dev/mapper/ubuntu--vg-swap_1: 8577 MB, 8577351680 bytes
Disk identifier: 0x00000000
However, Nautilus displays that I only have 5.7 GB of free space as I had on the smaller SSD.
How can I make Ubuntu use the entire hard drive?

---

### Post by ajgreeny on 2014-03-13
What does sudo parted -l tell you about the partition on this new SSD?

I have never used clonezilla but I suspect that the restored filesystem, (or is it partition?) is still the same size as the original and I am afraid I don't know how to enlarge it to the new size you want, unless it can not be done simply with gparted.

---

### Post by volkerbradley on 2014-03-13
sudo parted -l
Model: ATA Crucial_CT960M50 (scsi)
Disk /dev/sda: 960GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  1530MB  1529MB  primary   ext2         boot
 2      1530MB  960GB   959GB   extended
 5      1530MB  960GB   959GB   logical


Model: ATA Seagate FreeAgen (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8577MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  8577MB  8577MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 151GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  151GB  151GB  ext4


Error: /dev/mapper/sda5_crypt: unrecognised disk label
I have included a screenshot of Nautilus[IMG]https://dl.dropboxusercontent.com/u/5383640/nautilus.png[/IMG]

---

### Post by volkerbradley on 2014-03-13
garted result:
[IMG]https://dl.dropboxusercontent.com/u/5383640/gparted.png[/IMG]

---

### Post by volkerbradley on 2014-03-15
Just was able to fix this by following the directions at [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

