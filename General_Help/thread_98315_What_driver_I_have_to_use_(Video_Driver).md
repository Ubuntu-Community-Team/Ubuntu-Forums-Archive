---
title: "What driver I have to use? (Video Driver)"
date: 2005-12-02
forum: General Help
---

### Post by Ruso on 2005-12-02
I have laptop DELL Latitude CPx 
And my video card is 
"VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)" 
I think I have the on board version but I am not sure. 
Right now I have vesa driver installed, but it working very slow, so what driver I have to use to be able to get better performace?

I tried to install the last ATI driver for onboard video cards but without any favorable result :(

---

### Post by kb00heda on 2005-12-03
You already tried to install

   xorg-driver-fglrx
   fglrx-control

as I understand it (the latter is just a control panel). It may be you also have to change some settings in file

   /etc/X11/xorg.conf

as root (or via 'sudo'). Under 'Section "Device"' see to it that it reads

   Driver          "fglrx"

I believe this option may need to be manually set (probably it reads "vesa" right now). If this is not altered you will not use the newly installed driver even though it is there (so-to-speek).

Otherwise have a look at

   [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

under Question

   4.3.	How do I install the 3D ATI video card driver?

Also: 

After installing the ATI drivers try to check the availability of 3D acceleration by typing

   glxinfo | grep rendering

in a terminal. The outbut ought to be

   direct rendering: Yes

Perhaps you already tried all of this... and in that case I'm sorry I was of little help. My laptop (Acer Ferrari 3000 with an ATI Radeon 9200 graphics card) used a driver called "ati" per default --- it came, e.g., with 3D acceleration out-of-the-box. However, I later installed ATI:s own, i.e., "fglrx", anyway.

Good luck!

---

### Post by JoshuaRL on 2007-12-28
Sorry dude, that advice wont help you.  In fact, it probably hosed your Xorg.

For the Rage Mobility you can't use fglrx.  It doesn't support any but the newest laptops unfortunately.  Try to use the following to configure xorg.conf correctly:

[CODE
sudo dpkg-reconfigure xserver-xorg
[/CODE

You'll need to us the DRI driver "ati."  Believe me, I'm trying to configure one right now and that's the only one that works.

---

