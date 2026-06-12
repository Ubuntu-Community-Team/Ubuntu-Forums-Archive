---
title: "Mounting Harddrive"
date: 2010-01-10
forum: Hardware
---

### Post by qkzoo on 2010-01-10
Hello!

I recently installed Ubuntu 9.10 on our main family computer.  I obtained a second hard drive (40gb samsung) to copy all our music, pictures and Quicken (financial software) data to.  That part was easy.  Now, I setup Ubuntu, upgraded all the packages using the automatic upgrade features in Gnome and everything seems set, except for some minor annoyances.  First of all, the second hard drive appears on the desktop and I have to "mount" it whenever I want to access it.  Second, my wife's login doesn't seem to have permissions to access it.  What do I need to do so Ubuntu automatically "mounts" this device and gives permissions to "all users" including my children if I so desire, to access this drive, save, alter and execute items on it?  I guess I'd say that this drive should be "shared" (is that the right terminology?) between all users?  For instance, all our music is on there, so it would be nice if my wife could access the music I've put on there, and vice versa.  Also, our financial information is on there, so it would be nice if I could load GNU Finance and use the same file that my wife is using, know what I mean?

Thanks in advance for any assistance!

Q

---

### Post by Barriehie on 2010-01-10
Please post your /etc/fstab file.

---

### Post by qkzoo on 2010-01-11
Sure, here it is!

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=03d3f746-7994-46f4-861c-1a838ab8ead5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e363a29e-d423-4b5a-a10f-1697139dd9d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by Barriehie on 2010-01-11
I don't see the drive in your fstab file so give this a shot.  From the terminal (Applications > Accessories > Terminal) and make a mount point:
```

cd /media
sudo mkdir family
gksudo gedit /etc/fstab

```
At the end of the file:
```

/dev/sdb1  /media/family  auto  auto,user,exec,rw  0  2

```
This last line will mount, I'm assuming it's dev/sdb1, on /media/family directory, auto-detect the filysystem type, auto-mount at bootup, users can mount the device, execute files, mount as read/write.  The 0 tells dump not to worry about backing it up and the 2 tells fsck to scan.  To make sure the /dev/???? you can go in gparted and it can tell you.  This is System > Administration > Partition something on my machine.

With the last line in place in gedit now CTRL-s (save), CTRL-w (close), and CTRL-q (quit).  Exit the terminal, (exit), and restart.
HTH,

---

### Post by oldfred on 2010-01-11
After you edit fstab you can do this:

mount -a

It will tell you if any errors or just return if ok. And you have your new mount without rebooting.

---

### Post by qkzoo on 2010-01-12
Ok!  After following Barries instructions, it mounted perfect, thanks!  I even logged on as the Mrs. and her login worked just fine with it.  Now, is there any way to get the "36 GB System" icon off the desktop, since it's already up in "Places"?  I know it's only a minor thing, but it's just kind of annoying having it there!

Thanks again to both of you for your help!

Q

---

### Post by Barriehie on 2010-01-12
> **qkzoo said:**
> Ok!  After following Barries instructions, it mounted perfect, thanks!  I even logged on as the Mrs. and her login worked just fine with it.  Now, is there any way to get the "36 GB System" icon off the desktop, since it's already up in "Places"?  I know it's only a minor thing, but it's just kind of annoying having it there!

Thanks again to both of you for your help!

Q

Glad it worked!  Yes, there's a way but I can't remember right now!  I'll find it when I get back from work.

---

### Post by Barriehie on 2010-01-12
Okay, you can do this:  Right click on either of the panels and **Add to panel** you want to add the disk mounter applet.  This should put the drive(s) on the panel and then you can delete the icon on the desktop.  I KNOW there's a way in nautilus to set the visibility but I can't for the life of me find it!!!

---

### Post by Barriehie on 2010-01-14
So is this [SOLVED]?  I've had an issue with gnome-settings-daemon so have been unable to explore your other issue.

---

### Post by Barriehie on 2010-01-21
For the benefit of others is this [SOLVED]?

---

