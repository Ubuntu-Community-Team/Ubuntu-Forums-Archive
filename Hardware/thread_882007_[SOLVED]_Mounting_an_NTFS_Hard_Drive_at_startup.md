---
title: "[SOLVED] Mounting an NTFS Hard Drive at startup"
date: 2008-08-06
forum: Hardware
---

### Post by garymce on 2008-08-06
Hello there

I've just recently switched from Windows XP to Ubuntu, and I have to say I'm enjoying it very much :) However I have two questions I'd like to ask relating to my hard drives.

I have a 40GB hard drive formated with ext3 which my Ubuntu installation is sitting in. However, I also have an 80GB hard drive formatted with NTFS that holds all of my music, pictures and movies along with old games and such. It mounts with no problem when I double click it in File Browser, but every time I log out and back in I need to remount it. 

Firstly, is it possible to automatically mount the drive as part of a login script or similar? All of my desktop wallpapers are contained on the NTFS drive and so when I log in I'm presented with a blank desktop. I know I could just copy the wallpapers to my main HDD but I'd like to keep everything in one place. Would mounting it at startup cause my wallpaper to persist over sessions?

Secondly, will the fact that the 80GB HDD uses NTFS cause any problems? Should I just back everything up and format it with ext3 or can I get away with being lazy? :D

Any help would be much appreciated.

Thanks for your time
-Gary

---

### Post by evets25 on 2008-08-06
You should be able to add it to fstab so that it automatically mounts it a boot. "fstab" is the configuration file for all your drives, and it determines what is mounted where and whatnot. It is found in /etc/fstab, and you can edit it with any old text editor, although you need to do it with sudo - so for instance, run this to edit fstab as root: 
```
gksu gedit /etc/fstab
```

Someone more unlazy than I (and more knowledgeable) can probably give you a more specific answer on how to make it automount, but that at least points you in the right direction. 

Oh, and you can find out more about fstab and the way it works by running "man fstab" in terminal. Have fun. If you need more help, just ask, I'm sure someone knows he answer to this. There might even be a how-to around here somewhere...

---

### Post by sisco311 on 2008-08-06
open a terminal and post the output from:
```
sudo fdisk -l
```
```
sudo blkid
```
```
mount
```and
```
cat /etc/fstab
```

---

### Post by evets25 on 2008-08-06
Also, I just found this thread on automounting NTFS drives on startup:
 
[http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)

Tada.

---

### Post by garymce on 2008-08-06
Ahh that thread looks to be just the thing I'm looking for :) I'll just follow that rather than flood this thread with the output of those four commands.

Thank you both for your answers, much appreciated.
-Gary

---

