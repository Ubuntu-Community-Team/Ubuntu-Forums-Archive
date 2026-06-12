---
title: "Nautilus not seeing cdrom as mounted"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by spyke01 on 2006-06-10
I just burned the dapper desktop cd from iso using k3b from inside dapper(i installed using the server cd), after k3b ejected my disc,  popped it back in and launched nautilus. When i double-clicked on my cdrw drive, i got the error saying it couldnt mount it because its alreaddy mounted. I then went to the trusty terminal and heres what i got:
> 
spyke01@phoenix:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/hda1 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=spyke01)
spyke01@phoenix:~$ cd /media/cdrom0
spyke01@phoenix:/media/cdrom0$ ls
autorun.inf  disctree  isolinux    pool      README.diskdefines  start.ini
bin          dists     md5sum.txt  preseed   start.bmp           ubuntu
casper       install   pics        programs  start.exe           ubuntu.ico

and heres the fstab file
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/windows	ntfs	nls=utf8,umask=0222 0    0
so, the drive is mouted, disc is good(it shows files and i just bought this spool last night, not sure why nautilus is thinking that its not mounted when it is. any ideas?

---

### Post by TSP on 2006-08-25
I have the same problem with a couple of dvds burned with k3b :(,the most weird thing is that this works perfect in windows!! but  really bad in ubuntu.

---

