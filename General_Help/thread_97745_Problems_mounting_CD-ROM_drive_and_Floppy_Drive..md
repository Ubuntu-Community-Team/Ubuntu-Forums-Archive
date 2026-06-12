---
title: "Problems mounting CD-ROM drive and Floppy Drive."
date: 2005-12-01
forum: General Help
---

### Post by InsanePenguin08 on 2005-12-01
I'm new to Linux, and not exactly sure what mounting/unmounting is all about, but in any case, I can't do it!  

I made a mistake when partitioning and deleted the Windows partition (no biggie,) but the file system for my Ubuntu partition is ext3.  Any ideas on what to do?

Oh, and Ubuntu doesn't recognize my MP3 player (Dell DJ pocket)  Just wondering, but does anyone know a way to fix that, as I'd really like to get all my music back onto the computer.

---

### Post by psychicdragon on 2005-12-01
You're using the default Ubuntu Gnome desktop right?

In which case it _should_ be mounting all this stuff for you, just like Windows.

What happens if you put an audio cd in the drive for instance?

You can take a look at the settings for mounting media through the  **System** menu at the top. Go to **Preferences** and then **Removable Drives and Media**.

If it's not working, try entering these commands in a terminal and then insert an audio cd again and see what happens.
```
killall gnome-volume-manager
gnome-volume-manager &
```

---

### Post by InsanePenguin08 on 2005-12-01
The CD plays, is that all mounting is used for?

I'm less worried about my floppy drive, it's not like I ever use it anymore.

---

### Post by psychicdragon on 2005-12-01
Yup, that's it. 
Mounting is basically just the process of pointing a location on the filesystem to some sort of storage media. In the case of the cdrom, the "mount-point" is /media/cdrom/. It's totally hidden from you in Windows but the function is more or less the same.

You can do this stuff from the command-line as well, using the **mount** and **umount** commands

This mounts your cd:
```
sudo mount /media/cdrom/
```
and this unmounts it:
```
sudo umount /media/cdrom/
```
Gnome does this stuff for you though, so you'll never have to worry about it, if you don't want to. ;)

---

### Post by InsanePenguin08 on 2005-12-01
Thanks for all your help, having that cleared up is nice.

---

### Post by Tosa on 2005-12-02
But what about floppy? It is not mounted at start up, and it is a bit anoying to type the mount command whenever I need it.

In /etc/fstab there is a line:

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

but floppy isn't mounted. I've read in so me post here that changeing auto to vfat would do the trick, but it didn't for me. Still have to mount floppy manually...

Any suggestions?

---

