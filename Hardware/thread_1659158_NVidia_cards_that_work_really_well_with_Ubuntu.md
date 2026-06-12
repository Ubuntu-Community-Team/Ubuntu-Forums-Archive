---
title: "NVidia cards that work really well with Ubuntu"
date: 2011-01-03
forum: Hardware
---

### Post by Wismi on 2011-01-03
Hello all,

I decided to try Ubuntu out for development purposes, and to learn more about Linux.  I had some trouble with "nomodesetting" with my ATI card, which I managed to get through.  However, nomodesetting seems to disable OpenGL, which I care a good deal about learning on Ubuntu.  I tried everything to get an ATI Radeon 9250 pro to work with Ubuntu while keeping OpenGL activated.  This I have failed at.

I swapped it for another much older card, a G-Force MX2.  This turned out to make Ubuntu far happier.

I would like to upgrade to a more modern card, as frame rates during development are important to me.  Seems to me that NVidia works far better with Ubuntu than ATI.  Is this true?  I certainly do not mind using exclusively NVidia and locating a well known card.

What NVidia cards work *really* well with Ubuntu?

What "version" of driver should I use with it?  I am using "96" but I have seen others that I guess are for newer cards.

---

### Post by mikewhatever on 2011-01-03
Yes, Nvidia cards generally work better because the company provides better drivers. I think any modern budget Nvidia card will give you a good performance/money ratio, and the driver will be recommended by Driver Installer in Ubuntu.

---

### Post by cascade9 on 2011-01-04
> **Wismi said:**
> I swapped it for another much older card, a G-Force MX2.  This turned out to make Ubuntu far happier.

I would like to upgrade to a more modern card, as frame rates during development are important to me.  Seems to me that NVidia works far better with Ubuntu than ATI.  Is this true?  I certainly do not mind using exclusively NVidia and locating a well known card.

What "version" of driver should I use with it?  I am using "96" but I have seen others that I guess are for newer cards.

Yes, the GF-2 MX use the 96.xx drivers . The earlier 71.XX drivers will work, but they are not supported by current ubuntu versions.  Newer drivers (173.xx, 18x.xx and later) will not work with the geforce 2. 

Most of the GF2-MX cards I've seen are AGP (advaced graphics port). nVidia stopped making AGP cards years ago, the last cards they made with AGP support were the 7XXX card. 

Unless you are very lucky, you wont find any 7XXX AGP cards new. There are some older 6XXX and 5XXX (nvidia 'FX') cards stil around, but they are 5200/6200s, very 'bottom end' cards, and not really worth the money. 

If you have a free PCI slot, you could get a PCI 8400GS, but thats not really worth the money either IMO. Not really that current either. 8XXX cards will be 4 years old in april.

---

