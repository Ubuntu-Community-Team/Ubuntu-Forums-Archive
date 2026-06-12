---
title: "Kubuntu 11.04 plymouth problems (nvidia)"
date: 2011-09-29
forum: Hardware
---

### Post by khaos1 on 2011-09-29
Hi guys
I've just installed kubuntu 11.04 (clean install) in my laptop: Sony VAIO VGN-FZ31Z. It has nVidia GeForce 8600M GS GPU for gfx card.

My only problem is the plymouth and the drivers.

After the grub menu the background (blue) screen remains without showing "Kubuntu" logo and progress bar. When I logged in I enabled this driver: nvidia accelerated graphics driver version current Recommended

After the reboot in the settings menu for restricted drivers says: " this driver is activated but not currently in use " !!!
and the plymouth is not fixed.

Also I've tried the other options in the restricted with no luck. I searched some old solutions for plymouth (older kubuntu/ubuntu versions) with no luck.

I must say that in the poweroff/restart the plymouth is working ok.

Thanks for any help

---

### Post by searchfgold6789 on 2011-09-29
Don't worry! your driver is activated, but there is a bug that somehow lets the Additional Drivers program show that it's not activated when it is.
As for plymouth, I'm having the same problem, I just didn't know that it was a problem! Can't help you there.
 - search

---

### Post by Redblade20XX on 2011-09-29
Can you try this? I had the same problem and it fixed it. :P

[http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/](http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/)

- Red

---

### Post by khaos1 on 2011-09-29
No the link above didn't worked for me.
But I found a solution. I installed startupmanager (it requires some gnome packages) and I changed the resolution/mode only and after that the plymouth is ok ;-)

Try it...

---

