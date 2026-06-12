---
title: "Difficulties retrieving files from a partition with corrupt filesystem"
date: 2008-07-14
forum: General Help
---

### Post by euchrid33 on 2008-07-14
While attempting to change the firmware on an iPod, I appear to have damaged my Hardy Heron install's filesystem, and stupidly enough I did not have a restore point set up.  I found myself unable to boot, with GRUB crashing out and refusing to load.

Luckily I had a copy of Ubuntu on a CD, so I loaded that up, partitioned the drive and installed a fresh copy.  I'm in that partition now, trying to mount the original partition so that I can retrieve my files.  If there's a better way to go about doing so, please let me know, as my top priority right now is getting my hands on those files.

Here's my problem - I can't mount it without specifying a filesystem, and the filesystem is corrupted and unrecognisable.  Gparted is identifying it as 'unknown'.  I've entered the instructions for that partition into fstab, trying every filesystem I know, but the mount command always returns the following:

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm at the extent of my knowledge here.  I really don't want to format that partition and lose all my data.  I'm really hoping that somebody can help me.  I probably haven't provided all the necessary information, so please feel free to ask for more specific info.

---

### Post by Vivaldi Gloria on 2008-07-14
Have you tried to fix it using fsck? 

There is also a program called testdisk which "checks and recovers lost partitions" but I have never used it so I cannot comment on it. Type

```
man testdisk
```

in a terminal to read about it.

---

### Post by euchrid33 on 2008-07-14
Fsck returns the following:

> 
Unable to resolve 'UUID=903108da-bd6b-41f7-bc8e-88bfeb8bc4a7'

Which isn't particularly helpful.  Still looking into Testdisk.

---

### Post by logos34 on 2008-07-14
What does

sudo vol_id /dev/sda1

show?

Or what about running a filesystem check w/ backup superblock option?

sudo fsck -b 8193 /dev/sda1

---

### Post by euchrid33 on 2008-07-14
sudo vol_id /dev/sda1

produces

> /dev/sda1: unknown volume type

and 'sudo fsck -b 8193 /dev/sda1' gives me

> fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

which is very odd.  I tried closing anything which could be accessing sda1, including Gparted, but nothing changed.

---

### Post by logos34 on 2008-07-14
post output of 

**sudo fdisk -l**

---

### Post by euchrid33 on 2008-07-14
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5453802

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14283     2313328+  82  Linux swap / Solaris
/dev/sda6           14284       14572     2321361   83  Linux
/dev/sda7           14573       14593      168651   82  Linux swap / Solaris

---

### Post by logos34 on 2008-07-14
well, sda1 isn't overlapping with any other partition.  

So, are you sure it's not already mounted somewhere else?

cat /etc/mtab> I can't mount it without specifying a filesystem, and the filesystem is corrupted and unrecognisable. Gparted is identifying it as 'unknown'. I've entered the instructions for that partition into fstab, trying every filesystem I know...

if you can't manually mount it with

sudo mkdir /media/ubuntu 

sudo mount -t ext3 -o ro -v /dev/sda1 /media/ubuntu

then it looks like you'll have to try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") as Vivaldi Gloria suggested, or Photorec.  Be careful and read the docs and [this page.]("http://www.users.bigpond.net.au/hermanzone/p21.html")

---

### Post by pooyaplus on 2008-07-19
Hi 
I have a similar problem and also started a new thread on the issue here: [http://ubuntuforums.org/showthread.php?t=863966]("http://ubuntuforums.org/showthread.php?t=863966"). None of the suggestions worked for me. Also tried to mount to /media/whatever and gave me the same message:
```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

