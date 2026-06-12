---
title: "xorg.conf catalyst 9.4"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by chimaera666 on 2009-04-28
Hi guyz,

can you help me tweaking my settings ? I just installed (again, cuz i messed it up) the new fgrlx drivers from ati (fgrlx 8.602) in jaunty.

i wanted to know what i have to add in my xorg.conf to get the most out of my video card.

I'm currently using Compiz-fusion and cairo-dock and it's all working but i think it can do better.

videocard RadeonHD 3650
fglrxinfo = ok
glxinfo = ok direct rendering yes
glxgears = what should this do ?
compiz-check = something strange it says rendering method is none ?????

If you need additional info please let me know, I'm no expert :-s

---

### Post by hurdy on 2009-04-28
hi there,

how did you get ATI graphics to work with 9.04?

I've just installed update 9.04 via update manager in 8.(something) but my graphics is all screwed up.

I get the scrolling ubuntu loading screen, then crazy graphics and freeze.

Do you do the update via recovery mode command line?

Any advice would be much appreciated.

Thank you.

---

### Post by chimaera666 on 2009-04-30
Hi,

I had the same a while back, my problem was my xorg.conf.
Use the recoverymode and go to the root prompt (or something like that) and type

/usr/bin/aticonfig --initial

reboot and normaly you should be able to login, if not you (maybe your card is not supported by fglrx) will have to remove the fglrx driver and use the standard installed open-source one. Than you can check the ati website and see if the driver works with your card and download the latest catalyst.

remove fglrx

apt-get remove xorg-driver-fglrx

and now back to my question :-)

---

