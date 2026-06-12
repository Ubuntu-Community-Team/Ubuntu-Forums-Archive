---
title: "No USB in Warty"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by nickspoon on 2005-03-25
When I plug a USB drive into my PC, nothing happens. I also have no USB wireless mouse support. I'm using the latest i386 version of Warty (which I downloaded yesterday). It installed fine and everthing works except for the USB. If I go into Device Manager, I get all my CD drives, hard drives, modems and a USB 1.1 Controller. It doesn't say that anything is attached to it. My USB drive is in Fat32 format. I checked the /dev folder for anything like sr or sdc or whatever USB drives are, but I can't find anything. Help!

---

### Post by ola on 2005-03-25
You can check the logfiles while you are inserting the driver
```

sudo tail -F /var/log/messages

```

Then insert your drive and post the messages from there!

.o

---

### Post by nickspoon on 2005-03-26
I've checked my log. I get no messages when I insert my drive.

---

### Post by wxm505 on 2005-03-27
The same thing happened to me.
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

### Post by clb137 on 2005-03-27
HI Nickspoon

Does you USB mouse work once the system has booted up?  Have you tried to unplug and re plug?

ALso do you get a 'resource error 4 ' on boot up at the very start of the boot process?

clinton

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

### Post by nickspoon on 2005-03-27
Thanks. I'll try it and get back to you. I'm having GNOME problems at the moment, but that's not for this thread. I unplugged, replugged, did a magic dance around and even prayed to my usb mouse, but no luck. Just in case it helps, if I go into Device Manager or whatever (my linux pc has no internet connection, so I have to use the Windows one) with anything plugged into my USB ports, I can only see "USB 1.1 Controller". :-k  :confused:

---

