---
title: "Can't mount /dev/md0 from LiveCD"
date: 2005-11-25
forum: General Help
---

### Post by pheitman on 2005-11-25
I'm still trying to debug some boot problems I'm having. One thing I've noticed that troubles me greatly is that I can't mount /dev/md0 if I boot with the LiveCD. I get the message that /dev/md0 is already mounted or /mnt/md0 is busy. But AFAIK neither is true - mount doesn't show /dev/md0 as being mounted and I can't umount it. /mnt/md0 was just created and I can remove it which seems to me indicates that it isn't busy.

Can anyone help me understand what is preventing me from mounting this md device? I really need to figure out how to fix filesystem problems from the LiveCD, even if those problems are on raid1 or lvm partitions. (I didn't mean to confuse things - md0 is not involved in lvm).

Thanks in advance,

Peter

---

### Post by aysiu on 2005-11-27
What is md0, anyway?
I don't know if I can help, but since no one else has answered, I may as well try. 

Boot from the live CD and open a terminal (Applications > Accessories > Terminal).

What's the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by linbetwin on 2005-11-27
I don't know what md0 is but the first time I installed gnomeradio I started it and it told me that I don't have permission to use /dev/radio, or that another application was using it. So I looked in the /dev folder "radio" was actually named "radio0".

I don't know if this will help, but you should check the /dev folder to see if md0 exists. Maybe is't called md1 or just md.

---

### Post by malang on 2005-11-27
Correct me if I'm wrong, but is'nt /dev/md0 software raid?

Martin

---

### Post by pheitman on 2005-11-27
I'm really sorry that I wasn't more clear. Yes, /dev/md0 is software raid. I've set up my system with /boot mirrored on two partitions - sda1 and sdb1 using RAID1. The new 'partition' that uses both sda1 and sdb1 is called md0. I've recently had problems with my system and I've been trying to re-run lilo. Unfortunately when I boot from the LiveCD for some reason I can't mount /dev/md0 and lilo can't write to it either. The installation automatically chose lilo for me (rather than grub) because the MBR is on the software raid. Lilo has special support for that (supposably). 

Anyway, I'm finding lots of odd problems when I boot from the LiveCD and am trying to manage my installed system. I figured I'd ask this forum about one of them and start at the beginning. 

Below is the output of the commands requested. Thanks for suggesting them. The output is interesting. Note that according to fdisk -l /dev/md0 does not have a valid partition table even though /dev/sda1 and /dev/sdb1 (the two mirrored partitions do). I can understand how higher-level abstractions may not have the same information as the lower level ones, but in this case it seems wrong. Also, if I try to do a mkfs.ext3 /dev/md0 the message I get back is "/dev/md0 is apparently in use by the system; will not make a filesystem here!". 
```

root@ubuntu:~# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          61      489951   fd  Linux raid autodetect
/dev/sda2              62         304     1951897+  82  Linux swap / Solaris
/dev/sda3             305       38913   310126792+  fd  Linux raid autodetect

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          61      489951   fd  Linux raid autodetect
/dev/sdb2              62         304     1951897+  82  Linux swap / Solaris
/dev/sdb3             305       38913   310126792+  fd  Linux raid autodetect

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/md0: 501 MB, 501612544 bytes
2 heads, 4 sectors/track, 122464 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 1998 MB, 1998651392 bytes
255 heads, 63 sectors/track, 242 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

    Device Boot      Start         End      Blocks   Id  System
/dev/md1p1               1         243     1951866   fd  Linux raid autodetect

Disk /dev/md2: 317.5 GB, 317569761280 bytes
2 heads, 4 sectors/track, 77531680 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md3: 300.0 GB, 300066340864 bytes
2 heads, 4 sectors/track, 73258384 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md3 doesn't contain a valid partition table

``` ```

root@ubuntu:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/casper-snapshot
                      2.0G  1.3G  672M  65% /
tmpfs                 507M  4.0K  507M   1% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
tmpfs                 507M   12K  507M   1% /tmp
tmpfs                  10M  2.9M  7.2M  29% /dev

``` ```

root@ubuntu:~# cat /etc/fstab
/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda2 swap swap defaults 0 0
/dev/sdb2 swap swap defaults 0 0
```

---

### Post by aysiu on 2005-11-27
Yeah, unfortunately, those commands help us diagnose what the problem is. I don't know how to fix it, though.

---

