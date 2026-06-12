---
title: "Bad screen flicker"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by dajasc on 2009-03-01
Trying to help a friend make the switch to Ubuntu is not going as smoothly as I would have hoped.  Immediately upon install everything is fine.

To enable the desktop effects I installed the resitricted driver "fglrx". The motherboard has ATI HD 3100 integrated graphics.  Upon restarting X there was horrible screen flickering and jttering.  I could barely look at long enough to unistall the fglrx driver.  After restart everything is fine.

After what to me at least was a long and painful process of downloading and making a debian package of the latest driver from ATI's site the result was exactly the same.

Ok, so obviously this is a problem that ATI needs to resolve with their closed-source driver.  Here's my question, is there any way to get desktop effects working with an open source driver or not?

---

### Post by WatchingThePain on 2009-03-01
No apparently Compiz does not work with the open source driver.
I gather that from reading other threads.

---

### Post by martino2k8 on 2009-03-01
Did you try 9.2/9.1? My flickering issues were solved with those, although I do run KWin as opposed to Gnome/Compiz (however as I recall some of the issues were nearly identical).

---

### Post by dajasc on 2009-03-01
Yeah I tried the most updated Catalyst drivers directly from ATI's site.

---

### Post by heiowge on 2010-10-15
I'm having similar issues.  I have an ATI card (came with the machine).  It worked ok under 10.04, but is awful under 10.10

There is no compiz at all and the screen flickers about every 3-4 seconds.

I have all the ATI drivers installed that are available in the repositories, with no success.

I tried to install the ones from the ATI site, but they failed to work (initially because their instructions are out of date and don't match filenames, later because they crash mid-install).

I have been forced to use win7 all week while I wait in the hope that there will be an update for 10.10 soon.  If there isn't an update fixing it by tomorrow, I'm going to have to reinstall 10.04 before win7 gives me a complete headache.:(

---

