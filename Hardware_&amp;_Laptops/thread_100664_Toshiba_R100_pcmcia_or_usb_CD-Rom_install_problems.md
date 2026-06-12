---
title: "Toshiba R100 pcmcia or usb CD-Rom install problems."
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by coza on 2005-12-08
Hey guys, 

I have a Toshiba R100 and am itching to get ubuntu runnung so that i can move away from XP. But i cant get it to install .
For those of you who dont know, the R100 doesnt have a cd, or floppy.
When i boot off my pcmcia cdrom ( Freecom.) it boots and starts the install and gets to the detecting hardware stage, where it says that it cant detect a cdrom( even though it just booted off it??) 

In the past, with Centos, i have booted off the pcmcia cdrom and then swapped it to the usb cable, and selected a usb driver form the default drivers. but it seems that ubuntu ( 5.04) doesnt have a usb driver in its set of default drivers. If i had a floppy i could just load them , but i dont, ( maybe i should buy a usb floppy) 

Anyway, does anyone know if 5.10 has better usb pcmcia device support during install ?

Shot.

---

### Post by 23meg on 2005-12-08
I have two suggestions: investigate the advanced install options in Ubuntu (I haven't had to, so don't have the details, but you can find help in the installation prompt where you normally just press enter for a normal install), and if it fails, try smart boot manager, which you can find here: [http://btmgr.webframe.org/](http://btmgr.webframe.org/)

---

### Post by zencoder on 2005-12-13
SBM looks decent, but it won't help me, nor **coza** I suspect.

I have an older Toshiba Portege 3480CT, which has the same issues; no floppy or cd-rom, and only 16-bit PCI card support (its an older system, PIII I think.)

I have a PortNoteworthy PCMCIA CD/DVD-Rom drive that can boot both the breazy CD and DVD discs, but when it gets to detecting hardware it can't recognize that the disc-drive it just accessed and loaded itself into memory from is there.  I've tried **boot: install pcmcia_start=false** with no luck.  Is there a comprehensive guide to all of the advanced settings that can be passed to the installer?  The F1-F6 keys don't offer a lot of help for this specific situation.

---

