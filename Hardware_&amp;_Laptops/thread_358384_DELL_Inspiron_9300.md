---
title: "DELL Inspiron 9300"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by tompouce on 2007-02-10
Hi!

I just want to know if theyre a way to make my front buttons work,  my touchpad scrollers and my card reader ?


[http://monitor.si/images/clanki/slika/Dell_Inspiron_9300_1.jpg](http://monitor.si/images/clanki/slika/Dell_Inspiron_9300_1.jpg)

Thanks

---

### Post by banditti on 2007-02-10
To get the Front-Panel media buttons working, it is necessary to map them to the standard XF86-Audio button symbols on X11 startup. 
AThe volume up, down, and mute buttons are handled internally by kmilo (which you might need to install: apt-get install kmilo). 
To have xmms use the play, pause, prev, next, and stop buttons, download and install the appropriate package: apt-get install xmms-xf86audio and then enable it in the xmms preferences.

---

