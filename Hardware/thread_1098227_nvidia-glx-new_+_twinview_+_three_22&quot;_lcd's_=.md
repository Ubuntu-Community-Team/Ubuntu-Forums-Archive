---
title: "nvidia-glx-new + twinview + three 22&quot; lcd's = pooooor performance"
date: 2009-03-16
forum: Hardware
---

### Post by ihod on 2009-03-16
Heya everyone. Recently switched to Kubuntu from openSUSE and i gotta say, i like it alot. Adept alone is enough to win me over, its ease over YaST is amazing.

OK enough of my glorifying and down to business. In my system are two NVIDIA 8800 GTS's and connected to them are three 22" LCD's. At first i was using the (opensource?) drivers available on NVIDIA's website. Version 180.x. Certain applications are laggy for example Firefox scrolls like crap and i can see lines drawing while using Kaffeine. Same symptoms with SUSE and i don't care for it but im used to it so w/e. I decided i wanted to try to run World of Warcraft under wine since it seems so easy (or so i thought) to do. So i went through the process of installing wine, wow, etc and low and behold it doesn't work! Its complaining that it cant find GLX: 

Major opcode of failed request: 142 (GLX)
Minor opcode of failed request: 3 (X_GLXCreateContext)
Serial number of failed request: 14
Current serial number in output stream: 15.

So having that issue i realized that i needed to install the restricted driver with the restricted driver manager and did so. So wow works now (yay right?) but to my annoyance, i now feel like im running with a Pentium 4 and an FX5500. Firefox hangs up like mad, dragging windows across the screens leaves trails and KDE itself just lags.

So i was thinking, there has to be a couple solutions to this problem. Ultimately I would like to run the latest NVIDIA drivers (180.x) and somehow have WoW find the GLX its looking for, or maybe the poor video performance can be fixed with a refreshing of my xorg.conf file. To be more specific: is there a way to point WoW (wine specifically) to the GLX drivers that 180 provides &/or is there any additional lines i could add to my xorg.conf...

To view my xorg.conf, just travel here: [http://bellancomputer.com/xorg.txt](http://bellancomputer.com/xorg.txt)

Thank You!

~IHOD

---

