---
title: "Installer won't detect hard-drive"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by Beesandhoneycombs on 2009-01-05
When I try to install Ubuntu on my ASUS EEEPC 701, The Hard-drive won't be detected. It is an 8GB Solid State Drive.

Here is what comes up:

[img]http://img211.imageshack.us/img211/725/screenshot1pe0.png[/img]

---

### Post by Beesandhoneycombs on 2009-01-10
bump

---

### Post by Beesandhoneycombs on 2009-01-19
please some-one help me :C

---

### Post by taurus on 2009-01-19
Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Beesandhoneycombs on 2009-01-19
in Windows or Ubuntu?

---

### Post by taurus on 2009-01-19
From Ubuntu LiveCD.  With the screenshot that you posted, see the Applications in the upper left corner?

---

### Post by Beesandhoneycombs on 2009-01-19
yessums

---

### Post by Beesandhoneycombs on 2009-01-19
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ 

Thats what i get

---

### Post by taurus on 2009-01-19
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That should be lower case letter L, not number one--1.

---

### Post by Beesandhoneycombs on 2009-01-19
Disk /dev/sda: 8061 MB, 8061419520 bytes
255 heads, 63 sectors/track, 980 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d305939

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         977     7847721    7  HPFS/NTFS
/dev/sda2             978         980       24097+  ef  EFI (FAT-12/16/32)
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 79.8 GB, 79824777216 bytes
26 heads, 50 sectors/track, 14991 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14992    77953628    b  W95 FAT32

Disk /dev/sdc: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders
Units = cylinders of 810 * 512 = 414720 bytes
Disk identifier: 0x0006e808

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          11       19166     7757824    b  W95 FAT32
ubuntu@ubuntu:~$ 

that is what i get now

---

### Post by taurus on 2009-01-19
> **Beesandhoneycombs said:**
> [B]Disk /dev/sda: 8061 MB, 8061419520 bytes
255 heads, 63 sectors/track, 980 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d305939

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         977     7847721    7  HPFS/NTFS
/dev/sda2             978         980       24097+  ef  EFI (FAT-12/16/32)
Note: sector size is 4096 (not 512)
[/B]


You want to install Ubuntu on your /dev/sda, wiping out whatever you have on that drive!  Make sure it is not mounted.

```
df -h
```

---

### Post by Beesandhoneycombs on 2009-01-19
Right, Ive gone and moved all the important files off of my hard-drive and put them on my ipod. How would I install it on the /dev/sda? It doesn't show up in the installer.

---

### Post by Beesandhoneycombs on 2009-01-19
I went to the partition edtior to demount it though it wont let me.

---

### Post by taurus on 2009-01-19
Are you going to paste the output of the second command in my previous post or are we doing a guessing game?

Otherwise, try something like

```
sudo umount /dev/sda1
sudo umount /dev/sda2
```
Now, run the installer again.

---

### Post by TiMBuS on 2010-04-30
Gunna bump this since I have this issue with ubuntu 10.04
I can't see any noteworthy errors in any logs, nothing seems abnormal. My hard drive just isn't listed in the installer.
Things tried so far: Changing disk order and sata modes in the bios, unplugging the other drives, making sure the disk is both detected and mountable in ubuntu (it is), checking ubiquity's output for errors (none, but logs show os-prober ignores the hard drive as well).

One clue I have is that the installer fails when I select 'install' at boot. No idea what the error is but it drops me to the desktop to apparently try to figure out what the problem is..

---

### Post by tshannon on 2010-04-30
Ditto, I'm getting the same.  Gparted finds my hard drives fine, but the ubuntu installer can only find /dev/sda, but I have two other drives /dev/sdb and /dev/sdc, which don't show up.

---

### Post by TiMBuS on 2010-04-30
The logs mention ubiquity using 'partman', so I fired that up, and yeah it can't see /dev/sdc either. This is probably the issue?
Still have no idea how to fix the issue though.

---

### Post by tshannon on 2010-04-30
Just found this post.  [http://ubuntuforums.org/showthread.php?t=1467386](http://ubuntuforums.org/showthread.php?t=1467386)

Fixed my problems. 

sudo apt-get remove dmraid

---

### Post by TiMBuS on 2010-04-30
Ah man can't believe I didn't see that when I searched.. Yep that fixed it. 
Thanks man.

---

