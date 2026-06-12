---
title: "Driver - VIA KM400A"
date: 2010-11-04
forum: Hardware
---

### Post by taelmx on 2010-11-04
Hey everyone, so far I have just installed Ubuntu, attempted to install KDE, and a few other things. I'm not too big of an expert, but do know a few simple shell commands, and am willing to try anything out to get my display driver working. I have a VIA KM400A Integrated Graphics, and it seems like the manufacturer's website doesn't have any recent Ubuntu drivers for this. If worst comes to worst, I'll have to shell out for a new graphics card, but honestly, I want to keep my computer pretty balanced, and since this is an older computer, I don't want to invest a ton in it when I can get by without it. I'd pay to have a driver written also, just as long as it makes financial sense to do so. Ultimately, I want to use this old computer for coding(both for Linux, Mac, and Windows if I can), but wouldn't mind if it also had some 3d modeling stuff for it. Just some basic art tools on the Linux side for this computer will help students a lot I think, instead of a strictly windows/mac environment. Anyways, if you have any advice for how I should approach this graphics card, or can help me to get it working, it's greatly appreciated! Thanks!:mrgreen:

---

### Post by P4man on 2010-11-05
There are no good linux drivers available for your videocard. VIA hasnt released the specifications and isnt providing their own drivers (though they do provide drivers for newer VIA GPU's). You may have seen this page:
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

BUt it doesnt contain useful information for your unichrome IGP I think.

Honestly, just pick up a cheap videocard on ebay or wherever. (nVidia is a good bet). Even with the best drivers in the world, you wouldnt want to do any 3d modelling with what you have now.

---

### Post by taelmx on 2010-11-05
I think I'll take the PCI one out of my newer computer next to me, and invest in a PCI-E card for it, since that seems to be the latest and greatest...though hopefully it won't break my wallet. Thanks!

---

### Post by P4man on 2010-11-05
Its very doubtful your motherboard has PCI-E slots. The KM400 is a rather old chipset that predates PCI-Express. You will most likely need an AGP card.

---

