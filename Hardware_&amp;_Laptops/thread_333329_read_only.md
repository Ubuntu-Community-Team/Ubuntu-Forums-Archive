---
title: "read only"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by kaiwan on 2007-01-07
Every external haard drive or usb memory stick is read-only, so I cant paste anything on it....how can I fix it?

thanks

---

### Post by teaker1s on 2007-01-07
sounds like it's mounting read only try looking at 
[http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/")

explains mounting partitions read/write

---

### Post by kaiwan on 2007-01-07
ok, but I cant find anything for external drives. Have found something for booting NFTS and allowing read and write but it is in beta and advised not to install ....

---

### Post by Koybe on 2007-01-07
Try to instal usbmount and/or gnome-volume-manager if it's not.

---

### Post by kaiwan on 2007-01-07
ok, I have installed usbmount...and what now? :)

---

### Post by teaker1s on 2007-01-07
in gome right click on panel and Add to panel 
select disk mounter

secondly using fdisk we can see what your drive is called
use this command for manual
[COLOR="Red"]man fdisk[/COLOR]

if you plug in usb drive and
[COLOR="Red"]fdisk -l[/COLOR]

you should see usb disc like mine below

daniel@daniel-laptop:~$ fdisk -l

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32


**sdb is the serial usb disk**

---

### Post by Koybe on 2007-01-07
How is it going now when you plug a new device?

Could you post the result of 'mount' once you've plugged your external usb storage?

---

### Post by kaiwan on 2007-01-07
these are my mount results

/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/Portable type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)


When I plug in it mount and shows on desktop...

---

### Post by Koybe on 2007-01-07
> **kaiwan said:**
> When I plug in it mount and shows on desktop...
And it's still read only?? It seems not.

---

### Post by kaiwan on 2007-01-07
> **teaker1s said:**
> in gome right click on panel and Add to panel 
select disk mounter

secondly using fdisk we can see what your drive is called
use this command for manual
[COLOR="Red"]man fdisk[/COLOR]

if you plug in usb drive and
[COLOR="Red"]fdisk -l[/COLOR]

you should see usb disc like mine below

daniel@daniel-laptop:~$ fdisk -l

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32

**sdb is the serial usb disk**


This is what I get from fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    7  HPFS/NTFS


what now?



I

---

### Post by kaiwan on 2007-01-07
> **Koybe said:**
> And it's still read only?? It seems not.

yes it is..cause I cant paste anything to it... ??

---

### Post by Koybe on 2007-01-07
/dev/sda is your device. And /dev/sda1 the mounted partition of your device.

Hum an what's the result of 
```
id
``` ?

---

### Post by kaiwan on 2007-01-07
> **Koybe said:**
> /dev/sda is your device. And /dev/sda1 the mounted partition of your device.

Hum an what's the result of 
```
id
``` ?

uid=1000(miroslav) gid=1000(miroslav) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(miroslav)

---

### Post by kaiwan on 2007-01-07
> **Koybe said:**
> /dev/sda is your device. And /dev/sda1 the mounted partition of your device.

Hum an what's the result of 
```
id
``` ?

uid=1000(miroslav) gid=1000(miroslav) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(miroslav)

---

### Post by Koybe on 2007-01-07
OK I see. the problem is your external disk is a ntfs disk. There is no support for ntfs write by default (because it is quite new, not fully supported and not in the kernel). If you want to use write on a ntfs device you need to use ntfs-3g.

You'll find a tutorial and get help on this thread : [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

Keep in mind that ntfs support in linux is still experimental even if it's really better then it was a few time ago. ;)

Good luck.

---

### Post by kaiwan on 2007-01-07
aha...so if I format my drive as FAT it will be read-write automatically or have to do something even then?

thanks

---

### Post by Koybe on 2007-01-07
Yes, FAT will do the trick more easily if you can format it at the moment.

---

### Post by kaiwan on 2007-01-07
and what  is the wort that can happen is I try with this experimantal?

---

### Post by Koybe on 2007-01-07
Look at the bottom of the first post in the thread i gave you. And/or ask there... I never used it personnaly.

---

