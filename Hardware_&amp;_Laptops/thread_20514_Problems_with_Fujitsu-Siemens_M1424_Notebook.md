---
title: "Problems with Fujitsu-Siemens M1424 Notebook"
date: 2005-03-17
forum: Hardware &amp; Laptops
---

### Post by doco on 2005-03-17
With Hoary my USB-Devices dont work and I have no access to my windows partition (ntfs)! :cry:

---

### Post by lorap on 2005-03-17
hi friend!
lets move ahead!
we'll connect you right now to the ntfs windows partitions:

i.create a folder,say "win" in your home directory this way:

sudo mkdir /home/yourusername/win

ii.now we'll connect you to the ntfs partitions:

sudo mount /dev/hda0 /home/yourusername/win -t ntfs -o umask=000
----------------------------------------------------------------------------------------------------------------
now we're gonna connect you to the usb cdrom or hard drive you've.

i.create a directory say "usb-cd" in "/media" directory:

sudo mkdir /media/usb-cd

ii.now lets add a line to the "fstab" file in "/etc" directory,but firstly we'll open it:

sudo nano /etc/fstab

iii.now add this line:


/dev/sr0 /media/usb-cd udf,iso9660,rw,user,noauto 0 0

iv.save the changes:

ctrl+o

v.exit:

ctrl+x

p.s.:
once you get an error the device's busy or doesn't exist change "hda0" to "hda1" or even "hda2".but begin with "hda0" anyway.
about usb devices:
if it wouldn't work try instead "sr0" - "sr1" - "sda0" - "sda1".
what's your version?warty or hoary?
let me know if it worked.
have a nice day!
pavel

---

### Post by lorap on 2005-03-17
hi friend!
lets move ahead!
we'll connect you right now to the ntfs windows partitions:

i.create a folder,say "win" in your home directory this way:

sudo mkdir /home/yourusername/win

ii.now we'll connect you to the ntfs partitions:

sudo mount /dev/hda0 /home/yourusername/win -t ntfs -o umask=000
----------------------------------------------------------------------------------------------------------------
now we're gonna connect you to the usb cdrom or hard drive you've.

i.create a directory say "usb-cd" in "/media" directory:

sudo mkdir /media/usb-cd

ii.now lets add a line to the "fstab" file in "/etc" directory,but firstly we'll open it:

sudo nano /etc/fstab

iii.now add this line:


/dev/sr0 /media/usb-cd udf,iso9660,rw,user,noauto 0 0

iv.save the changes:

ctrl+o

v.exit:

ctrl+x

p.s.:
once you get an error the device's busy or doesn't exist change "hda0" to "hda1" or even "hda2".but begin with "hda0" anyway.
about usb devices:
if it wouldn't work try instead "sr0" - "sr1" - "sda0" - "sda1".
what's your version?warty or hoary?
let me know if it worked.
have a nice day!
pavel

---

