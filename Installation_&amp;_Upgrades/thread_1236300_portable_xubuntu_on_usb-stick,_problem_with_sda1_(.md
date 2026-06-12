---
title: "portable xubuntu on usb-stick, problem with sda1 (stick&amp;xp-hd)"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by p.becks on 2009-08-10
Hello,

I have installed xubuntu on my usb-stick (size: 8 Gb , 4 gb casper-rw-file). When i boot from the stick everything works great EXCEPT that i have a problem with mounting my XP-harddisk (ntfs). 

"mount" gives the following response:
*****************************************
ubuntu@ubuntu:~/Desktop$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sdb1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdg1 on /media/TOSHIBA_USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
securityfs on /sys/kernel/security type securityfs (rw)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
/dev/sdg1 on /media/TOSHIBA_USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
nfsd on /proc/fs/nfsd type nfsd (rw)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sdg1 on /media/TOSHIBA_USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//NASHOME/openshare on /home/ubuntu/smb4k/NASHOME/openshare type cifs (rw,mand,nosuid,nodev,user=ubuntu)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//UBUNTU/ubuntu on /home/ubuntu/smb4k/UBUNTU/ubuntu type cifs (rw,mand)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//NAShome/openshare on /home/ubuntu/smb4k/NAShome/openshare type cifs (rw,mand)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr1 on /media/Password type iso9660 (ro,nosuid,nodev,uhelper=hal,utf8,uid=999)
/dev/sdg1 on /media/TOSHIBA_USB type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=999)
tmpfs on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=0755)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
***********************************

There's nothing mounted on /media/disk (?)

fdisk -l

*************************************
ubuntu@ubuntu:~/Desktop$ fdisk -l

Disk /dev/sdb: 8019 MB, 8019509248 bytes
251 heads, 44 sectors/track, 1418 cylinders
Units = cylinders of 11044 * 512 = 5654528 bytes
Disk identifier: 0x000906e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1419     7831551+   b  W95 FAT32

**********************************************************


I think that my pc mounts the stick on sda1 and the internal hd (xp) also on sda1 (?)


Some help please?

---

### Post by markbuntu on 2009-08-10
The hdd is sdb according to fdisk. Try mounting that.

---

### Post by p.becks on 2009-08-11
sdb1 = cdrom (which is the usb-stick actually)

---

### Post by randcoop on 2009-08-11
Run fdisk as root: ```
sudo fdisk -l
```

Your USB drive is sdb and it gets mounted as cdrom (so you can actually access the non-casper-rw section of the USB by looking at /cdrom).

Your hard drive remains at /dev/sda.  Running the sudo fdisk -l command will show you that drive's partitions. 

The alternative to the command line approach would be to run Gparted (partition editor in the System menu).  In the upper right of the window, it will show the device as sdb, but you'll be able to pull down that list and switch to sda.  Again, that will show you the partitions on your hard disk.

Either way, you should from there be able to figure out which partition to mount.  If not, come back here with the results.

---

