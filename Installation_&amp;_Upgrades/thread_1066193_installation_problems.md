---
title: "installation problems"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by sumsa on 2009-02-10
I've tried to install both the 64 bit version of ubuntu and kubuntu on my new 64 bit system. when i boot up and choose install or live, I only get a white screen. after about ½ hour i rebooted back into vista64

next i tried to install ubuntu from within windows using the "windows install feature". when I reboot and choose ubuntu on the bootup menu i somehow end up in a crippled terminal called something like DOS4.

lastly i cant use the remove program for ubuntu in vista, it simply fails to launch.  

my system specs are:
Intel Corei7 920 
Asus P6T Deluxe x58
6gb ram

do any of you have any ideas or am i stuck in a world of windows?

---

### Post by avtolle on 2009-02-10
Do you know the identity of your graphics card? If so, post that so someone can give you some assistance.

---

### Post by sumsa on 2009-02-11
the graphics card is a Asus AMD HD4870

---

### Post by avtolle on 2009-02-11
IIRC, that is a type of ATI card. It sounds like you are being dropped to a command line. I need to do some looking around, as I don't have that particular card myself.

---

### Post by avtolle on 2009-02-11
What I suggest is to download the alternate cd iso from [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate) so you can install without the conflict with the graphics card. When the system restarts after installation, it will (hopefully) start up in low graphics mode which will get you to the desktop, where you can then install the restricted driver for your card.

Alternatively, as you already have the Live CD, you can select "Install in low graphics mode" (or words to that effect), accessed by F6, I think, from the main installation menu. The object here is to get around the issue with the graphics card by using an open-source generic video driver. Then, again hopefully, you can get to the desktop and get an appropriate driver installed for the card.

There are threads, which in my hurried scan of things, discussing how to disable desktop effects from the command line, which could also get you along further. 

My first recommendation is to use the alternate cd for installation, however. Good luck.

---

### Post by avtolle on 2009-02-11
One last thing: to uninstall Ubuntu from Vista, see [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?) for some information.

---

### Post by sumsa on 2009-02-11
Thank you avtolle

I'll give the alternate CD a spin

---

