---
title: "Video Card &amp; Wireless Networking..."
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by mitchmaster on 2007-06-10
I have an ATI X300SE video card and I installed the drivers from ATI by going... sudo sh /home/mitch/ati.run...
and... Now it wont let me log in!
It gets to the login screen of ubuntu (6.10) and i type in my user/password... and the screen flashes and its back at the login screen!
gahhhhhhh
and...
before that i was trying to install drivers for my Atheros wireless network card...
and i have to compile/make them...
But I am not sure how to do that and the instructions with it werent very clear...
If someone knows how to fix these things that would be greatly appreciated!

---

### Post by 444 on 2007-06-10
You shouldn't have to compile the Atheros drivers. They should be there already, or be readily downloadable from 'Add/Remove...'.

Hit Ctrl-Alt-F6, login at command prompt, type 'sudo nano /etc/X11/xorg.conf', hit Ctrl-W to do a text search, look for '   Section "Device"  ', scroll a few lines down to what'll probably say 'Driver     "fglrx"  ', change that to ' Driver    "vesa" ', hit Ctrl-O to save, reboot. That should enable basic 2d support.

---

### Post by mitchmaster on 2007-06-10
I can't really connect to my network without the wireless device working ^^
I'll run my big long ethernet wire though... lets hope my network card works.

Any idea what might have caused the ATI drivers to go wacko? lol

Mitch

---

### Post by 444 on 2007-06-10
linky [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=restricted-modules&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=restricted-modules&searchon=names&subword=1&version=edgy&release=all)
Use 'uname -r' command to see which one to get.

Copy it via usb drive?

ATI... dunno, I avoided installing the driver...

---

