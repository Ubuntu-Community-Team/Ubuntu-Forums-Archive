---
title: "Need docking/undocking display advice"
date: 2012-11-05
forum: Hardware
---

### Post by P-J on 2012-11-05
Hi all,

I'm trying to setup my laptop (Dell Latitude E4310) running XFCE4 so I can dock and undock it and have the screens adjust accordingly.

As far as I can see, the easiest way to do it should be using 'xrandr'. I've set up a couple of scripts that I attached to hotkeys to run xrandr and set the displays depending on the script I run.

The problem is with the monitor detection. My laptop display is listed as 'eDP1' in xrandr but it only shows up at all if I boot undocked.

If I boot the machine docked, eDP1 doesn't appear at all so there's no way for me to output to it. If I boot undocked, eDP1 is detected correctly and all is well.

So what I'm asking really is advice on how to solve this issue. If there was a way for me to 'force detection' of monitors that might help. Is there any command I could run to rescan connected hardware?

Any assistance much appreciated.

---

