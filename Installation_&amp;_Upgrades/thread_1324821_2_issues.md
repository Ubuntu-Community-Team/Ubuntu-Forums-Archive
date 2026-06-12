---
title: "2 issues"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by Viktorja on 2009-11-12
Okay. I recently re-installed ubuntu-eee on my asus eee 1000 netbook. It is 8.04 (Hardy).

I've noticed that since I've done the reinstall, I cannot use my flash drive.  When I plug it in, it says "invalid mount option when attempting to mount the volume" 

I looked in another thread where this same problem had been solved, however my outputs were different when I tried to emulate the steps, so I am posting the output of "mount" & "fdisk -l" respectively in case this helps anyone help me

mount:
> 
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sdb1 on /home type ext3 (rw,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)


fdisk -l
> 
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x294a294a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e7d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3924    31519498+  83  Linux

Disk /dev/sdc: 4025 MB, 4025810432 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         488     3919841    b  W95 FAT32


my flash drive is sdc1, just fyi.


Thank you in advance to anyone who can help me out.

Asus eeepc 1000 / 1.6 GHz.

:rolleyes:

---

### Post by Viktorja on 2009-11-13
I ended up finding the solution to this problem on the eee user forums.
I'll post it here in case anyone else comes across this problem:

> 
sudo gedit /etc/fstab

remove the line (probably at the bottom) that is for the cd drive.

save and close

reboot


link to eee user forum for this issue: [http://forum.eeeuser.com/viewtopic.php?pid=303240#p303240](http://forum.eeeuser.com/viewtopic.php?pid=303240#p303240)

:popcorn:

---

