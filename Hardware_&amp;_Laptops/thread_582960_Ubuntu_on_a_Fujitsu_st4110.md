---
title: "Ubuntu on a Fujitsu st4110"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by hoborocket on 2007-10-20
I'm about to buy a Fujitsu tablet, and wanted to know what installing Ubuntu on it will entail. I found [_this guide_](http://home.comcast.net/~calkinsc/fujitsu_st_4000.html) but it's written for 5.10, and not entirely comprehensive, so I'm not sure what may have changed since then that's relevant to me.

I know I will need an external keyboard to do setup, and either a USB CD drive, or a bootable USB drive. I also heard the pen might take some doing to get working.

I also don't know if some of the stuff XP tablet does carries over, like rotating the screen 90 degrees for portrait mode. Is there a special tablet edition I might need? Or just some extra packages, like an onscreen keyboard?

---

### Post by vemon on 2007-12-12
I also have one of those and am going to install Ubuntu 7.10 on it. I also found two other pretty short guides on the subject (the one that describes a Ubuntu install also tells that it's possible to use xrandr to rotate the screen):

[http://www.mjmwired.net/resources/mjm-fujitsu-tablet-suse.html](http://www.mjmwired.net/resources/mjm-fujitsu-tablet-suse.html)
[http://offtopic.org/twiki/bin/view/Main/GadgetTabletST4110](http://offtopic.org/twiki/bin/view/Main/GadgetTabletST4110)

I'm planning to put my stylistic in the bedroom for watching movies & playing music using freevo (it would stream the stuff from my home server). It's perfect for it since I have the docking station which can be placed on a bedside table.

Have you had any luck with your install yet? I'll report here when I get my toy up and running with Ubuntu Gutsy.

---

### Post by vemon on 2007-12-17
I just tried to install Gutsy using the docking stations CD/DVD drive but with no luck. The drive seems to work at boot very randomly even though "Boot from optical" is enabled and first in the boot order. Out of twenty boots I only managed to get the cd-installer started once. The problem may lie in the connections between the tablet and the docking station.

Next step for me will be installing through PXE (booting via ethernet network). I've done that before to a laptop without a CD drive and it worked nicely.

I'll post back when I have results :)

---

### Post by cowbaka on 2007-12-18
I have a st4120 and installed 7.04 from one of the live CD's (the ones that will boot the OS without installing).  It installed fine, but I never could get my wireless working - it was detected, just didn't ever connect to my router (plugged into ethernet).  I had lots of trouble getting updates (namely video codecs).  I did get screen rotation working, although the touchscreen would not always work after rotating (registered up as left, etc).  Anyway, I had no problem with the installation - but I booted from a Firewire external CD, not USB.

However, I had big big problems with 7.10 - I actually tried to install it first, and it gave me a black screen with white bars on it when it booted.  This happened again when 7.04 wanted to upgrade to 7.10 (which it told me it had to do in order to get my video codecs downloaded).

---

### Post by vemon on 2007-12-19
cowbaka: At which point did your screen turn black w/ white bars? Right after booting the install cd or after it was installed? And did you try disabling bootsplash/framebuffer? Did it ever reach the gnome desktop?

I haven't installed mine yet but it'll be easier if I know what to expect :). I was able to run the live cd once using the docking stations cd drive but it just jammed after approximately 2 minutes of booting. This could've also had something to do with the fact that my docking station not working properly. I didn't get the black screen w/ white bars. The boot splash (screen w/ boot progress bar) appeared normally but at some point I just got black screen and nothing happened anymore.

---

### Post by nor02744 on 2007-12-20
> **cowbaka said:**
> I have a st4120 and installed 7.04 from one of the live CD's (the ones that will boot the OS without installing).  It installed fine, but I never could get my wireless working - it was detected, just didn't ever connect to my router (plugged into ethernet).  I had lots of trouble getting updates (namely video codecs).  I did get screen rotation working, although the touchscreen would not always work after rotating (registered up as left, etc).  Anyway, I had no problem with the installation - but I booted from a Firewire external CD, not USB.

However, I had big big problems with 7.10 - I actually tried to install it first, and it gave me a black screen with white bars on it when it booted.  This happened again when 7.04 wanted to upgrade to 7.10 (which it told me it had to do in order to get my video codecs downloaded).

Is your wireless working now? I have E-series and I have struggled with the wireleess connection without success.

---

