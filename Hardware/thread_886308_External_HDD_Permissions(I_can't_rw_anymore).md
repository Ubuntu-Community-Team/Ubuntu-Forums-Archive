---
title: "External HDD Permissions(I can't rw anymore)"
date: 2008-08-11
forum: Hardware
---

### Post by jybeard on 2008-08-11
Hi have a Maxtor external HDD that I have just learned how to mount properly but can't write to it.  I had it connected previously but for some reason it got unmounted and I sent out a thread and remounted it.

-Before, when I first had it set up I could copy files to it.
-Now, I can't.; since remount the drive
-It is mounted as a vfat which I gather means I can't change permissions.

-How do I get back to the way it was when I could write to it?

> mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/scd2 on /media/U3 System Files type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/scd3 on /media/U3 System Files_ type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sdb1 on /media/external type vfat (rw)
/dev/sdd1 on /media/external type vfat (rw)
/dev/sdc1 on /media/maxtor type vfat (rw)

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ce28d3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38914   312571192+   b  W95 FAT32


Please help

---

### Post by libra1780 on 2008-08-24
on mount use "-o user,exec,rw,umask=000" as option in command line or change the opt's in /etc/fstab
the umask sets the permissions.. 000 means as on disk(all)

oh, and you have 2 disks mounted in the same folder
> /dev/sdb1 on /media/external type vfat (rw)
 /dev/sdd1 on /media/external type vfat (rw)

---

