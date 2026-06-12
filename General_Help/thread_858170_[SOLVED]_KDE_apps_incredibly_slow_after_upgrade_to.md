---
title: "[SOLVED] KDE apps incredibly slow after upgrade to Hardy Heron"
date: 2008-07-13
forum: General Help
---

### Post by svivian on 2008-07-13
I just upgraded to Ubuntu 8.04 from 7.10, and all my KDE apps (KATE, Amarok) seem to run very, very slowly. Specifically, whenever I switch to a KDE app the interface takes about 10 seconds to display!

Any ideas what's wrong?

---

### Post by svivian on 2008-07-13
Anyone? My system was perfectly fine before the upgrade. I've since turned off all compiz effects (had a few on before that used to work fine)

I'm using the ATI restriced drivers, which I was using before as well.

---

### Post by svivian on 2008-07-13
I've played about with some settings in xorg.conf to no avail. I followed the advice [in this post](http://sudan.ubuntuforums.com/showpost.php?p=3588978&postcount=3) and disabled xgl, though it's still running and using high (up to 100%) CPU at times.

Using a "lighter" KDE theme (classic Windows-like one instead of Plastik) helped a little but there's still a big lag for menus etc.

Anyone have any other ideas to try, or advice about ATI cards? In Hardware Drivers there are three options, all are ticked:
* ATI accelerated graphics driver
* Atheros Hardware Access Layer (HAL)
* Support for Atheros 802.11 wireless LAN cards

---

### Post by tuxxy on 2008-07-13
Not sure what the problem is are you running 64 bit? if so I have had KDE problems, mistakenly thought I should give KDE another try not long ago as it had been a while and thought it deserved atleast a chance and I had at that point not run it on Ubuntu.

After 10 minutes in KDE I realised not much had changed and it seemed even slower than ever, how it cannot run slow on an AMD X2 w/ 6GB RAM is beyond me, anyway I returned to GNOME and thought that would be it but no.  The packages I had installed on the system to use KDE seriously messed up my GNOME, I had problems with graphics, apps not functioning correctly and also system lockups!

I think you can guess what I did next, once all KDE apps were removed GNOME functioned excellent again.

---

### Post by svivian on 2008-07-13
I've solved my problem now, thanks to [http://ubuntuforums.org/showthread.php?t=798556](http://ubuntuforums.org/showthread.php?t=798556) (basically I just removed xserver-xgl).

---

