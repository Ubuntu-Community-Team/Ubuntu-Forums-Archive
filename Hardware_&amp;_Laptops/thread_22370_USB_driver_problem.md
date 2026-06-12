---
title: "USB driver problem"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by wxm505 on 2005-03-27
I worked with USB driver very well until this morning.
When I pluged in my USB disk there was not a sda1 icon
on the desktop which was supposed to be there.
I mount the usb driver manually .but I can not access the 
files in it.All the directories were displayed as single file.
The point was that it worked just well yesterday.
I did some change to my box yesterday,
I installed the linux-module-686.
Will it cause the problem??
Any help????thanks a lot.

---

### Post by lorap on 2005-03-27
hi friends!
let's solve your problems!
now we'll solve the problem for the one who couldn't get connected his usb fat32 device:
i.create a directory say "usb-fat" in your home directory:

sudo mkdir /home/yourusername/usb-fat

ii.connect a system driver to it:

sudo mount /dev/hda0 /home/yourusername/usb-fat -t vfat -o umask=000

if it pops up a message "the device's busy" then try "hda1" and so on until you find the free device out.

iii.to unmount the device you don't anymore need do this:

sudo umount /dev/hda0

-o umask=000 gives you w/r rights.
-------------------------------------------------------------------------------------------------------------------------

now for those who's usbcd:

i.create a directory "usb-cd" in "/media" directory:

sudo mkdir /media/usb-cd

ii.open "fstab" file:

sudo nano /etc/fstab

iii.edit it this way,remember in warty sr0 or sr1 or so on works with usb,adding this line:

/dev/sr0        /media/usb-cd   udf,iso9660 rw,user,noauto  0       0

iv.save changes:

ctrl+o

v.exit:

ctrl+x

you're ready to get cd inside :-)

have a nice day buddies!
pavel

---

