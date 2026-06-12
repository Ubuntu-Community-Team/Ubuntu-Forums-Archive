---
title: "Read-only hard external hard drive"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by bertrand82 on 2006-10-20
Hi, 

I have been having troubles with my external LACIE USB hard drive for two days. Although it had been working perfectly up to now, for some reasons I cannot write/delete anything on it now, I always have the same error message "cannot .....: Read-only file system". 

A df returns:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             36859272   3155244  31831656  10% /
varrun                  517760       104    517656   1% /var/run
varlock                 517760         4    517756   1% /var/lock
udev                    517760       112    517648   1% /dev
devshm                  517760         0    517760   0% /dev/shm
lrm                     517760     18856    498904   4% /lib/modules/2.6.15-27-386/volatile
/dev/sda1             39052448  37467968   1584480  96% /media/LACIE

And a cat /etc/mtab returns:

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-386/volatile tmpfs rw 0 0
/dev/sda1 /media/LACIE vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

The filesystem is vfat and I have tried the hard drive on other computers (Linux and Windows) and it works perfectly. I use Ubuntu 6.06 LTS.

Do you have any clues?

Thank you vry much!

/Bertrand

---

