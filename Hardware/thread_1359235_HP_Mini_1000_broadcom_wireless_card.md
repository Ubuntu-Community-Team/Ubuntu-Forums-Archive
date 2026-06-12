---
title: "HP Mini 1000 broadcom wireless card"
date: 2009-12-19
forum: Hardware
---

### Post by Amisten on 2009-12-19
Hello ubuntu community forums! I've heard great things so I've come to see if you can give me a hand.

I own a HP MINI 1000 and I'm trying to fix the known problem of the wireless card in ubuntu 9.10. Now let me tell you the steps I have taken.

First I noticed that ubuntu has put this artical on their support site
[HERE]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP Mini 1000")

Of course this does not work due to the fact that I cannot access the internet (only wireless card in this one)

So then I decide to download it manually (bcmwl-kernel-source)
[HERE](http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source)

This requires me to input the CD which there is no CD-ROM drive and I have no idea how to make it look outside /cdrom at the USB drive.

Then it was on to various corners of the internet looking for linux drivers and the HP site was ,of course, no help.

So in conclusion; without a ethernet jack or CD-ROM, I can't find any solutions. Please help.

---

### Post by IcarusR on 2009-12-19
I don't know how to add USB as a repository for synaptic but if you installed Karmic from USB stick this should work.
With USB plugged in go to /pool/main/b/ on the USB & you should find the required file somewhere there.
Double click on it & it should install. If there are missing dependencies you will have to find them on the USB & install them first.

---

### Post by Amisten on 2009-12-19
Thank you for the reply.

The only two files that are in there are: 

b43-fwcutter_012-1_i386.deb

Build-essential_11.4_i386.deb

and both of them only gave me an error part way through. I didn't write down the error and have now switched back to the pervious ubuntu due to the misses wanting her "internets" back. But if you or anyone else has any more suggestions I would still like to have the newest ubuntu on this netbook

Thanks again.

---

