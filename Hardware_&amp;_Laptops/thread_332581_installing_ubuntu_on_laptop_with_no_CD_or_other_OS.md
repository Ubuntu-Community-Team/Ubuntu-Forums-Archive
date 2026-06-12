---
title: "installing ubuntu on laptop with no CD or other OS"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by mistafeesh on 2007-01-06
Hi,

I've just got a laptop through the wonderful freecycle.com. It had been datawiped, so there was no OS on it, which is fine, because I really didn't want windoze anyway!

It's a Dell Latitude CP1 with a P2 mmx 300mhz processor. The rest of the tech specs, I don't know how to find out without an OS...

It has a removable floppy drive, but not a CD drive. It also currently has no network card, although I intend to rectify this soon.

First off, can this computer run Ubuntu, or is it too old?

If it can, how can I get it on there...?

I've already tried whipping out the hdd, sticking into my PC, and installing ubuntu there. It seemed OK throughout startu, but then the X-server crashed, or something. I guess this was probably because the install detected different hardware to when I tried to boot it?

I did read the article [here]("http://www.ubuntuforums.org/showthread.php?t=28948") about how to install without a CD, but it's very complicated!! I'll do that if there isn't an easier method though.

The other option I thought of is a network install. If I buy a network card, then is there an easy way to install over a network?

---

### Post by teaker1s on 2007-01-06
if you did a bios update could you then usb boot an external cdrom drive? Secondly you may find another distribution of linux which caters for older hardware will provide better performance-maybe vector linux or [knoppix]("http://www.knopper.net/knoppix/index-en.html") 
to test it or
 [damm small linux]("http://www.damnsmalllinux.org/")

---

### Post by mistafeesh on 2007-01-06
Does it sound like this hardware is too old for ubuntu? :(

I can't track down a USB CD drive to borrow at the moment. I'll see a couple of mates who might have one tomorrow, so I'll ask around, but it's not too likely... If I can find one, the bios already supports booting from it, I think.

---

### Post by Frogger on 2007-01-06
Congrats!, you already installed it, you need to configure it for your hardware.
With the install from your desktop, go to a terminal (in edgy you will need to press <ctrl><alt><f1>,in dapper it will just go to it), login and type:
sudo dpkg-reconfigure xserver-xorg
Answer the questions and the run:
startx

If that works reboot by typing (in an xterm):
sudo reboot

your system should work after that.

---

### Post by Frogger on 2007-01-06
you will have to tell it "no" when it asks about showing you the outputs of the X server.

---

### Post by mistafeesh on 2007-01-07
Thanks Frogger,

It's up and running now!! If you're ever in North Cornwall, I'll buy you a pint!


Dan

---

