---
title: "Mounting another hard drive"
date: 2009-03-17
forum: Hardware
---

### Post by little cazy on 2009-03-17
i jst installed an other hard drive, and i'm trying to remimber the program i used to mount new hard drives,  but i can't seem to remember(i used to play with linux alot but i forgot most of it.)

---

### Post by taurus on 2009-03-17
What filesystem is that new harddrive?  You just need to add an entry in /etc/fstab to have it mount automatically each time you boot.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by little cazy on 2009-03-17
```
root@Zola:~# sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00058b24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59323   476511966   83  Linux
/dev/sda2           59324       60801    11872035    5  Extended
/dev/sda5           59324       60801    11872003+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc302c302

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9553    76734441   83  Linux
/dev/sdb2            9554        9964     3301357+   5  Extended
/dev/sdb5            9554        9964     3301326   82  Linux swap / Solaris
root@Zola:~# sudo blkid
/dev/sda1: UUID="c7a0122e-e4e3-4cd2-9a53-ea0b398321e3" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="98475daf-4115-4c07-9f33-0c578d4b2cff" 
/dev/sdb1: UUID="3e82d6a1-3bea-46a7-a3f3-97d7adee0d7d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="455da4f3-7e0d-43c4-b481-ab7d13b1bbe2" TYPE="swap" 
root@Zola:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c7a0122e-e4e3-4cd2-9a53-ea0b398321e3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=98475daf-4115-4c07-9f33-0c578d4b2cff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
root@Zola:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             448G   29G  396G   7% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  208K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G  848K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-11-generic/volatile
```
here you go, btw, the 500gb is sata and the one i'm trying to bring in is ate or eta or however you spell it and it looks like it isn' even loading it, fun.

---

### Post by taurus on 2009-03-17
Did you by any chance install Linux on the second harddrive, /dev/sdb1 (82GB)?  

If you want to mount it, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```
Save it and exit gedit editing window.  Now, create that new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

---

### Post by little cazy on 2009-03-17
ty, that worked like i wanted it to.

---

### Post by stchman on 2009-03-17
> **little cazy said:**
> i jst installed an other hard drive, and i'm trying to remimber the program i used to mount new hard drives,  but i can't seem to remember(i used to play with linux alot but i forgot most of it.)

If the drive is formatted in FAT/FAT32/NTFS/EXT2,3 then it will appear in Places.  Clicking on it will mount.

If you want to mount it everytime at bootup then you will need to edit your fstab.

I have a tutorial to help.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

