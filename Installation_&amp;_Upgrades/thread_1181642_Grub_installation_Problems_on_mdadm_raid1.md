---
title: "Grub installation Problems on mdadm raid1"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by kaefert66014235 on 2009-06-08
I want my Ubuntu 9.04 Server to contain only the two discs currently known to my system as sdb & sdc.

For beeing able to boot the system, I also have an older disc which partitions arn't used anymore but which contains a working grub that boots the system.

The partitions currently known as sdb1 & sdc1 are used for an mdadm raid1 (md0) which is mounted as /.

My aim is to beeing able to remove the old disc sda, so that the discs currently known as sdb & sdc are sda & sdb. Both of this discs should contain a grub bootloader that boots the system that resides on md0, which uses sdb & sdc (or sda & sdb in future)

My tries to install grub:
```
kaefert@Blechserver:~$ sudo grub-install /dev/md0 
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.
kaefert@Blechserver:~$
```

```
kaefert@Blechserver:~$ sudo grub-install /dev/sdb
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.
kaefert@Blechserver:~$
```

```
kaefert@Blechserver:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
grub> device (hd1) /dev/sdb
device (hd1) /dev/sdb
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
grub> 

```

And there is my /boot/grub directory which contains the "missing" stage1
```
kaefert@Blechserver:/boot/grub$ ls -ali
total 469
 4623 drwxr-xr-x 2 root root    608 2009-06-08 11:15 .
  252 drwxr-xr-x 3 root root    368 2009-05-14 18:46 ..
22691 -rw-r--r-- 1 root root    197 2009-06-08 11:15 default
26062 -rw-r--r-- 1 root root     30 2009-06-04 18:48 device.map
61726 -rw-r--r-- 1 root root     15 2009-06-02 22:25 device.map~
45676 -rw-r--r-- 1 root root     60 2009-06-02 21:45 device.map.bak
22541 -rw-r--r-- 1 root root   8288 2009-06-08 11:15 e2fs_stage1_5
22678 -rw-r--r-- 1 root root   7856 2009-06-08 11:15 fat_stage1_5
61728 -rw-r--r-- 1 root root     16 2009-06-02 22:25 installed-version
22682 -rw-r--r-- 1 root root   8712 2009-06-08 11:15 jfs_stage1_5
22698 -rw-r--r-- 1 root root   4296 2009-06-04 18:42 menu.lst
22705 -rw-r--r-- 1 root root   4302 2009-06-04 18:42 menu.lst~
22684 -rw-r--r-- 1 root root   7352 2009-06-08 11:15 minix_stage1_5
22686 -rw-r--r-- 1 root root   9756 2009-06-08 11:15 reiserfs_stage1_5
15167 -rw-r--r-- 1 root root    512 2009-06-08 11:15 stage1
 4902 -rw-r--r-- 1 root root    512 2009-06-04 19:05 stage1-bak
22539 -rw-r--r-- 1 root root 121740 2009-06-08 11:15 stage2
11995 -rw-r--r-- 1 root root 121740 2009-06-04 18:42 stage2-bak
45529 -rw-r--r-- 1 root root 121740 2009-05-14 18:30 stage2_eltorito
22688 -rw-r--r-- 1 root root   9556 2009-06-08 11:15 xfs_stage1_5
kaefert@Blechserver:/boot/grub$
```

My fstab:
```
kaefert@Blechserver:~$ more /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/md0 during installation
UUID=a3f64ea4-3d8e-451a-9210-bc7f70e108bb /               reiserfs notail,relatime 0       1
# /tmp was on /dev/sdb2 during installation
UUID=f4d63ed4-eaf8-43f4-b13d-d33902830991  /tmp  reiserfs  suid,dev,relatime,exec  0  0
# swap was on /dev/sda2 during installation
UUID=59de9e87-eba5-4ab0-a184-4761039bb41a  swap  swap  sw  0  0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/md1  /media/mirror320ide1  reiserfs  suid,dev,exec  0  0
/dev/sdd2  /media/elements  ntfs  suid,dev,exec,noauto  0  0
/dev/sdg1  /media/maxtor  ntfs  suid,dev,exec,noauto  0  0
kaefert@Blechserver:~$
```

Some of the GRUB guides and forum threads I found and read:
[http://wiki.ubuntuusers.de/GRUB](http://wiki.ubuntuusers.de/GRUB)
[http://wiki.clug.org.za/wiki/RAID-1_in_a_hurry_with_grub_and_mdadm](http://wiki.clug.org.za/wiki/RAID-1_in_a_hurry_with_grub_and_mdadm)
[http://www.linuxquestions.org/questions/linux-software-2/gentoo-grub-the-file-bootbootgrubstage1-not-read-correctly-275708/](http://www.linuxquestions.org/questions/linux-software-2/gentoo-grub-the-file-bootbootgrubstage1-not-read-correctly-275708/)

Please tell my how I should proceed to achieve my goals.

---

### Post by JDoska on 2009-06-08
I also have the same issue installing the gfxboot, GRUB is still working, but not the Graphic Part, I recieve the same Exact errors  **kaefert66014235** list here.

Any Solution will be posted here. I hope *by myself*

---

### Post by kaefert66014235 on 2009-06-09
When I remove the disc currently known as sda, then the GRUB installation from the other discs gives me the following error at boottime (and doesnt boot):

```
internal error: the second sector of Stage 2 is unknown.
```

---

### Post by kaefert66014235 on 2009-06-16
I wonder what I could do to solve this issue. maybe I should file a bug at launchpad. If anyone is reading this: could you tell me if you think this is a bug, or am I doing something wrong / trying to achieve things that can't be achieved?

---

### Post by ricmitch on 2009-07-19
.

---

