---
title: "File system corrupt? (grub error 16)"
date: 2010-05-31
forum: Hardware
---

### Post by nixi on 2010-05-31
Hello


My hard drive (WD Raptor 150GB) seems to have crashed. It contains a dual boot option for Ubuntu 10.04 and Archlinux (Chakra), but at Grub stage 1.5 it merely says Grub error 16 denoting a corrupt file system structure, or the like. The drive appears in BIOS, yet neither in GParted nor Testdisk. 

Any suggestions on what to do?

---

### Post by lordbux on 2010-05-31
Ok here is what you can do.

1)POP In live CD

2) Once up , unmount all the drives.

3)then run fsck
```
sudo fsck /dev/<DRIVE> -f 
```

REPLACE the <DRIVE> with the name of drive, ie: sda1, hda2 .or what ever it is.
[B][COLOR="Red"]
If that looks too confusing use this [/COLOR][/B]

```
sudo fsck -A -f
```
the 'A' option should be capital.

happy fsck, please post results.

---

### Post by nixi on 2010-05-31
Thanks

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdb -f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Read-only file system while trying to open /dev/sdb
Disk write-protected; use the -n option to do a read-only
check of the device.
```


```
ubuntu@ubuntu:~$ sudo fsck /dev/sdb -f -n
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Invalid argument while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

The partitions on sdb are (or were) ext4 and linux swaps. 

I am unfamiliar with this type of error... should I try e2fsck?


By the way...
```
ubuntu@ubuntu:~$ sudo fsck -A -f
fsck from util-linux-ng 2.17.2
```
does not seem to say much, yet there are two hard drives attached to the computer: sda (storage) and sdb (systems). Unlike sdb, sda is identified by fdisk, gparted, testdisk, and such tools. However fsck says:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda -f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

The only partition on sda is (or was) xfs. 

Now both disks seem to have invalid super-blocks.... What on earth is going on?

---

### Post by nixi on 2010-06-01
This time I run fsck on partitions (sdb1, sda1...). one strange thing is that the disks seem to have swapped mbr names (sda, sdb). 

```

ubuntu@ubuntu:~$ sudo fsck /dev/sdb1 -f
fsck from util-linux-ng 2.17.2
If you wish to check the consistency of an XFS filesystem or
repair a damaged filesystem, see xfs_check(8) and xfs_repair(8).
```

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1 -f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda2 -f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda3 -f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda4 -f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
...


I recall reading threads on problems with SATA and ATA disks and Ubuntu... My systemsdisk is SATA2, and my storagedisk is ATA. Could this be relevant?

---

### Post by lordbux on 2010-06-01
> **nixi said:**
> This time I run fsck on partitions (sdb1, sda1...). one strange thing is that the disks seem to have swapped mbr names (sda, sdb). 

```

ubuntu@ubuntu:~$ sudo fsck /dev/sdb1 -f
fsck from util-linux-ng 2.17.2
If you wish to check the consistency of an XFS filesystem or
repair a damaged filesystem, see xfs_check(8) and xfs_repair(8).
```

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1 -f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda2 -f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda3 -f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda4 -f
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
...


I recall reading threads on problems with SATA and ATA disks and Ubuntu... My systemsdisk is SATA2, and my storagedisk is ATA. Could this be relevant?



hmm the trouble looks bit confusing.
I will advice that you DISCONNECT a hard drive and check one at a time.

and if still have trouble 
please try out ```
sudo e2fsk -f <device>
```

at times fsck can act funny. , and i see you are using a EXT4 file system.
I really advice you not to use it, ext3 seems better for the time.

---

### Post by nixi on 2010-06-02
I disconnected the storage disk, and ran fsck on the systems disk, but the results seem the same. 

```
ubuntu@ubuntu:~$ sudo fsck -f /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Read-only file system while trying to open /dev/sda1
Disk write-protected; use the -n option to do a read-only
check of the device.
```
```
ubuntu@ubuntu:~$ sudo fsck -fn /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
```
```
ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Read-only file system while trying to open /dev/sda1
Disk write-protected; use the -n option to do a read-only
check of the device.
```
```
ubuntu@ubuntu:~$ sudo e2fsck -f -n /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
```
```
ubuntu@ubuntu:~$ sudo e2fsck -b 8193 /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Read-only file system while trying to open /dev/sda1
Disk write-protected; use the -n option to do a read-only
check of the device.
```


Ubuntu's Disk Utility seems to be able to identify the disk as /dev/sda, and offers options to Format Drive, or Create Partition. I hit Format Drive, but an error message says
> Error creating partition table: helper exited with exit code 1: cannot open /dev/sda: Read-only file system

The disk is 3 years old, 10.000 rpm, SATA2, and has had several Linux systems on it. Last year I installed a version of Archlinux called Chakra, with partitions for boot, home, system, and swap (home and system partitions ext4). A month ago I made a dual boot option by resizing Arch's home partition and installing Ubuntu 10.04 (default ext4). Both systems worked well... until a few days ago, when signing in to Ubuntu to see a black screen with error messages referring to /etc/init.d/rc, and /etc/rsGd/S90reboot input output error. 

Now the disk seems inaccessible, identified as having a "Read-only file system", or "zero-length partition". :(

---

