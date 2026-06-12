---
title: "Xubuntu + laptop = no external display"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by Hexydes on 2007-10-09
When I start up my laptop, if I have the external 17" CRT monitor plugged in, and close the lid on the laptop, I get the BIOS, Xubuntu loading screen, etc. However, before the login screen comes up, the external display goes blank. I can't find any settings for saying "force to external display". I don't much care how it does it (clone, extend, etc), because the lid will be closed. I'm using the display as a "TV" monitor, so I only open the lid to power it on and from there I don't need it.

Any ideas on what's up? It is an old laptop, with an old ATI Rage integrated chipset or something in it. I think I set it to use the 'ati' driver in xorg, though I'm not 100% on that one.

Thanks!

---

### Post by mazy haze on 2007-10-09
Same with me. But I'm using KDE. Got this problem both with Edgy and Feisty on my laptop and my desktop PC (both of them aren't old at all). There actually is an option in the graphical system configuration tool to anable mulitscreen, but it somehow did not work. I guess it would work if you add a second screen in xorg.conf, but I haven't tried this one yet, since I was using a video projector and just used it instead of my PC's monitor, however I tried the multiscreen feature first on both computers. By the way: Both have Nvidia GeForce.

Update: Working fine with nvidia-settings. ;)

---

### Post by Hexydes on 2007-10-09
Not for me. :(

I'm sure this would probably work in Ubuntu. I really respect Xubuntu for what it is (and it runs really quickly!), but missing networking in the file manager, and not having some advanced settings like support for external monitors out of the box sucks.

Anyone have any ideas on how to get this working?

---

### Post by Hexydes on 2007-10-10
Seriously? Nothing? :(

---

### Post by Hexydes on 2007-10-11
It's hard for me to imagine that NOT ONE SINGLE PERSON has run into this issue before...

---

### Post by bapoumba on 2007-10-15
I am running in right now..
If I restart X with a video-projector connected, the laptop screen is out. That is the best I could find for now. I do presentations with Openoffice, and it is quite inconvenient not to be able to clone the desktop with the Fn keys (that used to work with GNOME). I've searched quite extensively, I'm running Xfc on gutsy with the nVidia restricted drivers for my old GeForce. Hmm..

---

### Post by PmDematagoda on 2007-10-15
As you use an Nvidia, it would be easy for you bapoumba, but not for Hexydes as he uses an ATi card.

Your biggest obstacle, Hexydes, is your ATi card, it may be difficult to achieve what you are trying to do unless you do a serious bit of tweaking.

---

