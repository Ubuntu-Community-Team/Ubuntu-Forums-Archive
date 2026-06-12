---
title: "[SOLVED] Sdb1"
date: 2008-09-12
forum: General Help
---

### Post by kaber on 2008-09-12
Hi
 I have two hardrives both 80 gb setup as follows




Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8e2b8e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        2006     1461915   82  Linux swap / Solaris
/dev/sda3            2007        9729    62034997+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c3caf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1 

My problem is setting permission for me to access sdb1 without having to be root and also getting it to mount at bootup time

---

### Post by iaculallad on 2008-09-12
Open your terminal and try unmounting the sdb partition if it had been already mounted:

```
sudo umount /dev/sdb
```

Create a directory on your media folder:

```
sudo mkdir /media/SDB2
```

Next, open your fstab file for editing:

```
kdesu kedit /etc/fstab
```

and insert the lines of text below on the last part of the file (copy and paste it if possible):

```
/dev/sdb /media/SDB2     ntfs    defaults,umask=007,gid=46 0       1
```

Save and close the file. Still on the terminal, issue the command:

```
sudo mount -a
```

---

### Post by EmanresuusernamE on 2008-09-12
In your /etc/fstab file, edit your drive so that the options have these in them:
user,auto
Fourth group of text is the options.
/dev/sda3 /<mount point> <mount type> user,auto,<other options> <whatever's left>

---

### Post by kaber on 2008-09-13
Thanks for your quick reply,I must of stuffed up the last line of the fstab for the message I got was as follows

NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

This is how my fstab is now


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=535f4518-3747-4019-b8cf-b802ab05a61e / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda3
UUID=5c8a131c-d424-45c8-8e09-e02493feb49c /Data ext3 nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda2
UUID=b00c8599-44d1-46fd-817a-c303f20feeaf none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb /media/SDB2     ntfs    defaults,umask=007,gid=46 0       1

---

### Post by Too Late on 2008-09-13
> **kaber said:**
> /dev/sdb /media/SDB2     ntfs    defaults,umask=007,gid=46 0       1
/dev/sdb is a hard drive. /dev/sdb1 (or /dev/sdb2, /dev/sdb3 and so on) is a partition. You can't mount a hard drive, but you do can mount a partition. I don't know what's the correct partition number you would like to mount, because your first post somehow lacks the last words (?).

---

### Post by iaculallad on 2008-09-13
Could you post the complete output of the terminal command below:

```
sudo fdisk -l
```

---

### Post by kaber on 2008-09-13
This is my fstab




Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8e2b8e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        2006     1461915   82  Linux swap / Solaris
/dev/sda3            2007        9729    62034997+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c3caf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    b  W95 FAT32
keith@sampon:~$

---

