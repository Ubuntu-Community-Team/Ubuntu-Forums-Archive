---
title: "ATI Rage Mobility &amp; LCD Projector"
date: 2008-10-21
forum: Hardware
---

### Post by 00b00nt00 on 2008-10-21
nOOb here.

I have a projector connected to my Compaq laptop, and while the desktop image is mirrored correctly to the projector (internal display and projector can be toggled with 'function+4'), I am not able to choose any options within Ubuntu 8.04 itself. I'm looking to span the desktop or increase the resolution beyond that of the internal LCD.

Any suggestions?

---

### Post by teaker1s on 2008-10-21
twinview- depending on whether you are using restricted open gl drivers (ati) you may be able to alter in ati catalyst control centre or free you will need to edit xorg.conf for virtual screen.
I would suggest searching forums as I know little more

---

### Post by 00b00nt00 on 2008-10-22
I haven't installed any restricted drivers - only the drivers that were installed in the Ubuntu installation process. I'm not sure if the ATI drivers support the Rage Mobility chipset as it's getting a bit long in the tooth.

It's not really a big deal; at least I CAN get an image on the projector! Any brain waves would be appreciated, but it's not something to lose sleep over.

Thanks for your input.

---

### Post by teaker1s on 2008-10-22
depending which version of ubuntu you are using, desktop panel
System>Administration>hardware Drivers and use restricted driver.
this will give you catalyst control panel

---

### Post by 00b00nt00 on 2008-10-22
I've tried installing the on-line ATI drivers, but they don't seem to  have made any difference. Neither is Catalyst available.

I did some digging in the xorg log files, and discovered that Ubuntu recognises my projector- including the video resolutions it supports. However, in the screen resolution menu I am only given options to change the resolution of the internal panel. Strange!

---

### Post by teaker1s on 2008-10-25
twinview will give you this

---

### Post by jocko on 2008-10-25
Just to avoid useless attempts at installing restricted drivers:

ATI have never produced any linux drivers for rage cards (or anything else older than radeon 8500). Recent drivers from ati only supports radeon 9500 and newer cards.

For rage cards, the only option is the open source driver (named "ati"), which is already preinstalled in ubuntu. So don't try to change to another driver, there is no other driver that will work (but I don't know how to set it up for dual screen or projectors).

---

### Post by olking on 2009-03-25
I am very much a newbie.
I am trying to use a projector with my laptop running on ubuntu 8.
When I boot up, connected to the projector it recognises the source and continues to do so until the point where my user name is called for and then loses the source.
When running in windows recognition is achieved by toggling the function key with F5.
Can anyone tell me is there a similar method from ubuntu?
The F5 method doesnt work
Olking

---

