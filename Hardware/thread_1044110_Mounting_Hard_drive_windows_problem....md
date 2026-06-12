---
title: "Mounting Hard drive windows problem..."
date: 2009-01-19
forum: Hardware
---

### Post by hollandnigel on 2009-01-19
I have a laptop with Vista, but it's not working, there appears to be a problem with the HDD,
I am now running Ubuntu Live from a USB Key, but when I try and access the HDD it is unable to mount, i think it's because the PC wasn't shut down correctly.
Is there anyway of resetting the computer so that windows doesn't realise that there was an error?

Hope that makes sense

---

### Post by matpol on 2009-01-19
How are you mounting it? Using the mount command?

This article might help you:
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

If windows isn't starting up try running a the windows install disk - it has a repair mode.

---

### Post by hollandnigel on 2009-01-27
Tried the windows disc's
Repair mode doesn't work, it doesn't recognise that there's even a hard drive connected

---

### Post by theApokalypsis on 2009-01-27
try out this command, i use it when i have an unclean shutdown.

sudo mount -t ntfs-3g /dev/sdb1 /media/diskname -o force 

diskname is your HD name and /dev/sdb1 might differ depending on your setup.

it might say it didnt, but try mounting it in Nautilus(if ur using GNOME) again and it should work.

---

