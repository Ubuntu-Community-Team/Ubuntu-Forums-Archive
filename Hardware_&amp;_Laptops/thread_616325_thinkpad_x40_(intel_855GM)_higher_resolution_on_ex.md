---
title: "thinkpad x40 (intel 855GM): higher resolution on external VGA"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by orangeek on 2007-11-18
Hi all.
I tried almost everything on my x40 (actually with ubuntu feisty, and intel-810 xorg driver) in order to obtain:
- LCD resolution 1024x768
- output on external VGA with a res of 1440x900 (if not possibile, something more than 1024x768)
- possibly I would like to have an extended desktop with (1024+1440)x(768x900) resolution (I think the feature is XINERAMA) or, if not possibile, two desktops aligned in vertical
- if with xinerama, Xorg should recognise if the external monitor is attached and consequently adapt the resolution
- XVideo and openGL (for compiz) capabilities

I installed ubuntu gutsy, hoping for the new "incredible" Xorg configurator, but with no luck: it's also highly instable.
Before of that, I tried with the standard i810 and the 915resolution tool but, in this case too, with no luck.
I read somewhere that the intel chipset on the x40 is somehow limited to a certain resolution but I still don't get if what I ask for is even possible.
I'm pretty confused with xinerama, mergefb, 915resolution and so on...

I would like to ask you:
- if even possible what I ask for? should I give up? please don't tell me that I should...
- can someone share his xorg.conf or something from that I can understand how it works? I searched thinkwiki and googled for that but didnt find anything related.

Many thanks,
orangeek

---

### Post by tact on 2007-12-03
Hi there...

I am using a Dell D410 laptop that has max 1024x768 resolution on the LCD and I connect it (via a "media base" docking station) to a Dell 19" external LCD monitor with max res 1280x1024

The new xorg seemed able to auto configure for each situation (internal LCD or external) but just as Gnome was starting the external LCD would flick from 1280x1024 into 1024x768.   After the desktop finished loading I would have to System>Admin>Screens and Graphics then change resolution manually back to 1280x1024

Then....  I found that if I change this key in gconf  /desktop/gnome/screen/default/0/resolution from 1024x768 to 1280x1024 things worked nicely.

When in the dock using the 19" external monitor gnome stays in 1280x1024.
When out of the dock and using the laptop LCD screen (despite the default set higher) gnome boots nicely as 1024x768

---

