---
title: "Memory Card Reader Doesn't Work"
date: 2009-03-12
forum: Hardware
---

### Post by ForenameSurname on 2009-03-12
Hey, guys,

I bought a USB memory card reader (Single Slot, USB 2.0, etc) for my Sony memory card. One of the people on Amazon who reviewed it said he/she uses Ubuntu and the thing works like magic. 

On my computer, though, I put the thing in, went to Places => Computer, clicked on the USB Drive icon, and a window popped out that said the following: Unable to mount location. No media in the drive. 

If it's referring to the emptiness of my memory card, that's a lie, because it's almost full. The red light on the reader is on. 

Any suggestions would be greatly appreciated.

Thanks a lot!

-FS

---

### Post by andrewc6l on 2009-03-13
One suggestion I learned from an OpenBSD FAQ: always put the card in the reader, then insert the reader into the USB port. When you eject, take the reader out first and then take the card out. I'm not sure if it's true for Ubuntu, but here's an explanation for the issue on OpenBSD:

[http://www.nmedia.net/flashdist/flashadapter-howto.html](http://www.nmedia.net/flashdist/flashadapter-howto.html)

Also, what filesystem is on your card? You might have to mount it explicitly:

sudo mount -tvfat /dev/sda1 /mnt

(using appropriate values for vfat and sda1 depending on your filesystem and device address respectively.)

---

