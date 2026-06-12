---
title: "[SOLVED] Lenovo X60 Tablet - Install"
date: 2008-06-23
forum: Hardware
---

### Post by bonfire89 on 2008-06-23
So, every now and then I try and start using linux again, it's the summer, I'm off school and actually have time this time around so I figure I will try again.

I have installed the latest Ubuntu 8.x.

Works pretty good out of the box, but not good enough.

I recall there is some sort of thinkpad package that I can install that should do everything for me? Could someone point me in the right direction please?

Right now these are known issues I'm having:
  Full tablet functionality does not exist

  When running an external monitor, the cursor moves extra fast relative to the stylus so that when I go from one extreme bound of the tablet screen to the other I will cover the in entire distance of the two displays. I would like it to only remain on the tablet screen.

  It would be nice if I could get the rotate button to work



I think, instead of focusing on one program at need to look at this as completing the install in general since I think I'm missing a lot.

I can likely benefit from drivers, packages and a xorg.conf file



Thank You

---

### Post by djvonfunkin on 2008-07-03
Hey welcome, I have an X60 tablet and have been using it in ubuntu 8.04 for a few weeks.  My tablet is working great for the most part (although I found this post looking for a way to get the rotate button to work...). I've attached my xorg config, although you probably just need the wacom related stuff in there.  My touchscreen doesn't work, if you have the multitouch model like mine.  I think it may with the newest linux-wacom installed instead of the ubuntu wacom-tools but when I tried that the pen stopped working so I gave up. In anycase make sure wacom-tools is installed in synaptic package manager.  I can't remember if it was already installed in mine or came with the Ubuntu Studio Packages I installed but if you don't have it get it and your pen should work great. I've been drawing in inkscape and the gimp, and installed artrage in wine and using cell writer as a windows "tip" replacement.

I'm still new to linux myself so I don't have all the answers. I don't know of any thinkpad package, there is kthinkbat a battery monitor program for kde (I'm using gnome) and the thinkpad acpi stuff that should've been detected automatically.

These sites have been invaluable to me, but none of it does it automatically for you :):

[http://luke.no-ip.org/x60tablet/](http://luke.no-ip.org/x60tablet/)
[http://www.thinkwiki.org/wiki/Category:X60_Tablet](http://www.thinkwiki.org/wiki/Category:X60_Tablet)
[http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption](http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption)
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)
[http://www.krizka.net/2008/02/13/thinkpad-x61-tablet-automatic-screen-rotation-under-linux/](http://www.krizka.net/2008/02/13/thinkpad-x61-tablet-automatic-screen-rotation-under-linux/)

I'm trying to figure out the rotate button now, it seems to be a matter of assigning the rotate button keycode 0x6c to run a script like "#!/bin/sh
xrotate +

but I'm pretty sure I need to rotate the cursor stylus etc as well but I haven't found the exact lines yet.

best of luck,

Devon

---

### Post by bonfire89 on 2008-07-04
woa, thank you for the reply!

At this point I have screwed things up on this install pretty good so I'm going to go for a fresh install pretty soon, and that point I will check all those links closely.

I will give updates as they come.




edit:  I didn't see anything in your config file about which screen the stylus should work on. Have you tried using the stylus with an external monitor? That is my greatest concern at the moment.

---

### Post by TheCarNinja on 2008-08-06
I have an X61 Tablet running Hardy 8.04 and I've pretty much got everything working. The links above are more or less what I've used and while its time consuming it is possible to have everything working. 

Right now the only problem I'm having is that my brightness is not quite right and my battery meter is messed up (though I can get an accurate one with PowerTop). It resets to half brightness and while I can change it to max again it seems to keep doing it. I haven't had time to play with it yet, but those are basically the only things that isn't working on my tablet. Btw on 7.10 it all works. 

Fingerprint works, bluetooth, wifi, tablet rotation, tablet buttons... etc etc all work for me.

---

### Post by iggyiguana on 2008-08-27
djvonfunkin, thank you so much for posting your xorg file. I installed Ubuntu gutsy on my X60 tablet a week or so ago and I had no tablet functionality whatsoever. I tried editing my xorg.conf manually with bits and pieces of info I've found on the interwebs and nothing seemed to work in my favor. Finally I found this post and decided to use your xorg.conf and now everything works. Thank you so much!

---

### Post by dieudo on 2008-11-19
> **djvonfunkin said:**
> [...]

best of luck,

Devon

Thanks a lot ! It works :)

---

