---
title: "Installing Ubuntu 16.04 gpartd sees the drive but the installer doesn't"
date: 2017-02-11
forum: Hardware
---

### Post by jordanthompson on 2017-02-11
I am trying to install from a USB stick. 
I have been able to partition the SSD with gpartd 
The installer does not see the SSD

This is on a cheap Asus celeron computer I just  installed the SSD on.  I already had Ubuntu running on it with the original HDD. 

The SSD is a Kingston 120 GB drive that was working fine on another machine. 

Any suggestions?

---

### Post by oldfred on 2017-02-11
If gparted saw drive, then I assume BIOS sees drive correctly?

How was drive used in other system.
Things like RAID may leave meta-data on drive that interferes with many Linux tools.
Or Windows converting drive from basic to dynamic.

Post this:
sudo parted -l
sudo fdisk -lu

---

### Post by jordanthompson on 2017-02-12
You can see how I partitioned the drive with gparted.  Note that these results were while running the setup CD:

the parted command:
```
ubuntu@ubuntu:/tmp$ sudo parted -l
Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  110GB  110GB   primary  ext4
 2      110GB   120GB  10.5GB  primary  linux-swap(v1)


Model: Generic Mass-Storage (scsi)
Disk /dev/sdb: 3997MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  538MB   537MB   fat32              msftdata
 2      538MB   1050MB  512MB
 3      1050MB  3996MB  2946MB                     lvm


Error: /dev/mapper/ubuntu--vg-home: unrecognised disk label
Model: Linux device-mapper (linear) (dm)                                  
Disk /dev/mapper/ubuntu--vg-home: 1195MB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/mapper/ubuntu--vg-swap_1: unrecognised disk label
Model: Linux device-mapper (linear) (dm)                                  
Disk /dev/mapper/ubuntu--vg-swap_1: 101MB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/mapper/ubuntu--vg-root: unrecognised disk label
Model: Linux device-mapper (linear) (dm)                                  
Disk /dev/mapper/ubuntu--vg-root: 1598MB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: MATSHITA DVD-RAM UJ8E1 (scsi)                                      
Disk /dev/sr0: 1513MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1499MB  1501MB  2425kB               EFI


```
And the fdisk command:
```

ubuntu@ubuntu:/tmp$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1459982336 bytes, 2851528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7893f71c

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1            2048 213960703 213958656  102G 83 Linux
/dev/sda2       213960704 234440703  20480000  9.8G 82 Linux swap / Solaris


Disk /dev/mapper/ubuntu--vg-root: 1.5 GiB, 1598029824 bytes, 3121152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 96 MiB, 100663296 bytes, 196608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-home: 1.1 GiB, 1195376640 bytes, 2334720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdc: 3.7 GiB, 3997171712 bytes, 7806976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8808A399-9FF1-40F1-AEEE-B7D75643255B

Device       Start     End Sectors  Size Type
/dev/sdc1     2048 1050623 1048576  512M Microsoft basic data
/dev/sdc2  1050624 2050047  999424  488M Linux filesystem
/dev/sdc3  2050048 7804927 5754880  2.8G Linux LVM

```


And for grins:
```
ubuntu@ubuntu:/tmp$ lsblk
NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                     8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1                  8:1    0   102G  0 part 
&#9492;&#9472;sda2                  8:2    0   9.8G  0 part 
sdc                     8:32   1   3.7G  0 disk 
&#9500;&#9472;sdc1                  8:33   1   512M  0 part 
&#9500;&#9472;sdc2                  8:34   1   488M  0 part 
&#9492;&#9472;sdc3                  8:35   1   2.8G  0 part 
  &#9500;&#9472;ubuntu--vg-root   252:0    0   1.5G  0 lvm  
  &#9500;&#9472;ubuntu--vg-swap_1 252:1    0    96M  0 lvm  
  &#9492;&#9472;ubuntu--vg-home   252:2    0   1.1G  0 lvm  
sr0                    11:0    1   1.4G  0 rom  /cdrom
loop0                   7:0    0   1.4G  1 loop /rofs
```

---

### Post by jordanthompson on 2017-02-13
I was even able to format and mount the drive but I still cannot install to it!  I can write to it as well!

Any suggestions?

---

### Post by oldfred on 2017-02-13
I do not know LVM. Did you also use encryption?
LVM is an advanced logical volume management system. You have 3 standard partitions, the ESP for UEFI boot, the /boot which is normally outside the LVM as if LVM is encrypted the boot cannot be.
But standard partition tools like gparted only work on the physical partitions, not on the logical partitions inside the LVM like / & swap.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

---

### Post by jordanthompson on 2017-02-14
The drive is not encrypted.

I tried changing the drive type to IDE in the BIOS and repeated my steps...  Again I was able to create multiple partitions, format them etc.  I was able to create a swap partition also.

But when I tried to install Ubuntu, the installer did not see the SSD.

---

### Post by oldfred on 2017-02-14
It is better to have drive in AHCI. 
And with SSD it is required for trim to work. Old IDE does not fully support new drives.

---

### Post by jordanthompson on 2017-02-14
I just updated the bios. This time there was an option for csm in the bios (which I enabled.) I've been trying different combinations of secure boot, csm, ideal, uefi, etc. 
Fwiw, it seems that as I change drive settings, the installer changes also. Now it asking to select secure boot options... 

Still no joy..

---

### Post by jordanthompson on 2017-02-14
I just updated the bios. This time there was an option for csm in the bios (which I enabled.) 
Still no joy..  

I did try running install from a USB stick. This time, when I run gpartd I get this warning : The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.

The installer still does not see the disk.

---

### Post by oldfred on 2017-02-15
I have had a flash drive say 2048, but I reformatted and did a full install to it.
Others have had drives with the message, but do not know why.
I thought it was because they used Windows to format drive.

You can try using sgdisk like this:
[http://askubuntu.com/questions/781223/physical-block-size-is-2048-bytes-but-linux-says-it-is-512-when-formatting-a](http://askubuntu.com/questions/781223/physical-block-size-is-2048-bytes-but-linux-says-it-is-512-when-formatting-a)
Or maybe use dd to zero out the beginning of the drive.
[http://superuser.com/questions/1112147/gparted-physical-block-size-error](http://superuser.com/questions/1112147/gparted-physical-block-size-error)

---

### Post by jordanthompson on 2017-02-22
So for grins (and mounting frustration) I tried:
```
sudo dmraid -E -r /dev/sda
```
After an installation attempt that resulted in a crash of the installer that prevented gparted from running, I rebooted and was finally able install Ubuntu! &#128513;&#128513;
I guess the drive WAS part of a RAID at some point and I completely ignored the signs and had forgotten about it.

---

