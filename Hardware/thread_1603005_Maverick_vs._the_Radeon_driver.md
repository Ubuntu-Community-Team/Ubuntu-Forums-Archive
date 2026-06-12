---
title: "Maverick vs. the Radeon driver"
date: 2010-10-22
forum: Hardware
---

### Post by Fafler on 2010-10-22
I have two laptops, both contain older Radeon cards. One a x1400 and one  a FireGl V5200. I have been using Ubuntu on both of them and general 2D  performance is great. But they both fail when it comes to 3D.

These benchmarks have been made with Doom 3 on my Thinkpad T60p,  containing the FireGl, which is comparable in performance to a x1600. Al  testing is done at the default settings (i think it's 640x480).

Ubuntu 10.04: 4 fps
Ubuntu 10.04 with xorg-edgers driver: 24 fps (somewhat survivable, but theoretical performance should be 3 to 4x)
Ubuntu 10.10: 7 fps
Ubuntu 10.10 with xorg-edgers: Horrible crash during boot and unable to start X, not even with the vesa driver)

I have tried all kinds of settings in my Xorg.conf with no luck.

In general, 10.04 feels flawed compared to 10.10.  Doesn't support 3G modems in the network manager, no powersave for the graphics due to kernel limitations etc., unable to reconnect my bluetooth headset without re-pairing it, so i really want to upgrade. But 7 fps from a card that should do 70-100 at those settings is unbearable.

---

### Post by mastablasta on 2010-10-22
i can't really find drivers information for x1400 cards. i found this though:
 
"If installing a different operating system other than the one included with the laptop, the laptop may not meet all the requirements, and supported drivers may not be available." --- FireGl V5200
 
i am going to guess that you are using opensource drivers? If so then yes they are not perfect.
 
perhaps you could try topensource drivers testing version? maybe it could help. i don't know.

---

### Post by Fafler on 2010-10-22
I'm using the opensource drivers, both "normal" and testing, none of them giving performance i can live with. The official ATI drivers haven't worked with these cards since 8.10.

Right now i'm actually considering downgrading to Intrepid and have a virtual machine running Maverick on top of it. Although it seems like a big hassle just to get 3D support right.

---

### Post by Fafler on 2010-10-22
A bit more benchmarking:
Fedora 13 with default driver: 17 fps
Ubuntu 8.10 with ATI Catalyst: 56 fps, which is by far the best, but danm, 8.10 feels old :-(

Is it possible to upgrade to a later release while keeping specific packages back? It would be worth a try to keep back all kernel, X.org and ATI, while upgrading the rest.

---

