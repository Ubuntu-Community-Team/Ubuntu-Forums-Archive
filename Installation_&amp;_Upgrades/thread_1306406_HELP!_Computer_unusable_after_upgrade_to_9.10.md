---
title: "HELP! Computer unusable after upgrade to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by tammer on 2009-10-30
I performed an upgrade from my 9.04 installation today, and after restarting my laptop boots fine, but once the X server is loaded the screen is a complete graphical-glitch mess. The cursor appears normal, but the rest of the screen below it is a bunch of static/glitches.

I've tried commenting out each section of my xorg.conf one by one, and nothing changed. Please give me a direction to go! I can switch to a separate terminal screen and access the computer that way, but the X server is unusable.

I have a Thinkpad X31 which uses an ATI Mobility Radeon M6 LY for graphics. I'm not even sure where to start figuring this out, any help is greatly appreciated!

---

### Post by tammer on 2009-10-31
OK, I've isolated the problem. After a reformat and reinstall, everything was working well until I enabled metacity compositing. This completely breaks karmic, in that all I have afterwards is a cursor over garbage.

To make matters worse, I've been using the Metacity compositor due to the fact that using Compiz on my setup in 24 bit color depth (not 16, for some reason) causes the same problem. (Although, the actual garbage looks different. See my thread here for the full problem: [http://ubuntuforums.org/showthread.php?t=1266576](http://ubuntuforums.org/showthread.php?t=1266576))

So yeah, can anyone can help me figure out what's wrong with the Metacity or Compiz compositors?

---

