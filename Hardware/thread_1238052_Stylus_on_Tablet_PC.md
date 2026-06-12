---
title: "Stylus on Tablet PC?"
date: 2009-08-12
forum: Hardware
---

### Post by snakeman21 on 2009-08-12
Hi all!  My wife and I are both running Jaunty, and she has a Gateway TA6 tablet PC.  I was wondering if anyone knew how to make the "pen" work.  I found some other threads about this, but none for her particular model.  I tried some of the solutions anyways, but most were old and involved editing sections of xorg.conf that don't even exist anymore in that file... The one I found that I could try only resulted in Ubuntu getting stuck in safe graphics mode until I undid my changes and restarted... And ideas?

---

### Post by Favux on 2009-08-12
Hi snakeman21,

We tried to make a fpit.fdi file but couldn't get it to work.  So no HAL/.fdi at this point.  You can get it working through the xorg.conf.

Basically you need to install the Finepoint driver through Synaptic Package Manager.  Search "fpit"

Here's a thread where we thrash around before finally getting it to work:  [http://ubuntuforums.org/showthread.php?t=1221288](http://ubuntuforums.org/showthread.php?t=1221288)  Xorg.conf's are scattered through it.

Hard to tell if the reinstall was the key, eliminating some previous configurations left around that were interfering or if the key was adding the serial line to "/etc/rc.local".  Maybe you can tell us.  Anyway the "key" wiki:  [https://help.ubuntu.com/community/FujitsuStylus](https://help.ubuntu.com/community/FujitsuStylus)  and a more notebook specific wiki:  [https://wiki.ubuntu.com/LaptopTestingTeam/GatewayCX2618](https://wiki.ubuntu.com/LaptopTestingTeam/GatewayCX2618)

Hope this is helpful.

---

