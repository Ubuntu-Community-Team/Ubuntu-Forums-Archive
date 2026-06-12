---
title: "Nouveau on Karmic - only every other boot!"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by homunq on 2009-11-06
When I initially upgraded to Karmic, I had BOTH NVidia (binary) AND nouveau drivers running (!) according to "system:Hardware Drivers". I considered that a problem and turned them both off, hoping to reboot and turn just nouveau on. On reboot, I had no X - just some random crap on my screen until I dropped to the terminal. I messed around. If I tried to use the nvidia drivers, I'd get the flickering (or, with kdm, a cleaner unflickering fail). Eventually (as root)

mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf #has vesa driver
apt-get remove nvidia*

(of course, I'd previously gotten
apt-get install xserver-xorg-video-nouveau
to work - I had to fix dkms to get it to install correctly, I think I had it wedged from earlier)

... got me booting with just the vesa driver. Then, I could go into "Hardware drivers" and enable nouveau, and it would immediately start to work with acceleration.

BUT - on reboot, the acceleration is gone. I have to turn off nouveau, reboot (to make it really turn off), and turn nouveau back on, in order to get it to work again. Then it works until the next reboot.

Can anyone help me figure out why nouveau only loads manually?

---

### Post by DouglasAWh on 2010-01-08
I'd also like to know this.  I'm becoming very frustrated with virtualization on Fedora and would like to move back to Ubuntu, but I pretty much have to have these drivers working for that to be an option.

---

