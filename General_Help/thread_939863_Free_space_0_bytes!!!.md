---
title: "Free space 0 bytes!!!???"
date: 2008-10-06
forum: General Help
---

### Post by armageddon08 on 2008-10-06
Nautilus is showing the free space on my HDD to be 0 bytes, while it should be around 6 gigs. Gparted is showing correct amount of free space.
Why is this happening? Please Help!

---

### Post by Titan8990 on 2008-10-06
Possibly because the way that it is partitioned and you have one full partition (or nautilus is just off). Post the output for:

sudo fdisk -l


and

sudo mount

---

### Post by prem1er on 2008-10-06
> **armageddon08 said:**
> Nautilus is showing the free space on my HDD to be 0 bytes, while it should be around 6 gigs. Gparted is showing correct amount of free space.
Why is this happening? Please Help!

What does this show?

```
df
```

---

### Post by armageddon08 on 2008-10-06
> **Titan8990 said:**
> Possibly because the way that it is partitioned and you have one full partition (or nautilus is just off). Post the output for:

sudo fdisk -l


and

sudo mount

```
sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e565f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1913    15361888+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1914        9729    62782020    5  Extended
/dev/sda5            1914        9544    61295976   83  Linux
/dev/sda6            9545        9729     1485981   82  Linux swap / Solaris

sudo mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sayak/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sayak)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=sayak)

```

> **prem1er said:**
> What does this show?

```
df
```
```
df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             60812740  55390984   2356960  96% /
varrun                  253636       308    253328   1% /var/run
varlock                 253636         0    253636   0% /var/lock
udev                    253636        52    253584   1% /dev
devshm                  253636        40    253596   1% /dev/shm
lrm                     253636     39760    213876  16% /lib/modules/2.6.24-19-generic/volatile
overflow                  1024      1024         0 100% /tmp
gvfs-fuse-daemon      60812740  55390984   2356960  96% /home/sayak/.gvfs
/dev/scd0               715898    715898         0 100% /media/cdrom0

```

---

### Post by Titan8990 on 2008-10-06
Well, you are showing a couple free gigs. However, I would call that drive as good as full.

---

### Post by drs305 on 2008-10-06
You may have hidden trash accumulating or have created some large files (e.g. log files) recently, although in the former gparted would treat trash just as an ordinary file and thus should not show a disparity in free space.

In any case, here is a link to a tutorial on finding and deleting trash scattered throughout your system. 
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

You can also check your system for any files that have grown abnormally large by running this command:
```
sudo find / -size +500M
```

Additionally, the disparity between the partition size and the sum of used+free space in various apps may be due to the system reserving 5% of the partition space for system operations such as journaling. If you really need to squeeze a bit more space out of a partition, you can change the amount reserved with the tune2fs command. See the man page for details.

---

### Post by prem1er on 2008-10-06
> **Titan8990 said:**
> Well, you are showing a couple free gigs. However, I would call that drive as good as full.

Agreed.  I have seen numerous posts about Nautilus reporting the wrong disc space when there is very little space left.  I'm not sure of the exact reasoning.  Time for a new drive!

---

### Post by armageddon08 on 2008-10-06
> **Titan8990 said:**
> Well, you are showing a couple free gigs. However, I would call that drive as good as full.

Those 2 gigs are because I deleted a folder costing the same. But it should still show more of 'em.

---

### Post by SteveyDevey on 2009-02-22
I'm having a similar problem, and it brings me to a question. I've got a little 4GB drive in this dell mini, so space is at quite a premium. 

Are varrun, tempfs, varlock, udev, and lrm -- listed below -- parts of the file system that have space reserved for them, taking a part of my total 3.3GB for /?

```
/dev/sda1             3.3G  3.1G   60M  99% /
tmpfs                 247M     0  247M   0% /lib/init/rw
varrun                247M  292K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M  2.7M  244M   2% /dev
tmpfs                 247M   12K  247M   1% /dev/shm
lrm                   247M  2.0M  245M   1% /lib/modules/2.6.27-12-generic/volatile
```

If so, I'd love to be able to shrink those, are just have them part of the normal filesystem instead if possible. Am I wrong?

---

