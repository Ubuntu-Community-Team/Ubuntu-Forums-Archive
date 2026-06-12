---
title: "Writing denied on removable HD"
date: 2005-12-04
forum: Hardware &amp; Laptops
---

### Post by Delp on 2005-12-04
Hello:

I have a problem with my removable HD, I always get an error message when I try to write in it.

I tried to change the permissions, but it is not possible because it says that it is a read only system.

```

delp@ubuntu:/media$ sudo chmod u+w "Mario stuff"
chmod: changing permissions of `Mario stuff': Read-only file system


```

Of course it is possible to write in it, in windows, and actually it used to be possible in ubuntu some days ago. Does anybody have a clue??

Thanks!!

---

### Post by doitashimashite on 2005-12-04
What type of filesystem is on the removable HD? (type "fdisk -l" to find out)
Did you mount it manually (if so, what command did you use?), or automatically (in which case I would like to see your /etc/fstab file).

---

### Post by Delp on 2005-12-04
Thank you for answering me:
Ok i forgot something important, the HD is conected to the computer trough usb, and I suposse it is automount since i just connect and the icon appears in the screen, anyway the information you ask me for:

```

delp@ubuntu:/media/Mario stuff$ fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2433    19543041    7  HPFS/NTFS

```

And my fstab file:

```

delp@ubuntu:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2     /media/windows vfat umask=000 0 0

```

---

### Post by aysiu on 2005-12-04
Try this:
```
sudo umount /dev/sda1
sudo mkdir /extra_drive
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` and add this line in: ```
/dev/sda1 /extra_drive ntfs nls=utf8,umask=0222  0  0
``` Save and then ```
sudo mount -a
```

---

### Post by doitashimashite on 2005-12-05
How about NTFS write support? Is it no longer experimental? Is it completely safe?
I read different stories about the safety of writing NTFS partitions in Linux.

---

### Post by frodon on 2005-12-05
NTFS support is really far to be safe for the moment, so if you want to use both windows and linux FAT32 is a good alternative, if you think that you will mainly use linux and sometimes windows i would advice you ext3 file system.
All you have to do is to choose what kind of user you want to be ;)

---

### Post by Delp on 2005-12-05
Well... it's not working, i have just the same problem, the permissons are

```

delp@ubuntu:/media$ ls -l
dr-xr-xr-x   1 root root  4096 2005-11-22 22:53 Mario_stuff

```

but i can't change them, because it is said that it is a Rean-only file system.

Any help would be apreciated, i need to work with this device :confused: 

Greetings.

---

