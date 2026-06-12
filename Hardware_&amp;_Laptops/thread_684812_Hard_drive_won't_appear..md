---
title: "Hard drive won't appear."
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by iammrfrank on 2008-02-01
Hey, I have a 3 hard drives, 2 internal that i can view and edit and everything. I have 1 hard drive in a case that i use as an external usb. I can't find out if it's mounting it or not, i plug it in and nothing happens at all. I have installed everything on every forum for an external usb hard drive in ntfs format. But nothing works.

it IS viewable in Terminal when i us lsusb: here is what i've tried:

> frank@frank-desktop:~$ sudo mount
[sudo] password for frank:
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
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



> frank@frank-desktop:~$ lsusb
Bus 004 Device 003: ID 1415:2000  
Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

---

### Post by jan quark on 2008-02-02
please post the results

```
sudo fdisk -l
```

do you have read this
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)
[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by iammrfrank on 2008-02-02
the 80gb and the 20gb are inside. The 80 is Linux, Ubuntu. The 20gb is a backup.


> frank@frank-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ffb1ffa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9363    75208266   83  Linux
/dev/hda2            9364        9729     2939895    5  Extended
/dev/hda5            9364        9729     2939863+  82  Linux swap / Solaris

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb0fdb0f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2327    18691596   83  Linux
/dev/hdd2            2328        2434      859477+   5  Extended
/dev/hdd5            2328        2434      859446   82  Linux swap / Solaris


there you go buddy. please help...

---

