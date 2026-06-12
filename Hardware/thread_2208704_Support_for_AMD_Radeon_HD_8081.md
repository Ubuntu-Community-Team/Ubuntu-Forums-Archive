---
title: "Support for AMD Radeon HD 8081?"
date: 2014-03-01
forum: Hardware
---

### Post by uchi2 on 2014-03-01
Hi, I owned a laptop (asus 1025C) which had integrated graphics card (gma 3600) that was very wrong ... It had no drivers, and watch a movie with a rather good quality, mp4 was impossible. indeed .... I could not use unity3D


I will buy another laptop, but first I want to ask if this notebook: 


[http://www8.hp.com/lamerica_nsc_cnt_amer/es/products/laptops/product-detail.html?oid=6490167#!tab=specs](http://www8.hp.com/lamerica_nsc_cnt_amer/es/products/laptops/product-detail.html?oid=6490167#!tab=specs) 


whose amd radeon 8081 graphics card is relatively new .... works well 


I know from valve drivers have improved a lot .... this laptop will work with linux, especially with ubuntu? 


thanks

---

### Post by mörgæs on 2014-03-02
Before buying new stuff: Have you tried Lubuntu 13.10 on the Asus?

---

### Post by uchi2 on 2014-03-03
> **mörgæs said:**
> Before buying new stuff: Have you tried Lubuntu 13.10 on the Asus?


Yes, lubuntu, xubuntu, ubuntu with gnome fallback... KDE.... even windows xd any of them works a bit... its lagged, and like I say before, view a video file, its imposible...

It has an infamous cpu N2800 with integrated gma 3600 graphic card... intel has not launched a good video driver form linux, (we only have a poor 2D driver) and windows.... well.... its windows.... (it doesnt work very well) thats because i want to ask for AMD Radeon HD 8081... because I dont want the same problem with other laptop.... 

Anyway... searching for ATI drivers, the latest beta driver has support for HD 8000 series, and I think that Valve caused ATI and NVidia to develop good drivers to make SteamOS playable....

What do you think?

---

### Post by mörgæs on 2014-03-03
Sorry, I don't know the Radeon. Have changed the title of the thread to (hopefully) catch someone who does.

---

### Post by Mark Phelps on 2014-03-03
There have been problems with using the fglrx drivers from the repos on the AMD HD 8xxx series cards.  I have an 8850 and the Additional Drivers trashed my PC when I tried to install them.

However, I downloaded the Catalyst 14.1 drivers from AMD, uncompressed the file, executed the ".run" file -- and the drivers installed without a hitch -- and are working without any problems.

---

