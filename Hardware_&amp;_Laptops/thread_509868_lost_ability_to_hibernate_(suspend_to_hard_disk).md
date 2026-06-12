---
title: "lost ability to hibernate (suspend to hard disk)"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by ibmthinkpad-t30-2366 on 2007-07-25
I have a computer as described in my screen name. It is a pentium 4-M and has 1G of ram. I did not know that one needs a swap partition as large as the amount of ram one is using in order to suspend to hard disk when I installed ubuntu so I made my swap too small (about 400M). On those occasions when I am using more than 400M the computer did hibernate an if I left it thinking it would hibernate, sometimes the battery would run down. So this was annoying. I researched on this forum here and found that one needs a swap partion as large as the amount of physical memory one is using to hibernate. So I juggled partions with fdisk and created a larger swap partion (1G). It is the same slice (/dev/hda2) as the orginal so I did not need to edit /etc/fstab and I formated it with mkswap: "mkswap /dev/hda2." Now when ubuntu boots the new swap partion is not mounted (despite being in /etc/fstab). If I format /dev/hda2 with mkswap and do swapon -a or swapon /dev/hda2 the swap partion mounts. But the system does not mout it automatically next boot and morover it forgets that it is formated. I have to do mkswap all over again. The kicker is that when I hibernate even after manually formating and mounting the swap partition, the computer appears to dump memory to disk well enough (an indicator light blinks) but it does not resume when powered back on. Hibernate worked perfectly before (except when I was using more than 400M of ram). The only thing I can think of is that the page size of the swap partion is wrong. Is that it? What is the correct page size?

output of commands:

greg@gregs-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
#/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0     1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda1       /media/sda1     vfat    defaults,utf8,user,umask=007,gid=46 0     1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /home/greg/flash.ddo /home/greg/vol vfat user,loop 0
greg@gregs-laptop:~$
greg@gregs-laptop:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-28-386/volatile tmpfs rw 0 0
/dev/hda5 /media/hda5 ntfs rw,nls=utf8,umask=007,gid=46 0 0
greg@gregs-laptop:~$
greg@gregs-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       60945    30716248+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/hda2           60946       62946     1008504   82  Linux swap / Solaris
/dev/hda4           86334      116280    15093067+   f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/hda5           86341      116280    15089728+   7  HPFS/NTFS
greg@gregs-laptop:~$
greg@gregs-laptop:~$ dmesg | grep swap
[17179599.096000] Unable to find swap-space signature
[17179602.748000] Unable to find swap-space signature

---

