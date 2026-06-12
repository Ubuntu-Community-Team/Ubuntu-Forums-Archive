---
title: "ati driver help (I've already tried lots of stuff.)"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by mtaylor on 2005-08-11
Hello there.  I can't get 3d accelleration to work in ubuntu 5.04

I did a fresh install and first tried installing the fglrx drivers from  the synaptic package manager.
Editing the xorg.conf file allowed me to boot and load fglrx module into memory.  Things would appear to be just fine, booting into X when the system would totally hang (and the screen go black)... This seems to be on a timer.  10 seconds or so; It doesn't matter if i sit at the login screen, or get to the gnome desktop, it always crashes.  Switching the useinternalagpgart ="no" to "yes" allows me to boot with the driver and not crash, BUT I have no 3d acceleration as shown by running fglrxinfo. (mesa is doing my dri)

I've tried disabling 8x support in bios, changing the size of my agp arpreture, which were reccomended for my chipset.  The symptoms have not changed.

lsmod reveals that fglrx and my agpgart modules are both loaded.

video chipset: 9600xt  (R350 AR)  card: Sapphire 9600 ultimate 128M
My motherboard chipset is an nForce2.  I have 1 GB of ram.

this problem appears not to be limited to the distrobution i am using... I have been unable to make it work in gentoo, mandriva 10.2, and ubuntu.

So the last thing I tried made the driver fail in a new and interesting way which appears unrecoverable... under the advice of another thread in the forum, I aliened the rpm from ati and force-overwrite installed it.  Now, the system still hangs.. and it hangs whether or not i have set usinternalagpgart to yes or no.  In fact, it hangs when i revert to using the "ati" driver.  

The last paragraph can be ignored for the sake of helping me out, but it might give some insight to the problem?

I can provide xorg.conf and xorg logs if you'd like, but there doesn't seem to be anything out of the ordinary.

I am fairly competent with linux jargon and use (brought up on slackware), so feel free to give me gory details.

thanks! 

--matt

---

