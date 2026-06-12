---
title: "fglrx Stopped working this past week"
date: 2009-07-01
forum: Hardware
---

### Post by Psychoscorpic on 2009-07-01
Hi all.

Something changed this past week that broke my 9.6 Catalyst driver in Ubuntu 64bit.
It was working brilliantly, then all of a sudden from Sunday, I couldn't boot. It couldn't get to Log-on screen - all the graphics got crushed up to the top 1cm of the screen, and repeated sideways.

Finally killed & replaced xserver-xorg from Recovery Mode, which removed the ATI drivers with it, and I could boot again. (Remove took 189Mb, replace only put back 15Mb, so I lost all a few other odds & ends like the fast-user-switcher too)
Libraries affected:
   xorg-driver-fglrx
   fglrx-kernel-source
   fglrx-amdcccle
   dkms

Once back in, I added thing missing things one by one, and as soon as I reinstalled the fglrx driver, all went pear-shaped again.

What changed last week that broke this?
Now running with straight Ubuntu driver, so no nice screensavers and no compiz.

---

### Post by cryemoxkidcry on 2009-07-09
apparently ATI does not support a lot of older graphics cards anymore and the proprietary drivers are screwy with Jaunty right now.
In reading a lot of posts with similar problems there were a few fixes for this. You'll either have to use the open source drivers and not have the 3D performance.  use 8.10.  or downgrade Xorg to 1.5.2.
I think I'm going to use Ubuntu 8.10 for a while until things have cleared up.

---

### Post by Psychoscorpic on 2009-07-10
Hi cryemoxkidcry

It is a pain at the moment. Read an article yesterday saying that the Kernel chaps are working on the open ATI 3D driver, but that it is still at least 80% broken and insanely slow. 

Mine is not an old chip - X3100 - and it has worked excellently in Jaunty from upgrade from 8.10 to 9.04 a few days after release until beginning of this month.
All I can put it down to is a sub-component update that must have broken something (I generally let it auto-update once a week if there is something there)

---

