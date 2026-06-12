---
title: "cannot mount second internal harddisk"
date: 2008-05-04
forum: Hardware
---

### Post by Ampi on 2008-05-04
I have a second internal harddisk formatted as ext3. 

The problem is that it doesn't get recognized, even as a root. 
But when I open a program, for example Gimp and try to open a file, this disk turns up as a 38.9 Volume. 
When I try to click it, it says that it is not mountable.

How can I change this if the disk doesn't even appear to really 'exist' ??

---

### Post by Blednik on 2008-05-04
Can you mount it manually in terminal?
sudo mount -t ext3 /dev/sdb1 /mnt/disk

What does the output of "mount" say?

---

### Post by Ampi on 2008-05-04
Well, that is sort of the problem, even in my terminal the /media/disk or whatever it's name should be, doesn't exist. Even as a root....

---

### Post by Blednik on 2008-05-04
No no, you have to create that folder :)
Run a terminal and type these commands:

**cd /mnt**
**sudo mkdir disk** - Here you will be asked for your password. Enter it.
**sudo mount -t ext3 /dev/sdb1 /mnt/disk**

If this works then your disk should be mounted in /mnt/disk and you can then easily access it via Gnome.

EDIT: Okay I never really asked what type of disk you are using. Are you using an IDE or sata disk?
IDE disks are usually represented as /dev/hda, /dev/hdb while sata/scsi ones are /dev/sda, /dev/sdb, etc. Remember that /dev/sdb is your disk while /dev/sdb1 is a partition on the disk.

---

### Post by Ampi on 2008-05-04
I think it's a SATA :)

Is it possible to choose my mount point on /media because that's where my external harddisk shows up so I have them together or is that not done?

This might work... (excited!)

EDIT 1
No I think my external one is SATA this one probably isn't because all I have is hd...instead of sd...

EDIT 2
Hmm, it's not my hda, although it should be because hdb is my ubuntu...

```

mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by Ampi on 2008-05-04
```
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d34c0

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4998    40146403+  83  Linux

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098445

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4773    38339091   83  Linux
/dev/hdb2            4774        4866      747022+   5  Extended
/dev/hdb5            4774        4866      746991   82  Linux swap / Solaris
```

---

### Post by Blednik on 2008-05-04
Ugh, I'm not too sure about how the automount works. You could theoretically mount the disk anywhere you like, but I was more curious to see whether the disk can be mounted and read from.

What is the output of the "**mount**" command in your terminal?

---

### Post by Ampi on 2008-05-04
So I did it on /mnt/disk_int2 but when I try to mount /dev/hda my mount output is the output I have in post #5...

```
$ dmesg|tail
[ 6426.542133] VFS: Can't find an ext2 filesystem on dev hda.
[ 6437.825505] VFS: Can't find ext3 filesystem on dev hda.

```

---

### Post by Moop on 2008-05-04
> **Ampi said:**
> So I did it on /mnt/disk_int2 but when I try to mount /dev/hda my mount output is the output I have in post #5...

```
$ dmesg|tail
[ 6426.542133] VFS: Can't find an ext2 filesystem on dev hda.
[ 6437.825505] VFS: Can't find ext3 filesystem on dev hda.

```

You wouldn't use /dev/hda to mount it would be /dev/hda1. Here is a good tutorial on mounting a linux partition. [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Blednik on 2008-05-04
> **Ampi said:**
> So I did it on /mnt/disk_int2 but when I try to mount /dev/hda my mount output is the output I have in post #5...I don't mean the output of "**mount -t ext3 /dev/hda1 /mnt/disk**" whatever. Just "**mount**" without any parameters. Also, you were trying to mount a disk. Normally you'd want to mount a partition on a disk, not a disk.

/dev/hda => Disk
/dev/hda1 => Partition on that disk

The prototype of mount is: mount -t [filesystem] [something] [somewhere]
To mount the partition you'd use **sudo mount -t ext3 /dev/hda1 /mnt/disk**.
This means you're mounting the partition /dev/hda1 of type ext3 to /mnt/disk.

---

### Post by Ampi on 2008-05-21
Sorry, I have had a delay as you can see :)

Anyway, here is the output for the 'real' mount:

```
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
```

And I tried to mount again using hda1, but now it says that the device hda1 doesn't exist, which makes me doubt again. Though I am pretty sure that hda1 is the partition on the other disk.

```
$ sudo mount -t ext3 /dev/hda1 /mnt/disk_int2/
mount: special device /dev/hda1 does not exist
```

---

