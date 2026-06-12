---
title: "Make Installation CD"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by sebekhoteph on 2009-02-06
I am making a bootable CD that will install Ubuntu Hardy kernel in the 1st hard drive. I want it to overwrite anything in the hard-drive, as this is going to be an Ubuntu based appliance. I want a silent install.

I followed the guides on making a Live CD from Scratch. My isolinux.cfg is here:

DEFAULT install
LABEL install 
kernel /casper/vmlinuz
APPEND file=/isolinux/preseedfile.seed initrd=/casper/initrd.gz boot=casper debian-installer/locale=en_US console-setup/layoutcode=us debian-installer/framebuffer=false debconf/priority=critical acpi=force quiet vga=791 splash -- 

However, my CD is really not installing, it is behaving like a LIVECD - ie, booting the kernel from the CD, and not writing/ installing to the hard drive.

Can anyone tell me, how can I make the CD with iso image, an installation CD, that installs silently (no questions asked from user)

Thanks

---

### Post by Svensk023 on 2009-02-06
you can download an "alternate install cd" iso and i believe that is just a straight install disk, no liveCd function. just a text install

---

### Post by sebekhoteph on 2009-02-06
I have to customize the install CD with my own packages and applications. I started with an install CD (install CD from scratch tutorial here). After that configuration, I want to make back into an install CD

Also, since I want a silent install, I cannot use the install CD directly. I have to customize the installer files, so that it asks no questions.

---

### Post by mozkill on 2009-02-06
Until one day, when someone forgets they left that CD in their cdrom, then there is a power failure and the machine restarts itself and erases everything!

---

### Post by sebekhoteph on 2009-02-08
I am thinking of taking a standard ubuntu iso, and replacing that content with mine. Dont know if that would work or not, as I have done several kinds of customization (in the kernel as well as in isolinux.cfg etc).

---

### Post by sebekhoteph on 2009-02-08
> **mozkill said:**
> Until one day, when someone forgets they left that CD in their cdrom, then there is a power failure and the machine restarts itself and erases everything!
Hey Mozkill - this application is not for everyday PCusers. The application is an appliance, and the hard drive is used only for this application. This is not for everyday PC

And I do want to know how this is to be done. Any help in that directiion will be appreciated.

---

### Post by maybeway36 on 2009-02-10
You could preseed the Alterate Installer like you would with Debian:
[http://wiki.debian.org/DebianInstaller/Preseed](http://wiki.debian.org/DebianInstaller/Preseed)
And you can add packages to it too:
[http://wiki.debian.org/DebianInstaller/Modify/CD?highlight=%28cd%29](http://wiki.debian.org/DebianInstaller/Modify/CD?highlight=%28cd%29)
I'm not sure whether or not you can remove packages, but there must be some way.

---

### Post by sebekhoteph on 2009-02-11
Thanks, maybeway36 
Hope it works for Ubuntu. I'll try these out.

---

### Post by bedge on 2009-08-10
How did this work out in the end?
I need to do the same thing.

---

### Post by phillw on 2009-08-10
If you have a LAN set-up, there is an article on doing it that way here ....

[http://www.debuntu.org/how-to-unattended-ubuntu-network-install](http://www.debuntu.org/how-to-unattended-ubuntu-network-install)

I'm sure I've come across someone doing an instal with a script - I'll have a look for you.

Phill.

---

