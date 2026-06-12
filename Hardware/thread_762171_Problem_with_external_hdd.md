---
title: "Problem with external hdd"
date: 2008-04-21
forum: Hardware
---

### Post by krelverehan on 2008-04-21
I am having a problem backing up my stuff on my external hdd. It is a 160GB wall powered external hdd. I have the FS set to ext3 and 512MB's in the swap. Now the problem lies when I try to put stuff on it, it seems to freeze half way through loading the hdd.

I formatted the hdd using gparted, and I even used the check feature in the program to see if I could find any errors, which i did not find any.

here is my [FONT="Courier New"][COLOR="RoyalBlue"]sudo fdisk -l[/COLOR][/FONT]

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aa409

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29692   238500958+  83  Linux
/dev/sda2           29693       30401     5695042+   5  Extended
/dev/sda5           29693       30401     5695011   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00022151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           19393       19457      522112+   5  Extended
/dev/sdb2               1       19392   155766208+  83  Linux
/dev/sdb5           19393       19457      522081   82  Linux swap / Solaris

Partition table entries are not in disk order

```

And [FONT="Courier New"][COLOR="RoyalBlue"]mount[/COLOR][/FONT]

```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/hda on /media/cdrom0 type udf (ro,nosuid,nodev,user=krel)
/dev/sdb2 on /media/disk type ext3 (rw,nosuid,nodev)

```

and finally [FONT="Courier New"][COLOR="RoyalBlue"]cat /etc/fstab[/COLOR][/FONT]

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=adea9757-8251-4374-a41c-b4b1dc58b660 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b08912c4-b9c5-417f-9cce-8b871e6a1d8a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

I am trying to back up my stuff before I upgrade to hardy... Any help would be greatly appreciated.

Thanks!

***Added note: It usually crashes when I have about 50GB's loaded, and it usually crashed nautilus too. So I have to reboot. Afterwards if I try to put more on the drive it tells me it is too full (which is untrue 50 < 160)***

---

### Post by Limpan on 2008-04-22
Is there any particular reason as to why you have the extended partion with swap on the external drive?
I'd try again but with only one partion. A primary partition with ext3 (or maybe JFS but that's probably only because it's a personal favourite).

---

### Post by krelverehan on 2008-04-22
I'll give that a try without a swap partition... I thought all file systems on linux needed a swap partition? I just set it up the same way my internal hard drive is set up.

And is there a specific package I need to install to use jfs?

---

### Post by Limpan on 2008-04-23
The swap partition is used by the OS in case the physical RAM runs out. Then it'll be able to move things to the swap partition and continue to run. You won't benefit from having swap on the external drive but you might get to use the swap partition on the internal drive.

You won't need to install anything to use JFS. It's all there from the start.

---

