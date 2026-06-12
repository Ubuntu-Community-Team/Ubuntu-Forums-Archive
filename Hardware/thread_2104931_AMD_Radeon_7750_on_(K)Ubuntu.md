---
title: "AMD Radeon 7750 on (K)Ubuntu"
date: 2013-01-14
forum: Hardware
---

### Post by ShanaVar on 2013-01-14
I am planning to buy a new graphics card and wanted to ask if anyone can confirm that AMD 7750 cards are working well on Ubuntu (or more specific, I actually use Kubuntu). Or are there some problems with the proprietary driver?


Thanks a lot in advance!



PS: I am picking the 7750 because I'd like to have a passive cooled card, and the best passivly cooled Nvidia card is the GT 640 which is really slow compared to the 7750. Though if there are serious problems with the 7750, I might get a GTX 650 and install a passive cooler myself.

---

### Post by Yellow Pasque on 2013-01-15
AMD has open-source drivers, but they're not really ready for the 7000-series yet

If it was me, I'd go for a GTX660 and liquid cooling. I trust Nvidia proprietary drivers more than AMD's (especially when it comes to accelerated video playback). AMD also has the nasty habit of suddenly dropping support for fairly recent cards from the proprietary driver. They create a legacy driver branch, but they don't update the legacy driver for compatibility with newer kernels/Xservers, and you're forced to use open-source drivers or an LTS distro at that point.

In case you're wondering, I have a RadeonHD 4550 (passively-cooled) with open-source drivers on my primary rig right now. I watch HD videos on another Windows PC in the living room. But if I wanted more 3D power and good video playback, I would get a GTX660 and find some way to get an acceptable noise level out of it.

---

