---
title: "Nvidia GeForce 8400M GS in a Dell Vostro 1500 Binary Driver Problems"
date: 2008-08-13
forum: Hardware
---

### Post by minasmorath on 2008-08-13
Hi Everyone,

I'm new to the forums, but not new to Ubuntu. I've been using it as a desktop OS since 5.10, and I've only had a few rudimentary hardware issues (out of these i learned to google the product you're going to buy, or you're gonna get screwed), but this time i'm stumped. I have a Dell Vostro 1500 with a/an Nvidia GeForce 8400M GS. This card is awesome, but when i use the standard 'nv' drivers and try to play a DVD, encrypted or not, it's always choppy. I've *kinda* solved this by installing the Nvidia Binary Driver, but my problem is this:

When i restart my computer, Ubuntu tries to autodetect my card/monitor/GPU/Whatever, and it fails, reverting to low graphics mode.

what i don't understand is that i can install the nvidia driver, do a 'sudo /etc/init.d/gdm start' and everything works GREAT. but as soon as i restart, i get 640x480 (sometimes 800x600) res and color depth of 16. i'm using the xorg.conf file that 'sudo nvidia-xconfig' generated, which looks fine, and works fine, until i restart. 

If anyone else has experience with this problem or even a suggestion as to what it could be, please help me out. Thanks ahead of time!

MM

PS-I don't want Compiz/Compiz Fusion/Enhanced Desktop/Etc, i find it to be a waste of resources.

---

### Post by masonman on 2009-12-14
I am also having troubles, having just upgraded to 9.10, Karmic Koala. I have a vostro 1500 unit as well.

I attempted to install the 185 driver, but I recieved an error and it was unsuccessful.

---

### Post by mentes on 2010-02-27
hi I am having similar problem. did you find any solution for it?
Thanks

---

