---
title: "1680 1050 Resolution Problem... Intel Driver"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by Avicus on 2007-09-25
I know this is a major problem for alot of people, and I've scoured google and these forums for a solution.

I'm running Gutsy, using a Viewsonic VG2030wm 20 inch widescreen monitor, native resolution 1680 * 1050. 
My computer is an HP Compaq 5700 Small Form Factor, using an "Intel Corporation 82Q963/Q965 Integrated Graphics Controller" as listed from lspci. 

Many people found solutions using 915Resolution, others using the intel driver or i810 driver. Some have found using modelines in the xorg.conf helped. I've honestly tried all these solutions and nothing is helping... best I can get is 1400 * 1050, I can also get 1600 * 1400, neither of which is ideal.

Strange thing is, when I am able to get the 1400 * 1050 resolution (the best mode I can get yet) the Screen Resolution thing in the Preferences menu says 1680 * 1050, yet it is not as the monitor reports differently and the fonts an lines all look squiggly or blurry.

Even the new gutsy screen resolution thing is out of whack... I'm even able to load the driver disk that came with the monitor and then a reboot makes the xserver screw up and try an autoconfig which completely knocks out my previous settings.

Why does x configuration always have to be a pain in the arse? Can't Ubuntu be the first to get it right? What makes it so hard??? Windows has been doing this correctly for years.

Anyway, can someone wave their magic wand and  help me fix this issue? My skillset is intermediate with linux.

---

### Post by Syke on 2007-09-26
Using the -intel driver is your best bet. What happens when you try that driver and set the resolution in xorg.conf to 1680x1050? Are you using DVI or VGA cable? If you have DVI, try VGA (or vise-versa).

---

### Post by Avicus on 2007-09-26
When using the intel driver, and setting the res to the 1680x1050 value, all that comes up is X in 1400x1050 mode, close but not what I need... and the screen resolution properties in both the old resolution method and the new gutsy resolution app both claim 1680x1050, yet my monitor says 1400x1050... and the resolution is blurry/wiggly, so I believe my monitor. 
I am using vga cable, dvi is not an option for my onboard video.

Thanks for your time, any other suggestions?

---

### Post by Avicus on 2007-09-26
I upgraded from Feisty to Gutsy and am wondering if that's part of the issue... I decided to try Gentoo, but got tired of waiting for the damn thing to install so I burnt a new copy of Gutsy Tribe 5 and am installing that as I type, so I'll see if anything changes...

---

### Post by Avicus on 2007-09-26
Nope, same problem. 1400*1050 resolution, ubuntu claims 1680*1050 but it is not. At least acceleration is working this time, so I get the compiz effects... but I just need the correct resolution. I'll post my xorg.conf and my xorg log tomorrow when I get back to work. Maybe someone has some hints?

---

### Post by Avicus on 2007-09-27
Hmmmm very strange... I came into work today and there was my Gutsy looking perfectly fine, resolution-wise that is. Must have been an update that somehow fixed my issue by itself! Well, I wish I could say I fixed it. Nothing to do now except mark the thread as solved.

---

### Post by Avicus on 2007-09-27
Bah, no compiz effects now... why?!?!?!

---

### Post by Avicus on 2007-09-27
hmmm i think I'm affected by this:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/140833](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/140833)

---

### Post by smileypaul on 2007-11-28
Any solution to this?

I have the G33 chpset running the intel driver. I can't get 1680x1050 .. i can get 1440x900, but as soon as i switch to 1680x1050 , i really get 1280x1024 stretched out really, far..

argh!

---

