---
title: "Hard Drives Mounted in both /mnt and /media"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by toddtemaat on 2007-09-02
Even though I mount my hard drives through fstab to be mounted in /mnt, once I am in Nautilus, they show up in bot /mnt and /media.  Why?  Any help to fix this would be appreciated.

Current fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

#boot
/dev/evms/boot	/boot		ext2	defaults,errors=remount-ro	0	1

#root
/dev/evms/ubuntu /		ext3	defaults 	0       1

#swap
/dev/evms/swap	none		swap	sw		0	0

#var
/dev/evms/var	/var		ext3	defaults	0	2

#CD-ROM
/dev/cdrom      /media/cdrom    udf,iso9660 	user,noauto	0       0

#Floppy
/dev/fd0	/media/floppy  	auto   		rw,user,noauto 	0       0

#NAS
/dev/evms/NAS		/mnt/NAS	ext3	rw,user,auto	0	1

#Backups
/dev/evms/Backups	/mnt/Backups	ext3	rw,user,auto	0	0

#home
/dev/evms/home		/home		ext3	defaults	0	1

Output of mount
> /dev/evms/ubuntu on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/evms/boot on /boot type ext2 (rw,errors=remount-ro)
/dev/evms/var on /var type ext3 (rw)
/dev/evms/NAS on /mnt/NAS type ext3 (rw,noexec,nosuid,nodev)
/dev/evms/Backups on /mnt/Backups type ext3 (rw,noexec,nosuid,nodev)
/dev/evms/home on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

Please let me know if there is anything else you might need.

Thanks,
Todd

---

### Post by kidders on 2007-09-04
Hi there,

> **toddtemaat said:**
> Even though I mount my hard drives through fstab to be mounted in /mnt, once I am in Nautilus, they show up in bot /mnt and /media.
Your post is a little confusing. The "mount" output you posted doesn't show *any* filesystems mounted in /media. :confused:

---

### Post by toddtemaat on 2007-09-04
I agree that it doesn't make sense...that's why I posted it here. ;)

---

### Post by kidders on 2007-09-04
If typing "mount" tells you no filesystems are mounted in /media, then there really is nothing mounted there. I know this is a weird thing to ask, but  are you sure you're not confusing the two directories somehow?

---

### Post by kerry_s on 2007-09-04
just delete the folders in media.

---

