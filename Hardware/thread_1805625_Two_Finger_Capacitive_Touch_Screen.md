---
title: "Two Finger Capacitive Touch Screen"
date: 2011-07-16
forum: Hardware
---

### Post by mightybuddha on 2011-07-16
Hi Everyone,

hope you can help. 

I'm using a Dell Mini 9 with Ubuntu 11.04 and have just installed a 2 finger capacitive touchscreen from visualtouchworld.com

The netbook had xp installed on it initially and the touchscreen wouldn't work at all.  I contacted the seller and NOW HE TELLS ME that it is only compatible with Windows 7 :mad:

I was going to stick ubuntu on this machine anyway so installed Natty and presto!  The cursor moves when I touch the screen!  So it looked like it was working, but then soon found that it wasn't working properly.  

**The problem is it is constantly (repeatedly) clicking when I touch the screen so if I click on terminal, for example, it brings up half a dozen terminal windows and it is impossible to drag windows or scroll.**

Could anyone give me some advice on how to troubleshoot this problem?

Many thanks!!!!

---

### Post by mightybuddha on 2011-07-16
after doing some research on the controller, it appears to be an 8.9" Pixcir Projected Capacitive 2 Finger Touchscreen

if that helps :) can't find any info related to this touchscreen on Ubuntu, or a similar bug on Ubuntu, though an identical problem was found using MeeGo with this touchscreen  [https://bugs.meego.com/show_bug.cgi?id=10887](https://bugs.meego.com/show_bug.cgi?id=10887)

---

### Post by mightybuddha on 2011-07-17
just tested the screen on Windows 7 and it works perfectly :(

Any ideas how I can get it working properly on lovely Ubuntu? or where to begin?

---

### Post by mightybuddha on 2011-07-21
bump? :(

---

### Post by jooaik on 2011-07-23
i used Prolink Tablet to try out how good Ubuntu 11.04 works on touch screen system without any keyboad.
[http://www.prolink2u.com/new/products/index.php?cid=283](http://www.prolink2u.com/new/products/index.php?cid=283)

It was not a good experience. The touch works, I installed
the gnome on-screen keyboard too. everything works well, but
the touch experience was less than desired. 

i had my screensaver on, and would require password to get back.
The on-screen keyboard could not automatically pop up when I touch or "click" on the password box. 

If anyone could help me will be great.

---

### Post by bmullan on 2011-08-04
> **mightybuddha said:**
> after doing some research on the controller, it appears to be an 8.9" Pixcir Projected Capacitive 2 Finger Touchscreen

if that helps :) can't find any info related to this touchscreen on Ubuntu, or a similar bug on Ubuntu, though an identical problem was found using MeeGo with this touchscreen  [https://bugs.meego.com/show_bug.cgi?id=10887](https://bugs.meego.com/show_bug.cgi?id=10887)

Here is a helpful Blog on using Ubuntu with either the WeTab or ExoPC tablets (both are the same HW made by a division of ASUS called PegaTron).

Pay attention to the several sections where he discusses "twofing".

[http://wetabz.blogspot.com/](http://wetabz.blogspot.com/)

---

### Post by mightybuddha on 2011-08-09
> **bmullan said:**
> Here is a helpful Blog on using Ubuntu with either the WeTab or ExoPC tablets (both are the same HW made by a division of ASUS called PegaTron).

Pay attention to the several sections where he discusses "twofing".

[http://wetabz.blogspot.com/](http://wetabz.blogspot.com/)

thanks, though I'm not sure if that applies :( the problem isn't that it's double clicking instead of single clicking.  The problem is that it is constantly, and rapidly, clicking when the screen is touched.

made and interesting discovery though... **it doesn't happen if I touch the screen with two fingers** (instead of one)... for example if I touch the top bar of a window using two fingers I can drag the window around, but with one finger it is impossible to drag since it is constantly clicking.  

don't know if that offers any kind of clue to the solution?

---

### Post by mightybuddha on 2011-08-10
still struggling with this.... reinstalled ubuntu but with maverick 10.10 this time so i could try enac.fr's hid-multitouch drivers, but can't get them installed :/

everything goes fine though when i get to **make** the terminal ouput is :

mike@mike-Inspiron-910:~/hanvon/drivers$ make
/bin/bash compile.sh
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/mike/hanvon/drivers/drivers/hid/hid-core.o
/home/mike/hanvon/drivers/drivers/hid/hid-core.c:1383: error: &#8216;USB_VENDOR_ID_STANTUM_STM&#8217; undeclared here (not in a function)
/home/mike/hanvon/drivers/drivers/hid/hid-core.c:1383: error: &#8216;USB_DEVICE_ID_MTP_STM&#8217; undeclared here (not in a function)
/home/mike/hanvon/drivers/drivers/hid/hid-core.c:1384: error: &#8216;USB_VENDOR_ID_STANTUM_SITRONIX&#8217; undeclared here (not in a function)
/home/mike/hanvon/drivers/drivers/hid/hid-core.c:1384: error: &#8216;USB_DEVICE_ID_MTP_SITRONIX&#8217; undeclared here (not in a function)
make[2]: *** [/home/mike/hanvon/drivers/drivers/hid/hid-core.o] Error 1
make[1]: *** [_module_/home/mike/hanvon/drivers/drivers/hid] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [drivers/hid/hid-multitouch.ko] Error 2


any ideas where i'm going wrong? :(

cheers!

---

### Post by Interruptor on 2011-11-24
Is it still the case for 11.10?

---

