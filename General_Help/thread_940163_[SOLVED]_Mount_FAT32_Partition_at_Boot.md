---
title: "[SOLVED] Mount FAT32 Partition at Boot"
date: 2008-10-06
forum: General Help
---

### Post by ProgenitorVirus on 2008-10-06
Well, pretty much just need to know how to mount a partition at boot (Contains all of my media/files non-operating system related).

One of you smart Ubuntites (That a word?) should be able to help me out on such a simple task!

Thanks in advanced!

---

### Post by drs305 on 2008-10-06
Post the results of the following, plus tell us the name of the mountpoint you want (such as /media/myfiles):
```

sudo blkid
sudo fdisk -l
cat /etc/fstab

```

---

### Post by ProgenitorVirus on 2008-10-06
sudo blkid
/dev/sda1: UUID="5E9CCC439CCC1803" TYPE="ntfs" 
/dev/sda2: UUID="48E4-25E1" TYPE="vfat" 
/dev/sda5: UUID="18f84cb5-ee3c-4aa1-9380-00813d75cffe" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="2aa0dea4-2068-4cc5-b3f7-12b9ec15aaaa" 

sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ed60ed5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19581   157284351    7  HPFS/NTFS
/dev/sda2           19582       41220   173815267+   c  W95 FAT32 (LBA)
/dev/sda3           41221       60801   157284382+   f  W95 Ext'd (LBA)
/dev/sda5           41221       60045   151211781   83  Linux
/dev/sda6           60046       60801     6072538+  82  Linux swap / Solaris

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=18f84cb5-ee3c-4aa1-9380-00813d75cffe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2aa0dea4-2068-4cc5-b3f7-12b9ec15aaaa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

And I want the whole disk to be mounted as a whole, not as a specific point.  On my system when I do a manual mount it is "/media/disk" only because I don't have a USB or Windows Partition mounted

---

### Post by drs305 on 2008-10-06
> **ProgenitorVirus said:**
> 
And I want the whole disk to be mounted as a whole, not as a specific point.  On my system when I do a manual mount it is "/media/disk" only because I don't have a USB or Windows Partition mounted

The disk, if it is one partition, will be mounted in one place, but you still have to designate a folder, or mountpoint, on which it is to be mounted. Traditionally it is a folder in /media; for example, your disk can be mounted and accessible through "/media/myfiles". The folder can be named anything, as long as it exists and is named in fstab. For the following, I will call it "myfiles". 


Make the mountpoints. I will call it **myfile.**. Change the name wherever you see it in bold to whatever you want.
```

sudo mkdir /media/**myfile** 

```

Change the ownership of the mountpoints to yourself and set permissions:
```

sudo chown -R *[COLOR="Red"]username:[/COLOR]* /media/**myfile**  
chmod -R 750 /media/**myfile**

```

Make a backup copy of fstab and open with text editor (example uses gedit):
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Replace the fstab contents with the following. 
```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=18f84cb5-ee3c-4aa1-9380-00813d75cffe / ext3 relatime,errors=remount-ro 0 1
# /dev/sda6
UUID=2aa0dea4-2068-4cc5-b3f7-12b9ec15aaaa none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
# dev/sda2
/dev/sda2  /media/**myfile** vfat users,uid=1000,umask=027,utf8 0 0

```

Mount the new drive:
```

sudo mount /dev/sda2

```

---

### Post by gpsmikey on 2008-10-06
You might want to read through a post I started on FAT32 a couple of days ago and check out the information I found on the utf8 characterset translation issues.  You might want to consider moving your stuff to a NTFS partition or something else - there are a number of issues that you don't expect !!
my thread --> [http://ubuntuforums.org/showthread.php?t=938444](http://ubuntuforums.org/showthread.php?t=938444)

mikey

---

### Post by ProgenitorVirus on 2008-10-07
Thanks for your patience and help!  I understand now; about you needing a file for the drive to mount on, I had it backwards in my mind :p

Again thanks!  You've helped me tonnes!

---

