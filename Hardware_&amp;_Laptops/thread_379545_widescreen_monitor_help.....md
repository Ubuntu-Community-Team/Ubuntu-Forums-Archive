---
title: "widescreen monitor help...."
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by atflegenheimer on 2007-03-08
Hello,

Just set up my PC, installed ubuntu and have a widescreen xerox monitor (XM3) and nVIDIA GeForce 6150 mother board, problem is everything is looking stretched on the screen, ie not widescreen. 

i'm new to ubuntu but have run the nVIDIA thingy ubuntuguide.org (which now seems to be down!) that sorted out things like scrolling, but it's still not giving me teh option to set the resoluition to 1440x900, which is the resolution of the screen. as a result everything is looking fat.....any ideas...??

---

### Post by rjfioravanti on 2007-03-08
You may need to manually enter those values into xorg.conf

[CODE}
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
[/CODE]

Then go down to the 'Screen" section and add those values you want into each Display subsection

Then restart xserver by hitting ctrl+alt+bkspace

---

### Post by atflegenheimer on 2007-03-08
cheers mate - that did the job. i'm slowly getting the hang ubuntu after years of windows....great once you work stuff out.

---

