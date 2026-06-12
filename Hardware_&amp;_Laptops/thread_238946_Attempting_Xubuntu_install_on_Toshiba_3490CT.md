---
title: "Attempting Xubuntu install on Toshiba 3490CT"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by Flamekebab on 2006-08-18
I have a Toshiba 3490CT. It has both a PCMCIA network card and its own dock-thingy (not a true dock, but like a thing with a load of ports on that can be plugged into the side). I want to install Xubuntu on it without doing it the same way a friend (who also owns one of these) had to do it - ie swapping hard drives.

I happen to own a 1GB USB flash disk and also a USB floppy drive (and a floppy somewhere with a special booting app on it to force a PC to boot from a chosen device, even if it normally doesn't support it).

What I'd like to do, ideally, is to place either an ISO on the flash disk, or extract the ISO to the flash disk and then boot using the floppy drive and the app I mentioned earlier. However, having never done this before, I don't know how! I'm going to give it a try, but I'm unsure of what to expect.

On the other hand, I'm also considering a network install, however, after a bit of googling, this seems to involve setting up a DHCP server and FTP server.. A bit complicated for me.

I do happen to have a Buffalo NAS device which runs an FTP service and uses a fixed IP address. Would that allow me to avoid setting up a server?

---

### Post by wsj-m on 2006-08-18
I might recomend the following Ubuntu Wiki entry on how to use Linux or Windows to install the iso image onto a flash drive ...

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I did this for a while with my Toshiba Satelite M35X-S149 with Xubuntu.  As a note, if you are using a flashdrive, it will be slow.  Faster than running of a CD-ROM, but slow.  I finally use gparted and re-partitioned my hard-drive to install Xubuntu on it.

Good Luck ... :)

---

### Post by Craigus on 2006-09-20
This is how I did it on my 3490:

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

Very easy, but assumes that you have a Windows machine on your network.

---

