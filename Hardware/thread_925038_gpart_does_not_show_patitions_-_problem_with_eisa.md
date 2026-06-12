---
title: "gpart does not show patitions - problem with eisa?"
date: 2008-09-20
forum: Hardware
---

### Post by swyddefrog on 2008-09-20
Hi,

I am currently trying to install Ubuntu 8.04.1 but when it comes to creating a partition I am struggling.

The partition tool Gpart does not show any partitions on my pc and yet I already have Vista installed on the harddrive. There is also an EISA partition on the machine.  How can I get Gpart to recognise the existing partitions?

It complains that it does not recognise the disklabel.  I just want it to ignore the EISA partition and the Vista partition, and install Ubuntu in the blank space that I have left on the drive for it.

Are there any other tools that I can use instead of gpart to recognise my existing partitions?

Hope you can help.

---

### Post by swyddefrog on 2008-09-20
Further to my previous post - to provide some more information...

Gparted shows that I have two disks /dev/sda and /dev/sdb
(in windows vista I only see one partion (that somehow spans across the two disks?)).

Using parted I get the following output:

ubuntu@ubuntu:/dev$  sudo parted
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) select /dev/sda
Using /dev/sda
(parted) print                                                            
Error: Can't have a partition outside the disk!                           
(parted) select /dev/sdb
Using /dev/sdb
(parted) print                                                            
Error: Unable to open /dev/sdb - unrecognised disk label.                 
(parted) select /dev/sda1                                       
Using /dev/sda1
(parted) print                                                            
Error: Unable to open /dev/sda1 - unrecognised disk label.                
(parted) select /dev/sda2
Using /dev/sda2
(parted) print
Error: Unable to open /dev/sda2 - unrecognised disk label.


Anyone got any suggestions on what path to follow next?

---

### Post by IntuitiveNipple on 2008-09-20
How many physical drives does the PC have?
```

ls -l /dev/disk/by-id

```
Can fdisk report the partition table(s)?
```

fdisk -lu /dev/sda

```
If that fails, capture the master boot record and attach a (compressed) copy here:
```

cd ~
dd if=/dev/sda bs=512 count=1 | gzip >sda-mbr.bin.gz

```
Attach sda-mbr.bin.gz

---

### Post by swyddefrog on 2008-09-21
Ok - ***ls -l /dev/disk/by-id*** first

ubuntu@ubuntu:~$ ls -l /dev/disk/by-id
total 0
lrwxrwxrwx 1 root root  9 2008-09-21 15:33 ata-FUJITSU_MHY2200BH_K41KT842T93P -> ../../sdb
lrwxrwxrwx 1 root root  9 2008-09-21 15:33 ata-FUJITSU_MHY2200BH_K41KT842T98F -> ../../sda
lrwxrwxrwx 1 root root 10 2008-09-21 15:33 ata-FUJITSU_MHY2200BH_K41KT842T98F-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-09-21 15:33 ata-FUJITSU_MHY2200BH_K41KT842T98F-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 2008-09-21 15:33 scsi-1ATA_FUJITSU_MHY2200BH_K41KT842T93P -> ../../sdb
lrwxrwxrwx 1 root root  9 2008-09-21 15:33 scsi-1ATA_FUJITSU_MHY2200BH_K41KT842T98F -> ../../sda
lrwxrwxrwx 1 root root 10 2008-09-21 15:33 scsi-1ATA_FUJITSU_MHY2200BH_K41KT842T98F-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-09-21 15:33 scsi-1ATA_FUJITSU_MHY2200BH_K41KT842T98F-part2 -> ../../sda2

Seems to show two disks and two partitions on the one disk?

ubuntu@ubuntu:~$ fdisk -lu /dev/sda
Cannot open /dev/sda
ubuntu@ubuntu:~$ fdisk -lu /dev/sdb
Cannot open /dev/sdb
ubuntu@ubuntu:~$ 

Also - have included the gz after running the command - sudo dd if=/dev/sda bs=512 count=1 | gzip >sda-mbr.bin.gz

Hope you can help.

---

### Post by IntuitiveNipple on 2008-09-23
Okay, my typing left something to be desired!

Try prefixing the fdisk commands with sudo. For example:
```

sudo fdisk -ul /dev/sda

```

That'll let us know what partition types are, which may be affecting things. I'll look at the MBR/partition table sector attachment here too.

---

### Post by swyddefrog on 2008-09-25
Ah ha - there is something on /dev/sda

ubuntu@ubuntu:~$ sudo fdisk -ul /dev/sda

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x66b71a79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    24645631    12321792   27  Unknown
/dev/sda2   *    24645632   699510775   337432572    7  HPFS/NTFS

I repeated the command on /dev/sdb

ubuntu@ubuntu:~$ sudo fdisk -ul /dev/sdb

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

