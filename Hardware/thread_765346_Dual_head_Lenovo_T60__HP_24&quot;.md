---
title: "Dual head Lenovo T60 / HP 24&quot;"
date: 2008-04-24
forum: Hardware
---

### Post by Potatoking on 2008-04-24
Hi

I switched to 8.04 today and tried to get my dual-head setup running... i found round 1000 different how-to's, and nothing seem to work for me.

My T60 is on a docking-station, my hp 24" screen is connected to the docking-station through the dvi port.
The T60-Screen has a resolution of 1400x1050, the HP 1920x1200.

I've an ATI x1400 gfx-card. I tried it both with the restricted and unrestricted drivers...

Is there any hope for that setup?

..PK

---

### Post by Ub1476 on 2008-04-24
You have to use the drivers from Hardware Drivers.

You should be able to adjust screens through this tool:

gksu displayconfig-gtk

Note that the drivers from ATI is very knew and still lack way to many features..

---

### Post by Potatoking on 2008-04-24
Thanks for your help. I just went one big step ahead with this script here [http://www.thinkwiki.org/wiki/Sample_Fn-F7_script]("http://www.thinkwiki.org/wiki/Sample_Fn-F7_script")

With that, I've now a dual-head setup with the right resolution. The only thing I don't like, is that my laptop-screen is still the primary screen (with the bars etc.). It would be nice, to have the bigger external screen as the primary one. Is this possible? If it is... I'm :)

---

### Post by Ub1476 on 2008-04-24
There are settings do so in Screens & Graphics:

gksu displayconfig-gtk

Press alt+f2 for a run dialog.

---

### Post by Potatoking on 2008-04-24
Sorry, I forgot to mention. I saw that in the Screen & Graphics dialog. But it seems, that my external screen isn't recognized there. When I go to the Screen Resolution dialog, I can choose all valid resolutions. But in that Screen & Graphics dialog, there's only 640x480 and 860x600 - and of course, my screen is not in the model-list :(

Do I have to configure it in xorg.conf? How?

---

