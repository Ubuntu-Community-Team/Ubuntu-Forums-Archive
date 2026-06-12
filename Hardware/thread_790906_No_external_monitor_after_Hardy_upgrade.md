---
title: "No external monitor after Hardy upgrade"
date: 2008-05-11
forum: Hardware
---

### Post by ag65151 on 2008-05-11
I have an HP laptop with the ati igp 340M video card.

Under Gutsy, I could use xrandr to turn off the LVDS and then xorg would fill in the entire display on my external monitor. Since upgrading to Hardy, I have no external display. It will mirror command line (i.e., boot sequence, CTRL+ALT+F1, etc.) but when X loads, the display goes blank and I can not get any display whatsoever. My LVDS still works, but I really want my 19-inch.

Please help.

---

### Post by ag65151 on 2008-05-12
bump

Does anyone understand how to configure the new X? Everywhere I have read says to leave xorg.conf at the minimal settings that come from dpkg-reconfigure xserver-xorg. Is there any way to "force" X to recognize my external monitor?

---

### Post by ag65151 on 2008-05-13
Bump.

I have been experimenting with xorg.conf settings and xrandr settings and I still have no external monitor. 

Sometimes I feel like Pink Floyd, "Is There Anybody Out There?"

---

### Post by Zorael on 2008-05-13
You'll need to manually configure xorg.conf, yes. There are likely guides on how to do this on ATI cards here on the forums. I can't help much; I have an Nvidia card with which it's very easy.

[http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)

---

### Post by ag65151 on 2008-05-13
Thanks for the reply, but the instructions listed didn't do anything. I am beginning to wonder if it is the "new" ATI driver. Does anyone know if it is possible to go back to the previous version of the driver? It worked for my card/configuration.

---

### Post by ag65151 on 2008-05-14
Bump.

In case anyone reads this........

I have filed a bug report on LaunchPad.........

---

