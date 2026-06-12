---
title: "Windows HDD shown with its name but not acccessible..."
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by EL1984 on 2007-08-22
Well, I (finally) returned to linux. so I installed Kubunt 7.04,  did the dist-upgrade and else...

I have Kubuntu on my 2nd hdd an my 1t hdd (hda1) named Charly is my Windows HDD.

It's shown me in /dev/disk/by-label

its' neither mounted (cause I can't):

> mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab


and it's not into fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=decd8f06-50e4-446a-9b6b-748487b23188 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb6
UUID=b6ab62b4-13c3-4282-9bc5-702daa4530cf none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I tried to open it in Konqueror, but the rights are only for root I guess (so I'll have to change them too, but how?)

I also have an external hdd which is not shown at all, but my small 60gb usb is shown and mounted... don't ask how, it just is...

Thanks in forward, an sorry if I ask a stupid question, but I really want to work into it and I could just appreciate some help

Kind regards

Eric

---

### Post by merlinus on 2007-08-22
Post output of each of these:

```

sudo fdisk -l
blkid

```

-merlin

---

### Post by EL1984 on 2007-08-22
fdisk-l brings:
> root@PAT:~# fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       15234   122367073+  83  Linux
/dev/hdb2           29573       30515     7574647+   5  Extended
/dev/hdb3   *       15235       29572   115169985   83  Linux
/dev/hdb5           29950       30515     4546363+  82  Linux swap / Solaris
/dev/hdb6           29573       29949     3028189+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7295    58597056    c  W95 FAT32 (LBA)

Disk /dev/sdb: 100.0 GB, 100030242304 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11784    94654948+  83  Linux
/dev/sdb2           11785       12161     3028252+   5  Extended
/dev/sdb5           11785       12161     3028221   82  Linux swap / Solaris


and blkid brings us

> @PAT:~# blkid
/dev/hda1: TYPE="ntfs"
/dev/hdb1: UUID="69a79e91-5990-406a-9a82-8c0524634d0d" SEC_TYPE="ext2" TYPE="ext3"
/dev/hdb3: UUID="decd8f06-50e4-446a-9b6b-748487b23188" SEC_TYPE="ext2" TYPE="ext3"
/dev/hdb5: TYPE="swap" UUID="685b9f78-e8fa-4084-bc13-911201818368"
/dev/hdb6: UUID="b6ab62b4-13c3-4282-9bc5-702daa4530cf" TYPE="swap"
/dev/sda1: LABEL="60GB-USB" UUID="016F-3D6D" TYPE="vfat"
/dev/sdb5: TYPE="swap" UUID="42e19d9d-dc49-4d2a-807d-65cfdfb71d2d"

yep, there is another linux partition, I'll delete that one after I can access the win HDD

thanks in fwd

---

### Post by merlinus on 2007-08-22
From output of sudo fdisk -l, looks like you have four hdds, and two /swap partitions.

Is this so?

Also, have you installed the ntfs-3g driver?

-merlin

---

### Post by EL1984 on 2007-08-22
I have 2 IDE HDD's (one with XP on it, one with Linux (I guess even 2 linux distros on it) each one of them having a swap file
and an external 60gb usb

ntfs-3g driver? nope, didn0t even hear about it

---

### Post by taurus on 2007-08-22
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by EL1984 on 2007-08-22
well. I have to admit that the ntfs 3g stuff is acutally too high for my linux skill. So , Houston, we have a problem

---

### Post by taurus on 2007-08-22
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hda1
sudo mount -t ntfs-3g /dev/hda1 /media/hda1
df -h
```

---

### Post by merlinus on 2007-08-22
Open a terminal and enter:

```

sudo apt-get install ntfs-config

```

then:

```

sudo ntfs-config

```

Tick the appropriate boxes and restart.

-merlin

---

