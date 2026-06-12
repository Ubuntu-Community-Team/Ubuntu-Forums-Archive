---
title: "Dell Dimension E310 install hang"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by Gregoyle on 2006-02-03
Hello all, this is my first post here so of course it's going to be begging for help :-).

I recently bought a Dell Dimension E310 and have been having trouble installing Ubuntu on it.  The goal is to dual-boot Ubuntu and WinXP.

The trouble is that the install CD does not even finish booting.  This topic is discussed in these other threads that I've found:

[http://ubuntuforums.org/showthread.php?t=88358](http://ubuntuforums.org/showthread.php?t=88358)
[http://ubuntuforums.org/showthread.php?t=93908](http://ubuntuforums.org/showthread.php?t=93908)

and also on this site:

[http://www.stillhq.com/diary/toys/dell/e310/000002.html](http://www.stillhq.com/diary/toys/dell/e310/000002.html)

The upshot is that the Ubuntu installer seems to have trouble with the USB controller on the Dimension E310.  The errors I get are similar to the ones in the first ubuntuforums.org thread.  Then the install boot hangs on:

Starting system log daemon: syslogd, klogd...

and then does absolutely nothing.

Apparently Knoppix installs just fine on the E310, which would suggest that there is something the Ubuntu installer is or is not doing that is causing the trouble.

I'd much prefer to install Ubuntu, so any suggestions of boot options or workarounds would be much appreciated.  I've tried most of the ones listed in the help command.

---

### Post by Gregoyle on 2006-02-04
Update:  I tried Knoppix today, and that does not work either!

I noticed in an update to one of the abovementioned links that the author successfully installed Ubuntu on a Dimension E310 by disabling the onboard USB controller and installing a new one in the PCI slot.  As my system only has two PCI slots and one has a wireless card in it, I would really prefer to use the onboard USB! (yes I have also tried running the installer with the wireless card taken out; it was the first thing I tried :-)).

If anyone has any ideas about how to work around this USB controller problem I would be very grateful.

-Greg

Update:  I just tried Knoppix 4.0.2, and it *does* work.  Knoppix 3.8 did not work.  I'm somewhat relieved because that is actually the first version of Linux I've gotten to work on this system at all.  I'd still prefer Ubuntu.

---

