---
title: "Help mounting an External hard drive."
date: 2008-07-08
forum: Hardware
---

### Post by hellzkeeper1216 on 2008-07-08
I have a toshiba 100gb external harddrive. and i have been trying to extract the photos from it. i tried to mount it and force mount it but i can't seem to do it.

I used the lsusb command

Bus 002 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0930:a000 Toshiba Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
jon@jon-laptop:~$ 

jon@jon-laptop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30ad509f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23568   189309928+  83  Linux
/dev/sda2           23569       24321     6048472+   5  Extended
/dev/sda5           23569       24321     6048441   82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
jon@jon-laptop:~$ 


jon@jon-laptop:~$ tail -F /var/log/messages
Jul  8 18:25:23 jon-laptop kernel: [  309.880849] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
Jul  8 18:25:23 jon-laptop kernel: [  309.892934] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
Jul  8 18:25:23 jon-laptop kernel: [  309.892943] Info fld=0x0
Jul  8 18:25:23 jon-laptop kernel: [  309.892945] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
Jul  8 18:25:23 jon-laptop kernel: [  309.905291] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
Jul  8 18:25:23 jon-laptop kernel: [  309.905299] Info fld=0x0
Jul  8 18:25:23 jon-laptop kernel: [  309.905302] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
Jul  8 18:25:23 jon-laptop kernel: [  309.917381] sd 3:0:0:0: [sdb] Sense Key : No Sense [current] 
Jul  8 18:25:23 jon-laptop kernel: [  309.917390] Info fld=0x0
Jul  8 18:25:23 jon-laptop kernel: [  309.917393] sd 3:0:0:0: [sdb] Add. Sense: No additional sense information
jon@jon-laptop:~$ sudo mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jon)
jon@jon-laptop:~$ 

jon@jon-laptop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
jon@jon-laptop:~$ 


Any help would be great.

---

### Post by boltronics on 2008-09-16
The fdisk output is indicating that there is no partition table on the device. If this is true (and the device is not damaged), the filesystem was formatted directly.

Try without specifying a partition. ie.
$ sudo mount -t ntfs-3g /dev/sdb /media/hd-ntfs

---

### Post by pqrs541 on 2008-09-16
You just might be a Red Neck if You've ever used lard in bed. Your home has more miles on it than your car.[world of warcraft](http://www.mmoinn.com)There is a stuffed possum anywhere in your house.[cheap wow gold](http://www.mmoinn.com)[wow gold](http://www.mmoinn.com)[wow power leveling](http://www.mmoinn.com) [power leveling](http://www.mmoinn.com)

---

### Post by linyanam on 2008-11-12
This helped me with No sense issue.
check the bug report and comment.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789/comments/46](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789/comments/46)

---

