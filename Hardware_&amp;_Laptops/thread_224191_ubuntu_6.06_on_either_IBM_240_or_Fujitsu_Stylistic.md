---
title: "ubuntu 6.06 on either IBM 240 or Fujitsu Stylistic 3400"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by Rich Byett on 2006-07-27
Hi guys,
i would like to install ubuntu 6.06 on either my IBM Thinkpad 240 or my Fujitsu Stylistic 3400 tablet pc. i have the install disk and also the image on a usb stick. however, i only have a pcmcia cdrom for both units, and no floppy on the 3400. i cant get either unit to boot to either the usb or pcmcia cdrom in order to install ubuntu. can anyone help? 

Many thanx 

Rich

---

### Post by bcw on 2006-08-24
I haven't worked this all out yet, but some of it might help you:

Make Debian install floppies (boot, root, and first driver), insert Debian CD or DVD (I used Sarge 3.1r2 DVD, but I don't believe it matters), and boot and install.  Adding 'vga=788' blanks display.

Substitute Ubuntu Dapper sources.list file
Insert (K)ubuntu CD into drive, mount the CD, add the CD to the sources.list file
'apt-cdrom add'

If I rebooted while carrying out the aptitude install steps below, I was left with an inoperable wifi network setup.  YMMV.

(aptitude is sometimes more comprehensive in updating packages)
aptitude update
Run this twice if there are errors the first time.

aptitude install gnupg (<= to prevent scary but harmless complaints about not being able to verify package signatures)
aptitude install linux-686 udev pcmciautils modutils usbutils pciutils pciutils ksymoops hal hal-device-manager dbus

aptitude update; aptitude -y dist-upgrade; aptitude -y upgrade; aptitude -y -f install
(repeat above so it is all done twice)

works for me

su (to become root)

aptitude install kubuntu-desktop
aptitude install synaptic setserial sudo

---

### Post by bcw on 2006-08-28
An even better answer (since you don't have the 3400 floppy drive):
[http://www.interstice.com/journals/Simon/ims/20030911/usbcd.html](http://www.interstice.com/journals/Simon/ims/20030911/usbcd.html)

He talks about a project which is creating Ubuntu loaders that run from Windows.

Cheers,
Bret

---

### Post by cloakable on 2006-11-25
You can get boot floppies from Damn Small Linux that support normal, usb, and pcmcia booting, even if your BIOS doesn't.

Try [here.]("http://http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/")

Look for the bootfloppy.img, bootfloppy-usb.img and pcmciafloppy.img images. Does exactly what it says on the tin. :)

---

### Post by themischiev on 2008-06-26
Stylistic 3400 Harddrive Image For Download?

Please Someone Have An Image Of The Fujitsu Stylistic 3400 Hard Drive With Ubuntu Installed That I Could Download And Copy To My Stylistic 3400 Hard Drive?

---

