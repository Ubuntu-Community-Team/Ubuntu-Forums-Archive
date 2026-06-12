---
title: "&quot;mounting/unmounting flash drive"
date: 2009-02-08
forum: Hardware
---

### Post by conryf on 2009-02-08
Hello,
  I was getting the message "Cannot Mount Volume -- "You are not privleged..."

  I found a thread and it turned out I just needed to :

<code>sudo mount /dev/sdb1 /media/windows</code>

That's all well and good, but how do I get around this in the future. That is I"d like to mount automatically and unmount by just right clicking and choosing unmount. Is there a setting or a shortcut for this or something?

Thanks

---

### Post by Coldness on 2009-02-08
Well if I got you right, you want the drive to mount on startup and be able to unmount when right clicked?

If that's so, then do as follows:
First make a directory (folder) where you want the drive to be mounted. In your example it was "/media/windows". You make a folder by opening Terminal and typing:
```
sudo mkdir /media/windows
```.
Second, back up your fstab before editing it (you need to edit fstab if you wish to mount on start up), here's the code:
```
sudo cp /etc/fstab /etc/fstab.bak
```.
Now to editing the fstab:
```
sudo gedit /etc/fstab
``` (Replace "gedit" with "kate" if you're using KDE manager).
Next add this line to the fstab file: ```
/dev/sdb1 /media/windows ntfs defaults 0 0
```.
Now just type in, ```
sudo mount -a
```  to refresh the fstab.

As for the unmount script (that's what you want, right click function), I don't know how to do it. I'm not good with .sh scripts :( But hopefully, the other good members of this good forum will help you out ;)

PS: If you need to list your partitions, type : sudo fdisk -l

---

### Post by conryf on 2009-02-08
Hi Coldness,
   Thanks for the response. I went in and change my fstab entry, there was already one there, slightly different from yours, I changed it to your though "/etc/sdb1 /media/windows ntfs defaults 0 0"

  But when I tried to mount it, I got the error:

"NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?"

  I also just took it out and put it back in and got the same error about lack of priviledges however it still mounts fine with the current fstab using:

sudo mount /etc/sdb1 /media/windows 

  Any ideas? and thanks so much for the help.

---

