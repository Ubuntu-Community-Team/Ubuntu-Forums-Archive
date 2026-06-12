---
title: "Could I install Linux through a USB pen drive when my BIOS can't read USB for booting"
date: 2008-09-05
forum: General Help
---

### Post by SZF2001 on 2008-09-05
Pretty much the title.

Trying to install openSUSE and my CD drive in my laptop is crap so it can't get the Live session going without hitting itself in the nuts and failing completely.

The idea is, maybe there is something I can boot into (something small like GParted or maybe even a Ubuntu disk), have IT mount my USB drive, then just continue to read off the USB drive without interference so I can go through the Live session with openSUSE and install it.

Hey maybe this is my calling, making a small linux boot-app to read usb pen drives. But oh wait everyone is updated their BIOS.

I'm pretty sure my Compaq nx9030 has the latest BIOS and still can't read off a USB drive (but now it can do a network install), so if anyone could help, that would just be SUPER DUPER.

---

### Post by bingoUV on 2008-09-05
Are you saying your CD drive is totally useless for booting? Or it can boot off small images like gparted (that you mention)?

**maybe there is something I can boot into**
Do you expect this something to be a CD? 

Installation methods, and especially exotic ones like you seek can be very distribution specific. So an OpenSUSE forum would get you better help much faster. I can tell that it is certainly possible in Fedora if you can boot off a CD with a small image.

Fedora: Just download boot.iso, burn it on a CD. Store the whole DVD/CD ISO image somewhere on the USB pen drive or your hard disk. When installation starts, give it an option "askmethod". After initializing, it will ask you where is the image which you want to install from. You can browse hard disks and pen drives at this point to locate your DVD/CD ISO image. Installation will start from that DVD/CD ISO

---

### Post by SZF2001 on 2008-09-05
Yea, I can still use the CD drive for booting. The Ubuntu varients seem to go fine (slowly, but fine) in it. openSUSE seems to be needing more resources - I know the laptop can handle it but it's just not working out with the drive. So I would hope to find something like:

Boot into (something) with CD drive
Have whatever is booted read and mount the USB pen drive
Load into whatever the pen drive has on it

Something like that. But there are other methods and I'll look into what you posted.

Anyone with anymore ideas?

---

