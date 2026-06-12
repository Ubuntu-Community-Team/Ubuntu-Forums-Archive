---
title: "[SOLVED] Why only root can write ntfs?"
date: 2008-08-09
forum: General Help
---

### Post by asphixmx on 2008-08-09
Hello everyone,
I have Ubuntu Hardy. I have a second internal hard disk with windows (sda1). I was happily reading/writing to the drive. One day, I couldn't write anymore. It is mounted, I can read but can't write. BUT root can write. If I make a "gksu nautilus" and the browse to my windows partition, I am able to write, create folders, etc. I tried to fix it with ntfs-config graphically, with no results. What could be wrong? 

I post a my fstab:

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=2694fafc-9357-4613-b6d4-d3395b3fac55 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=565759da-f3ce-4327-919d-b4f8c5965b7e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
none /proc/bus/usb usbfs devgid=127,devmode=664 0 0

I post "mount" in terminal:

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
none on /proc/bus/usb type usbfs (rw,devgid=127,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
gvfs-fuse-daemon on /home/asphix/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=asphix)
/dev/sdd1 on /media/CANON_DC type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdh1 on /media/BACKUP type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

I can boot windows, read, write. Everything is normal. I shut down windows properly too.
One thing a noticed, is that when I right-click on the internal harddisk (windows, sda1) and select PROPERTIES, in the tab VOLUME, it says in the file system: "ntfs (3.1)" ... I guess it should say "ntfs-3g (3.1)" as another usb harddisk I have. Could that be the problem?
I hope I gave all the details to try to solve my problem. I need to write to the sda1 as I usually did before... what could be wrong? 

Thanks a lot for the help.

---

### Post by lisati on 2008-08-09
Assuming that you have a tool such as NTFS-3G installed to help write to NTFS partitions, another possibility is that there is something going on that is better dealt with by running Windows and doing something like```
chkdsk /f
```

---

### Post by asphixmx on 2008-08-11
Thanks for your help... I don't know what happened, suddenly, it worked again. I was just using the windows a few minutes... then the linux is ok now. Strange! I didn't do anything unusual ... the fact is that it's working now.

---

