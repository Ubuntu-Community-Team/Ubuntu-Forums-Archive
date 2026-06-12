---
title: "I tried everything but nothing works???"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by mase4me on 2007-02-07
I read many forums and guides. I have a 80 gb hard drive with a partition for Ubuntu 7.04 and Windows XP pro but when i type sudo fdisk I get:

aina@aina-laptop:~$ sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            5975        9665    29647957+  83  Linux
/dev/sda2   *           1        5974    47986123+   7  HPFS/NTFS
/dev/sda3            9666        9729      514080   82  Linux swap / Solaris

Partition table entries are not in disk order
aina@aina-laptop:~$ mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: only root can do that

aina@aina-laptop:~$ mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists

aina@aina-laptop:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: special device /dev/hda1 does not exist

aina@aina-laptop:~$ sudo mount /dev/hda0 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: special device /dev/hda0 does not exist

aina@aina-laptop:~$ 


I just want to access the files saved that i use with windows like Knoppixz 5.1.1 did off the bat. Can anyone help me out..? thanks..):P

---

### Post by zekopeko on 2007-02-07
from the looks of it... you are trying to mount a non-existant drive.

windows is on /dev/sda2 and you are trying to mount /dev/hda1 or 0.

try 

sudo mount /dev/sda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222

don't forget to make windows folder in /media with 

sudo mkdir /media/windows

EDIT: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by mase4me on 2007-02-07
so type what first?

---

### Post by mase4me on 2007-02-07
I got this:


aina@aina-laptop:~$ 
aina@aina-laptop:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
aina@aina-laptop:~$ sudo mount /dev/sda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: /dev/sda2 already mounted or /media/windows/ busy
mount: according to mtab, /dev/sda2 is mounted on /media/sda2
aina@aina-laptop:~$ 
aina@aina-laptop:~$ 
aina@aina-laptop:~$

---

### Post by zekopeko on 2007-02-07
ok you already have /media/windows created from the looks of it.

if you want to mount it in /media/windows do

```
sudo umount /media/sda2

```
then

```
sudo mount /dev/sda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

this will mount it just for this session.
if you want to have it at every boot follow the guide in the link i gave you.
(from the link)
/etc/fstab file tells linux what drives to mount, where and how.

so do 

```
sudo cp /etc/fstab /etc/fstab_backup
```

then

```
gksudo gedit /etc/fstab
```

and add this to the end of the file

/dev/sda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222

that should work.

---

### Post by mase4me on 2007-02-07
aina@aina-laptop:~$ 
aina@aina-laptop:~$ sudo umount /media/sda2
Password:
aina@aina-laptop:~$ sudo mount /dev/sda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222
aina@aina-laptop:~$ 


i don't see a new hard drive anywhere after doing that

---

### Post by zekopeko on 2007-02-07
hmmm.... don't really know.

try going to /media/windows and see if it mounted (ie. can you see your win files)

---

