---
title: "USB Persistent?"
date: 2008-08-06
forum: General Help
---

### Post by spwn on 2008-08-06
Hey, i LOOOOVEE xubuntu, and i last time kind of almost f*cked up my windows... now it's fixed, and i realized that a linux on a usb stick would be better..

However... i have tried this:
[http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-live-cd/](http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-live-cd/)

It's too hard to understand around the terminal part.. *sigh*

I am now using UNetbootin, but ive read that they don't do persistent changes so it will always be a clean install (wich i don't want)...

Unless there's another way... can anyone help me... try to fix the livecd on my usb make it changeable!!

---

### Post by reacocard on 2008-08-06
if you have a big enough (2GB+ iirc) drive, you can just do a full install of xubuntu directly onto the drive. you have to use manual partitioning and specifically choose the USB drive, and you also have to change the GRUB options so it gets installed to the drive instead of your computer, but aside from those two small bits it works just like a normal install.

If you have a smaller drive (1GB), you can do a text-only install from the alternate CD and then build up from that.

a word of warning: don't make a swap partition for it on the drive. swap will wear out flash memory really fast. This does mean that you'll only be able to run it on computers with enough RAM (384MB+), but that's not likely to be a problem.

---

### Post by spwn on 2008-08-06
I'ts actually a 4GB drive i have, and i actually did 1 really simple installation (fedora)..

Not that i really like their theme and ect, but it's really simple to install compiz on their "fedora 8" so that's awsome :P

[http://www.howtoforge.com/compiz-fusion-fedora8-ati-mobility-radeon-9200](http://www.howtoforge.com/compiz-fusion-fedora8-ati-mobility-radeon-9200)

[http://www.pendrivelinux.com/2008/05/17/install-fedora-9-to-a-flash-drive-using-windows/](http://www.pendrivelinux.com/2008/05/17/install-fedora-9-to-a-flash-drive-using-windows/)

lol, i think i just found what i needed, thanks anyways :D

---

