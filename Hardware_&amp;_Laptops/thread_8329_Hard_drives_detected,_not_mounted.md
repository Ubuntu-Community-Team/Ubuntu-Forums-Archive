---
title: "Hard drives detected, not mounted"
date: 2004-12-16
forum: Hardware &amp; Laptops
---

### Post by RastaMahata on 2004-12-16
Hello:
I have just finished installing ubuntu on an experimental HD. Everything was automatically installed, even my webcam works! ;)
Sadly enough, I have only one single complain. HD detection is everything but friendly.
I thought "why not plug in this 30 gb HD I have?", which is a fat32 disk full of music and images.
I turned the pc off, plugged it in as slave to my ubuntu disk (4 gb), turn the pc on, and well... nothing.
I went to device manager, and the hard drive was there, but that was it. I couldnt access the hard drive. I did try some commands I found, but all I could do was to look at the file names. When i right clicked on them, they dissappeared.
Is there a simple, graphical way to make the device manager or any other program mount the HD?

---

### Post by bluehige on 2004-12-16
i got the same problem as you, i don't succeed on mounting my other 2 hdd ( theyre not fat, but ext3 )
If u can log in as root ( i have this problem too, cannot login as root ), go on the terminal and type : 
```
mount /dev/hda
```  
/dev/hda is where you see your hard disk on device manager.

Hope that's help you

---

### Post by RastaMahata on 2004-12-16
cant login as root into gdm, and that didnt work :(

---

### Post by jcooper on 2004-12-16
Firstly, the root account is disabled in ubuntu. The idea is to use *sudo*  to perform super-user actions.

To mount your hard disk, you'll need to edit your /etc/fstab to enable linux to recognise it and mount it automagically. The best way to do this is to run gedit as the root user, hence giving you permissions to edit the file:
```
sudo gedit /etc/fstab
``` 
You'll need to add an entry (like the others) mounting your disk /dev/hdb to an appropriate mount point.

---

### Post by RastaMahata on 2004-12-16
[QUOTE=jcooper]Firstly, the root account is disabled in ubuntu. The idea is to use *sudo*  to perform super-user actions.

To mount your hard disk, you'll need to edit your /etc/fstab to enable linux to recognise it and mount it automagically. The best way to do this is to run gedit as the root user, hence giving you permissions to edit the file:
```
sudo gedit /etc/fstab
``` 
You'll need to add an entry (like the others) mounting your disk /dev/hdb to an appropriate mount point.[/QUOTE]
 but what if I take the disk out?
I mean, doesnt ubuntu have anything like autodetecting this? I thought that it was standard that an OS (linux, windows, mac) would autodetect new hard drives and "mount" them automatically, if not "automagically" :P
Is this planned for the next version or something? Or is there a way without having to edit text files (some kind of software or something).
Hal Device Manager correctly detects the hard drives, so why doesnt ubuntu/gnome?

---

### Post by RastaMahata on 2004-12-17
bump

---

### Post by varunus on 2004-12-19
Linux is a bit different than that...Linux will usually only automount things in your fstab.  The gnome-volume-manager aims to fix this, using the "pmount" command, but its not completely finished yet...and it still has problems with things not in /etc/fstab sometimes.

Personally, I like having the control over what gets mounted when...I don't always want my second partition mounted in Linux.  (It makes searching for files much slower...)

---

### Post by RastaMahata on 2005-01-05
[QUOTE=varunus]Linux is a bit different than that...Linux will usually only automount things in your fstab.  The gnome-volume-manager aims to fix this, using the "pmount" command, but its not completely finished yet...and it still has problems with things not in /etc/fstab sometimes.

Personally, I like having the control over what gets mounted when...I don't always want my second partition mounted in Linux.  (It makes searching for files much slower...)[/QUOTE]
 do you know if hoary autodetects hard drives?

---

### Post by RastaMahata on 2005-01-09
bump

---

### Post by fng on 2005-01-09
I dont know.
I looked briefly at [http://www.ubuntulinux.org/wiki/HoaryHedgehog](http://www.ubuntulinux.org/wiki/HoaryHedgehog) but didnt found anything.

Don't be affraid to use the terminal :) It's more powerfull then the GUI.

---

