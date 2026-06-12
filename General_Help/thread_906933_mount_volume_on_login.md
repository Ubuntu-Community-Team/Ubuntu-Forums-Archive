---
title: "mount volume on login"
date: 2008-08-31
forum: General Help
---

### Post by catch2two on 2008-08-31
I have a secondary drive which contains my mp3's this drive is not mounted when i first login. I can right click and mount it or double click and it is mounted after i open a folder, but the issue i am having is if i open rhythmbox first it just starts to lose its database (i have quite a few mp3's)

This was not a problem in fedora or previous version of ubuntu studio I do not believe. 

I know you are thinking just mount the drive first and then open the media player, but i already have a huge list for other users (my wife) of this computer to do.

So i just need it to be mounted when i log in is there an easy way to do this?

---

### Post by aloshbennett on 2008-09-01
You can add an entry to /etc/fstab file.
Look at the previous entries and you should be able to figure out how to do it.

Keep a backup of the file incase you are a first-timer (If you screw things up, put in your live cd, boot and replace the fstab with the original)

---

### Post by catch2two on 2008-09-01
Might need some help with this just to be on the safe side. So this is what i have in this file so far:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4a5a1135-b947-412c-a430-ff0d0b114269 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5cd24876-b76e-43d1-a470-8ded68d90c91 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Let me know what info you need to to add the second drive to the mount point.

this is the UUID and other infor i can get for that drive:

size: 292.3GB
Media: Hard Disk
UUID: ae3a646f-b456-4030-a669-45c6a2251754
File System: ext3 (1.0)
Mount Point: /media/disk
File System: ext3
Mount Options: rw nosuid nodev relatime date=ordered

---

### Post by aloshbennett on 2008-09-01
Add this to the bottom of fstab

> # secondary storage device
UUID=ae3a646f-b456-4030-a669-45c6a2251754 /media/disk ext3 defaults 0 1

Assuming your secondary disk is not removable storage and would be present always when you boot, this should be fine.

Here's a detailed guide
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by catch2two on 2008-09-01
I could not get this to work. I added the line of code and the next time i booted it did a check of the drive while the boot screen was loading. I was unable to access the drive or mount it as a user or as root.

Any other ideas?

---

