---
title: "OpenGL doesn't work properly after the upgrade to 11.04"
date: 2011-05-27
forum: Hardware
---

### Post by chief_tyrol on 2011-05-27
When I booted up after upgrading my Ubuntu 10.04 laptop to 11.04, the system lagged immensely and the desktop was black (even though I have a wallpaper).
I opened up gnome-system-monitor and saw that "compiz" was using ~90% CPU, even at idle. I opened "CompizConfig Settings Manager," and after disabling almost everything to no effect, I unchecked openGL. At once the system stopped lagging and my wallpaper returned.
Also, if I boot into classic mode, the problems go away. My computer is several years old, so my suspicion is that it is no longer supported. If that is the case, can anyone link me to a good thread with instructions on how to downgrade to 10.04, short of a full system wipe (I've done a fair bit of customization).

System:
   * Ubuntu 11.04 / winXP home
   * Toshiba satellite M45-S2693
* 2GB RAM, 100GB HD, 1.73GHz Intel Pentium M
   * Graphics card: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

---

### Post by coffeecat on 2011-05-27
Hi, and welcome to the forum. Yes, the 915GM chipset is getting old and the stock Intel driver in Natty clearly doesn't work with it properly. However, I've found this thread:

[http://ubuntuforums.org/showthread.php?t=1744284](http://ubuntuforums.org/showthread.php?t=1744284)

The poster in post #5 seems to have found a fix by enabling the xorg-edgers ppa. That's a repository with newer, relatively untested drivers but the Intel one must have been tweaked for older cards. 

You'll see the poster was picked up for their use of aptitude, but their response was incomplete. In fact, aptitude no longer comes in the box with Natty. No matter - if you enable that ppa, you can check/reload in either Update Manager or Synaptic and install any updates which should include the revised Intel driver. No guarantees. I haven't used this myself; I merely found the thread.

If you do need to downgrade, there is nothing you can do short of backup and re-install - sorry.

---

### Post by chief_tyrol on 2011-05-27
Thanks for the info. I tried the ppa and unfortunately it didn't fix the problem, but when I checked the their website it said that the intel drivers had failed to build ([https://launchpad.net/~xorg-edgers/+archive/ppa/+build/2528440]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+build/2528440")), so I'll watch that and see if they manage to fix them.
Until then I'll be using the classic mode.

---

### Post by chief_tyrol on 2011-06-14
**[update]**

They finally released the updated drivers! It still has the problem when I'm on dual monitor, but the display settings/desktop effects/open GL work absolutely smashingly on a single display.
Thank you so much for your help!

---

