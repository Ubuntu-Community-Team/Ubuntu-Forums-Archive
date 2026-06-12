---
title: "Automounting hard drives on boot"
date: 2008-09-15
forum: General Help
---

### Post by metroidnemesis13 on 2008-09-15
How would I go about automounting a few hard drives and partitions on the boot?  I know I need to use the start up manager but I don't know what the code would be.  Also, if I were to get a virus in Ubuntu, would it somehow transfer over to my Windows partitions when I mounted it?  I've been told that...

Thanks much...

---

### Post by drs305 on 2008-09-15
Are these internal or external drives. Internal drives are normally mounted in fstab while external drives are 'supposed' to mount automatically. If you post the results of these commands we can give you entries for your fstab:

```

sudo blkid
sudo fdisk -l  # small L
cat /etc/fstab

```

Viruses are generally not a problem in linux, and having one transfer from linux to ubuntu would be extremely unlikely at this time.

---

### Post by bodhi.zazen on 2008-09-15
For your security needs : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

And mounting : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by metroidnemesis13 on 2008-09-15
montag@ubuntu:~$ sudo blkid
[sudo] password for montag: 
/dev/sda1: UUID="6232BC8C32BC6727" LABEL="Windows Vista Ultimate x86" TYPE="ntfs" 
/dev/sdb1: UUID="54A40939A4091EDC" TYPE="ntfs" 
/dev/sdb5: UUID="AC502BCF502B9F58" TYPE="ntfs" 
/dev/sdb6: UUID="fe85eac4-f565-4c15-8ca5-4fbb3136ed0f" TYPE="ext3" 
/dev/sdb7: TYPE="swap" UUID="a41903dd-1a5b-4077-9551-c653459ca596" 
montag@ubuntu:~$ fdisk -l # small L
montag@ubuntu:~$ sudo fdisk -l  # small L

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0af20af2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0afd0afd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24328   195414628+   7  HPFS/NTFS
/dev/sdb2           24329       36483    97635037+   f  W95 Ext'd (LBA)
/dev/sdb5           24329       31623    58595328    7  HPFS/NTFS
/dev/sdb6           31624       36278    37391256   83  Linux
/dev/sdb7           36279       36483     1646631   82  Linux swap / Solaris
montag@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=fe85eac4-f565-4c15-8ca5-4fbb3136ed0f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb7
UUID=a41903dd-1a5b-4077-9551-c653459ca596 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by drs305 on 2008-09-15
Backup fstab and open for editing (substitute for gedit if desired):

```

sudo cp /etc/fstab /etc/fstab.old
gksu gedit /etc/fstab

```

Add these lines:
```

UUID=6232BC8C32BC6727 /media/windows ntfs-3g uid=1000,gid=1000,umask=022 0 0 
UUID=54A40939A4091EDC /media/sdb1  ntfs-3g  uid=1000,gid=1000,umask=022 0 0
UUID=AC502BCF502B9F58 /media/sdb5  ntfs-3g  uid=1000,gid=1000,umask=022 0 0

```
Optional: 
For a more definitive permission scheme, substitute 'umask=022' with 'dmask=027,fmask=111'
You can substitute the UUIDs with '/dev/sda1', '/dev/sdb1', and '/dev/sdb5' respectively
gid=1000 would be your user group. Other group ids are available.
You can name the mountpoints (windows, sdb1, sdb5) anything you wish. Make the same change below if you do.

Make the mountpoints (change as desired), put your username in chown line:
```

sudo mkdir /media/windows /media/sdb1 /media/sdb5
sudo chown -R ***username:*** /media/windows /media/sdb1 /media/sdb5

```

Remount (disregard 'busy' messages):
```

sudo umount -a
sudo mount -a

```

Now go read bodhi.zazen's link on fstab to learn what you have done. ;-)

---

