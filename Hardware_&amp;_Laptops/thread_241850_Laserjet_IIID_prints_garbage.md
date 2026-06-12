---
title: "Laserjet IIID prints garbage"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by quaestor_pg on 2006-08-22
Hi all,

After installing Ubuntu I was able to add a new printer in gnome (using foomatic-gui). However, when I try printing anything I find that my HP Laserjet IIID printer spits out page after page of garbage.

I've tried using the basic Laserjet driver as well but I get the same thing. The printer works perfectly under Windows XP and was working with Fedora Core 3 before the change to Ubuntu.

I'm not sure what I can try at this point. Can anyone point me in the right direction?

Thanks

---

### Post by zxee on 2006-08-23
Are you using the correct driver for your printer? 
The recommended driver is listed here: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_3D](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_3D)

---

### Post by quaestor_pg on 2006-08-23
I've tried both the ljet3d driver from the default install as well as trying the pdd file from the site you referenced. They give similar output. The original ljet3d driver prints a single line of garbage on each sheet, whereas the pdd file will produce a few pages of garbage.

Any other suggestions?

---

### Post by quaestor_pg on 2006-08-23
I'm still unable to print anything on this printer. Is there a way to peel back the levels of printing complexity until I find where the problem lies?

As I understand it, CUPS and Foomatic interact to create the printer. Is there a subsystem below these that I can try to configure directly?

Thanks

---

