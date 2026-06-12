---
title: "External hard drive doesn't mount on boot-up"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by NeoChaosX on 2006-06-03
Okay. I have an external 80 GB hard drive that I use as extra storage space. I installed Kubuntu off a live CD and told it to mount this drive at /mnt/cupil. However, whenever I boot into Kubuntu, the system never mounts this dirve; I have to mount it manually after I log in.

Here's what my /etc/fstab file looks like. The drive in question is /dev/sda1:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       			<dump>  <pass>
proc            /proc           proc    defaults        			0       0
/dev/hdc5       /               ext3    defaults,errors=remount-ro 		0       1
/dev/hdc7       /home           ext3    defaults        			0       2
/dev/sda1       /mnt/cupil      vfat    defaults,user,umask=007,gid=46		0       0
/dev/hdc1       /mnt/windows    ntfs    defaults,nls=utf8,umask=007,gid=46	0       1
/dev/hdc6       none            swap    sw              			0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     			0       0
```

I've tried putting "auto" in the hard drive's option, but the OS still refuses to mount the drive on boot-up. Does anyone know how I can fix this?

---

### Post by givré on 2006-06-03
Quite strange...
Anyway, if your external hard drive is an usb one (of course it is ) did you try to let it mount by gnome-volume-manager at log in
See that for more information [http://www.ubuntuforums.org/showpost.php?p=1088803&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1088803&postcount=4)

---

### Post by NeoChaosX on 2006-06-07
Why would I use gnome-volume-manager? I'm using Kubuntu.

---

### Post by givré on 2006-06-08
[QUOTE=NeoChaosX]Why would I use gnome-volume-manager? I'm using Kubuntu.[/QUOTE]
Ok, sorry man, i didn't notice that :cool: 
But anyway, there is the equivalent of g-v-m in kubuntu (it's ivman or something like that, i can't remember), so try what i said.

---

### Post by NeoChaosX on 2006-06-10
That didn't work. Drive continues to not be mounted on boot.

---

### Post by givré on 2006-06-10
And what's happens if you plug it after?

---

### Post by NeoChaosX on 2006-06-11
If I unplug it and plug it in with ivman installed, it does automatically mount it. However, I'd rather not do that everytime I boot into Linux; I'd just like it to mount automatically on boot-up like it did in Breezy.

---

### Post by givré on 2006-06-11
yes of course, so two solutions,

- Change the line in your fsab about your usb hard drive : add uid=1000, so the 
- If it doesn't work, delete this line, so it will be mount by ivman automaticly (it is not mount at start up because it's already mount because of this line)

---

### Post by NeoChaosX on 2006-06-11
Neither of those options work. The drive is still unmounted when I log in, even when I comment out the fstab line and have ivman run when I log in.

---

### Post by NeoChaosX on 2006-07-30
*bump* Seriously, can anyone help here? The drive mounted on boot-up in Breezy, but not in Dapper? What's going on?

---

### Post by NeoChaosX on 2006-08-06
Again, I'm asking - anybody know how to fix this? I hate having to manually mount my external drive every time I boot into Kubuntu.

---

### Post by benfindlay on 2007-02-26
This is a problem Im currently trying to solve myself, but with little luck, don't suppose anyone has come up with a solution to it?

---

### Post by buntu_hugenewbie11 on 2008-01-28
What about one year later? Any solutions?

---

### Post by BryanFRitt on 2008-05-03
I added ,**uid=1000** to the end the section before the **0 0** ... and installed **ivman** and it works (don't know which, or both, of the previous fixed it)

(replacing XXXXXXXXXXXXXXXX, /media/XXXXX, and /dev/XXX# with the appropriate letters and number, ntfs-3g with the appropriate file system, and locale=en_US.utf8,rw,auto,users with the appropriate options. try other posts if you need more info)

(use **sudo** YourTextEditor /etc/fstab, remember to **backup** this file first)
in 
**etc/fstab**
put in 
UUID=XXXXXXXXXXXXXXXX /media/XXXXX ntfs-3g locale=en_US.utf8,rw,auto,users,uid=1000 0 0

you can get the UUID from the konsole by
cd '/dev/disk/by-uuid/'
**ls -alF '/dev/disk/by-uuid/'**

you can get the corresponding **/dev/XXX#** from when the devices mount when you unplug and replug them back in
in konqueror type this in the address bar
**media:/**
then right click on whatever you want to mess with
click on the Meta Info tab
look at **Device Node: /dev/XXX# **

Doing the UUID part helps in case you have more than one external drive, etc...

tip: you might want to play with the **mount** command **before rebooting**, just in case

--------------------------------------------------------------------------------

ps. unmounting has more steps to do after doing this.  
(still figuring out details as of witting this, below is what I've tried, misc unorganized notes 
you might not want to spend time reading unless you want to help figure out this problem)
If anybody knows how to fix any of this feel free to help ...
... on to more research

Icons on the desktop showing the mounted/unmounted drives don't show up on startup

umount /media/XXXXX works from the konsole window
and then the icons appear on the desktop unmounted

right click on the icons (either from media:/ or desktop)->Mount gives
*Permissions denied*
mount /media/XXXXX
gives
[I]Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library. Either remove the setuid/setgid bit from the binary
or rebuild NTFS-3G with integrated FUSE support and make it setuid root.
Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)[/I]

when right clicking on the desktop icons and clicking Safely Remove or by right clicking on the media from media:/, I'm getting an error when trying to umount from media:/, or the icon on the desktop:
[I]Unfortunately, the device system:/media/XXX# (/dev/XXX#) named XXXXX and currently mounted at /media/XXXXX could not be unmountded.
Unmounted failed due to the following error:
Device to unmount is in /media/.hal-mtab so it is not mounted by HAL
[/I]

The two above makes the icons less valuable for mounting/unmounting

mount /media/XXXXX
gives
[I]Error opening '/dev/XXX#': Permission denied
Failed to mount '/dev/XXX#': Permission denied
Please check '/dev/XXX#' and the ntfs-3g binary permissions,
and the mounting user ID. More explanation is provided at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)[/I]

sudo mount /media/XXXXX
works
umount /media/XXXXX
works
mount requires sudo while umount doesn't

unmounting then turning off and then back on gives unmounted drives and things are the way they were before

basically, **after this you have to unmount/mount the drive(s) from the command line after this***, but **they will be mounted at startup**, (if they were mounted during shutdown?)
so take your pick at which is better.
*If you can find a better way of doing this, or fix the problem, please post.

---

p.s.  I'm using KUbuntu 8.04 with 2 external NTFS harddrives hooked via USB 2.0

---

