---
title: "[SOLVED] Update today broke my desktop"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by CoolHand on 2008-12-16
The latest udates today just installed on my PC.  I have two identical systems so when the first broke I didn't update the other.  Symptoms are this:  I can't move windows on my desktop.  Keyboard isn't working once logged in.  Firefox seems to cause some sort of CPU run.  The scroll wheel on the mouse does funky stuff.  Basically the system is unusable.

It worked fine until the latest updates 10 min ago.  I am running 8.10.  The latest updates seem to have installed 32 packages:

bind9-host console-setup dnsutils gnome-power-manager jockey-common jockey-gtk libbind9-40 libdns43
  libisc44 libisccc40 libisccfg40 liblwres40 libnm-glib0 libnm-util0 libpulse-browse0 libpulse0
  libpulsecore5 libshout3 libx11-6 libx11-data libx11-xcb1 network-manager network-manager-gnome ppp
  pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-utils ubufox xkb-data

Which is the most likely culprit and how do I roll it back to the previous package version?  I'm guessing one of the X11 packages.  Any help?

Thank you.

---

### Post by CoolHand on 2008-12-16
Well I fixed it before I got an answer.  Something wrong with the X11 update as I suspected.  Downgraded using the following commands and all is well.

On my good box I ran to find out the version numbers:
dpkg -l | grep libx11
Version was 2:1.1.5-2ubuntu1

On broken box I ran:
sudo apt-get install libx11-6=2:1.1.5-2ubuntu1
sudo apt-get install libx11-data=2:1.1.5-2ubuntu1
sudo apt-get install libx11-xcb1=2:1.1.5-2ubuntu1

Which downgraded one version and now everything is working again.

Thanks anyway.

---

### Post by coffeecat on 2008-12-16
I'm sure I haven't had that number of updates today or even recently. You haven't [enabled the proposed updates repository]("http://ubuntuforums.org/showthread.php?t=899262"), have you? If you have, be aware: it's bad for your systems' health. :wink:

---

### Post by CoolHand on 2008-12-16
Thanks for the sanity check but I just verified it.  I am not getting the proposed.  Just the standard updates.  Oh well...it was a very minor X11 update from the description and the version only added a .1  I know I will be blocking that update until I see another version.

---

