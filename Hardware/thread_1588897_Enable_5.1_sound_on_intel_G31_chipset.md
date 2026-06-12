---
title: "Enable 5.1 sound on intel G31 chipset"
date: 2010-10-05
forum: Hardware
---

### Post by RoelVeldhuizen on 2010-10-05
I've been trying to enable 5.1 sound on my intel g31 chipset. However, i can't get it to work. Now, the last page I came across was [http://www.alsa-project.org/main/ind...x:Vendor-Intel](http://www.alsa-project.org/main/ind...x:Vendor-Intel)

From this matrix I assume that it won't work at all? Hopefully some one has any idea's?

BTW, i'm using Ubunut 10.04, with gnome-alsamixer installed ( not sure whether my system actually uses it)

---

### Post by RoelVeldhuizen on 2010-10-11
Ow, it seems that the south bridge is ICH7 which should be working!

Anyone any ideas on what the easiest way is to make it work?

---

### Post by RoelVeldhuizen on 2010-10-11
I need to add that I tried this tutorial: [http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

But no changes took effect this could be because the tutorial is for hardy and not for lynx.

---

### Post by RoelVeldhuizen on 2010-10-11
When running pavumeter from commandline it shows the folling messages:

** Message: Starting in playback mode.
** Message: Using sample format: float32le 2ch 44100Hz
** Message: Using channel map: front-left,front-right

So, it seems the old configuration is still used for some reason. I also attached my deamon.conf (name: daemont.conf.txt)

---

