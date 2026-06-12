---
title: "SATA drive, what filesystem is it?"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by xmastree on 2006-02-23
I've reinstaleld everything on my new motherboard. Currently I have a 40GB hda, split 20/20 between XP(ntfs) and linux.
There's also one 80GB SATA drive, sda.
Before I installed breezy, I used gparted on my previous installation to make one FAT32 partition on sda, mounted it and can read and write to it.

Now, I can't get it to mount from fstab, but can do it manualy.

```
chris@xmastree:~$ sudo fdisk -l
/dev/sda1               1        9964    80035798+  83  Linux
```
but:
```
chris@xmastree:~$ mount
/dev/sda1 on /mnt/sata type vfat (rw)
```
gparted reckons it's FAT32, but fdisk says otherwise.

fstab entry:
```
/dev/sda1	/mnt/sata	vfat	umask="0000"	0	0
```
but if I try to mount it like that:
```
chris@xmastree:~$ sudo mount /dev/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error

```
but if I mount it like this:
```
chris@xmastree:~$ sudo mount /dev/sda1 /mnt/sata
```
It mounts as vfat.
```
chris@xmastree:~$ mount
/dev/sda1 on /mnt/sata type vfat (rw)

```
:-k

This is my first time to use a sata drive... :confused:

---

### Post by tokyovigilante on 2006-02-23
VFAT is equivalent to FAT, both FAT16 and FAT32.

The reason that your first mount attempt fails and your second succeeds is that your first is missing a mountpoint. The correct use of the command is:


sudo mount [-t <filesystemtype, ie VFAT>] /dev/yourdevicehere /your/mountpoint/here

---

### Post by taurus on 2006-02-23
Remove "" in your /etc/fstab for /dev/sda1!!!

/dev/sda1	/mnt/sata	vfat	umask="0000"	0	0

---

### Post by xmastree on 2006-02-23
I thought that, if it was listed in fstab then it looks there for the mount point etc.

Is there something wrong with the entry there?

Edit:
Thanks taurus, that did it.

But why does fdisk -l list it as linux not vfat :-k

---

### Post by cotcot on 2006-02-24
You can access ext2 from xp too. See [www.fs-driver.org](www.fs-driver.org).

---

### Post by xmastree on 2006-02-24
Well I eventually used my [ubd](http://www.ultimatebootcd.com) to partition and format it since gparted's version of FAT32 was unrecognisable in windows, and XP would only let me use ntfs.
But now, I have a different probem.

```
chris@xmastree:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             18492972   3197080  14356492  19% /
/dev/hda1             19454680   5716196  13738484  30% /mnt/windisk
/dev/sda1             80016224 -590295810358701074304  84593632 101% /mnt/sata
```
I have about 45GB on there, but nautilus thinks there's still 80.7GB available. :confused:

Edit: Never mind, it appears to have fixed itself now.

---

