---
title: "[SOLVED] USB Music Player Can't  Copy To It"
date: 2008-11-28
forum: Hardware
---

### Post by Rodney9 on 2008-11-28
Hello, I have a usb Music player, it is formated fat32,  but I can not copy files or create folders. 

If I right click on the desktop icon and select properties it says under Permissions -    

" The Permissions of "RODNEY" could not be determined "

I did try ~$ sudo chown $USER:$USER /media/RODNEY
$ sudo chmod -R 750 /media/RODNEY

from the hints [http://ubuntuforums.org/showthread.php?t=982560](http://ubuntuforums.org/showthread.php?t=982560)

But still can not copy to it.

What is going on ?

Rodney.

---

### Post by TenPlus1 on 2008-11-28
Try formatting it to fat16...

---

### Post by prshah on 2008-11-28
> **Rodney9 said:**
> 
usb Music player, it is formated fat32,  but I can not copy files or create folders. 

I did try ~$ sudo chown $USER:$USER /media/RODNEY
$ sudo chmod -R 750 /media/RODNEY


How did you mount it? Did you mount it manually using "sudo"? Then only root user has access to it. To manually mount usb removable devices, use the command from the terminal (Applications-Accessories-Terminal)```
gnome-mount --device /dev/sdb1
``` This will automatically create the mount point (directory) and mount the disk with relevant permissions. Replace /dev/sdb1 with the actual device ID for your usb device. If you do not know this id, plug the device in, wait 10~15 seconds, then give the command from the terminal ```
sudo fdisk -l
```

Normally, you should not need to manually mount this device. Does it not mount automatically when you plug it in? (Look under "Places->Computer").

There is no point running chown / chmod commands on a fat32 filesystem; these commands are not applicable to a fat32 filesystem.

---

### Post by Rodney9 on 2008-11-28
If I boot Ubuntu with the player plugged in , I can copy to it.

If I just plug it in after boot time, it automatically mounts, but says it is read only when I try to copy.

---

### Post by Rodney9 on 2008-11-29
It is awfully strange though, today I plugged it in , it auto mounted and let me copy a folder to it, but when I tried a second file it said "Error opening file '/media/RODNEY/cabbiev2.cfg': Read-only file system"
I tried unmounted and unplugging then plugging back in , auto mount, but still would not let me copy.

When I use $ sudo chown -R $rodney. /media/RODNEY

I get many, many lines saying similar to this one -

chown: changing group of `/media/RODNEY': Read-only
file system

but does not fix my problem.

Am I correct in thinking this "Read-only file system" is my problem.

Rodney.
__________

---

### Post by vanadium on 2008-11-29
Before proceeding with anything else, you need to check the file system. In MS Windows, you would have used the venerable "chkdsk a: /f", in linux there is the dosfsck program that allows to check and repair fat volumes. Only continue troubleshooting after you have made sure that the file system is healthy.

---

### Post by Rodney9 on 2008-11-29
> **vanadium said:**
> Before proceeding with anything else, you need to check the file system. In MS Windows, you would have used the venerable "chkdsk a: /f", in linux there is the dosfsck program that allows to check and repair fat volumes. Only continue troubleshooting after you have made sure that the file system is healthy.

**dosfsck -a /dev/sdd2 **


Thank You , that got it working perfectly.

Rodney

---

