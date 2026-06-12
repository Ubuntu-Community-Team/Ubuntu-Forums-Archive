---
title: "Problems to mount USB &amp; Floppy devices automatically"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by vsacramento on 2005-10-22
Hi, I've just installed Ubuntu Breezy in a station in my Network, but I've been having problems to mount floppy, Pen drive (usb memory key) via Nautilus. I had problems in two scenarios:

First: at my PC at home where I have a local user that belongs to plugdev, floppy, cdrom groups. My usb memory key is mounted automatically in the first time with RW rigths, but after umounting it, I cannot mount It again via Nautilus. The program report this error: given UDI is not a mountable volume

Regarding to the floppy disk, I could not even mount it once. I receive the error message: given UDI is not a mountable volume

Second: My PC at work where my user is authenticated via NIS Server (running SLackware). In this scenario my groups are those sent by NIS Server, so I do not have the plugdev, floppy, and so on. I had to create these groups and join the local uses to them so that the users can have rigths to execut 'pmount-hal' via Nautilus.

I think It would be very interesting if someone add this second scenario in Ubunto documentation making explicity what a network administrator must do when using nis client in ubuntu linux.

But, I still have problems to mount the floppy and usb memory key (pen drive). I always get the error message: given UDI is not a mountable volume
What should I do to solve this problem?

I know that I can manually mount these devices, but the users of my network don't :-)  (mount /media/floppy/ or mount -t vfat /dev/sda1 /mnt/pendrive)

thanks in advance.
Vagner

---

### Post by Major_Stitch on 2005-10-22
[QUOTE=vsacramento]
...
But, I still have problems to mount the floppy and usb memory key (pen drive). I always get the error message: given UDI is not a mountable volume
What should I do to solve this problem?

I know that I can manually mount these devices, but the users of my network don't :-)  (mount /media/floppy/ or mount -t vfat /dev/sda1 /mnt/pendrive)
[/QUOTE]

How about making a script? 
Then it's only a double-click (put it on desktop or somewhere else) for them and it's like they wrote the whole 'mount ...' command.
If you don't know how to make scripts then here's a guide:
[http://www.linuxcommand.org/wss0010.php#write]("http://www.linuxcommand.org/wss0010.php#write")
Hope that's what you need, and about the other thing I don't know anything about it (I'm still green ;) ).

EDIT:
It really doesn't mount automatically for me, but I made 2 scripts for mount and umount for floppy but my USB stick mounts and umounts normally without anything. I can send you those scripts if you need them.

---

### Post by fouad on 2005-10-26
I have the same problem. My users is in plugdev group in NIS server .

In my /etc/fstab I have
 /dev/sdb1       /media/usbkey   vfat    rw,user,auto    0       0

no users can have usbkey mounted automatiquely and they can't mout it with pmount
I have also a message with HAL when i just coonect to gnome 
Failed to initialize HAL!
in other machines without NIS server I don't have this problem.

Do you you the same things

Please Help

---

### Post by steevc on 2005-10-26
I've been trying to get my card reader and USB flash drive to work. Nothing in fstab would make them mount automatically (using KDE). I booted into Gnome and they just appeared on the desktop. I eventually found a mention somewhere of using ivman. I ran this on KDE and they all mount automagically :) I assume Gnome has something built in to do the job.

I just need to add ivman somewhere appropriate in my start-up. That's an area I need to read up on.

---

### Post by iNerdSure on 2005-10-28
Well, I hope this solution will help some people. I use a USB Thumbdrive. When I first installed Breezy, the thumbdrive was recognised and mounted automatically. However, recently, for whatever reasons, the system stops recognizing the thumbdrive. 

Tried various methods suggested in the various forums. Still couldn't get it to work. Eventually, found that if I boot up with the thumbdrive plugged in, the system will recognize and mount the the thumbdrive automatically .. truly plug & play. 

As a Linux convert newbie, I still can't figure out what's the root cause of the problem, but I guess I can live with the work around for the time being.

... Now, if I can only get the sound to work ...:???:

---

