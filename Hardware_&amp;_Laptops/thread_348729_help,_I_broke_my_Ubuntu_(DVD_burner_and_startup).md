---
title: "help, I broke my Ubuntu (DVD burner and startup)"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by akajonesy on 2007-01-29
I've been fooling around, trying to learn how linux and Ubuntu work (I'm new at this OS), and I think I messed something up.
I was following some instructions from the Official guide on how to gain access to NTFS partitions and I changed some settings (specifically in fstab), and since then I've had major issues with boot ups (they take a LOOOONG time. way more than it did beforehand) and my DVD player/burner doesn't show up, nor do the discs I try playing in it.
I changed everything back to what I think were original settings, but I was pretty tired during the original changes, and I may have missed something.
I have some large files (mostly pics of the kids that the wife will KILL me if I loose) that I can't delete, so I can't do a reinstall. (Can't burn the files to disc cause it's not registering the drive when I try to burn). 

Can anyone help?

---

### Post by Stemp on 2007-01-29
Show us your fstab file (**/etc/fstab**) and the result of **sudo fdisk -l**

---

### Post by akajonesy on 2007-01-29
sudo fdisk -l 
> Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/hdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2392    19213708+  83  Linux
/dev/hdb2            2393        2498      851445    5  Extended
/dev/hdb5            2393        2498      851413+  82  Linux swap / Solaris


etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=55dbb9b3-ed0a-43a2-93fd-9e5b5c757932 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=3ebf61e3-dba6-424b-a308-37c5f64ee69f none            swap    sw              0       0


---

### Post by Stemp on 2007-01-30
You have only 2 partitions in your fstab, the Linux / partition and the swap.
Nothing about your ntfs or you dvd disks.

. To add your ntfs :

create a mount point : **sudo mkdir /media/windows**
Add this line to your /etc/fstab :
```
/dev/hda1/     /media/windows/	  ntfs	ro,user,auto,gid=100,nls=utf8,umask=002	0	0
```

if it's working fine then we will look at the UUID of /dev/hda1 ;)

. to add you cdrom 

first look at the devices :

```
ls /dev/hd* -l
```

you will probably have a line like this :
```
brw-rw---- 1 root cdrom 22,  0 2007-01-30 11:41 /dev/hdc
```

Verify if /media/cdrom0 exist and add this line in your /etc/fstab :
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by akajonesy on 2007-01-30
ok... odd as odd is, it's now working. I did nothing yet. It just....works now. :confused: 
I went through the /etc/ directory to see what's what and i found a file called fstab~ and IT has the cd line in it...but I didn't create the file...

I'm so confused...

---

### Post by Stemp on 2007-01-30
Ir's working, that's the most important thing ;)

---

### Post by akajonesy on 2007-01-30
Weird. The only thing I can think of that was different is that I shut down vs restarting. Do you think this would make a difference?

---

