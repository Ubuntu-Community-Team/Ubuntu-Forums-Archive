---
title: "New Nvidia GPU/GTX 1080 Typical Support Tmeframe?"
date: 2016-05-11
forum: Hardware
---

### Post by Mr. Universe on 2016-05-11
I'm thinking about going for a GTX 1080 to replace my 680 when it comes out. As a generic question how long does it usually take Nvidia/Nouvea to release a driver for a new GPU with full support to Ubuntu? I don't expect that the new software features (Ansel, Free-look, multi-projection, etc.) will ever make their way to linux. I just curious how long it usually takes to get reasonable support for daily use.

---

### Post by oldfred on 2016-05-12
Nouveau always was reverse engineered and only recently has nVidia release some technical info on some details to make it easier for them to develop driver.

Proprietary driver should be available when card is available. But this new card may require other hardware features or a new system to work well.

[http://www.phoronix.com/scan.php?page=article&item=16-9800gtx-gtx980&num=1](http://www.phoronix.com/scan.php?page=article&item=16-9800gtx-gtx980&num=1)

Will not ship until May 27th 
[http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-GTX-1080-Unveil](http://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-GTX-1080-Unveil)

---

### Post by buzzingrobot on 2016-05-12
I'll recommend not buying the new card until after its release. Let other users be the testers. You want to be sure Nvidia releases a Linux driver and that others report it working successfully on a machine running your version of Ubuntu and, especially, the same kernel release.

---

### Post by anon24 on 2016-05-13
I've been using Ubuntu for more than a month now. I have an Nvidia card and I have yet to get the kinks worked out. I get severe tearing just from web browsing / scrolling, it's even worse with videos and gaming. I've asked both on this forum and the Nvidia forum and no one seems to know what the issue is. I would recommend finding a card by a brand that is better supported. Do a bit more research.

---

### Post by Yellow Pasque on 2016-05-13
If history is any indicator, Nvidia will have their proprietary driver ready to go around launch time. Ubuntu should have it available in standard repos for Ubuntu 16.10 and maybe they will issue an update for 16.04. If they don't, this PPA should have it shortly after release: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

> Nouveau

Forget it. Nouveau devs are still struggling with the previous generation (Maxwell): [http://www.phoronix.com/scan.php?page=article&item=gtx-900-nouveau&num=1](http://www.phoronix.com/scan.php?page=article&item=gtx-900-nouveau&num=1)

---

### Post by Mr. Universe on 2016-05-13
Thanks for all the insight.

It sounds like Nouveau is definitely out but that nVidia will shortly follow with an official release.

I'm running a Haswell era board so I would think I'm current enough for the GPU.

I could  leave the 680 in to just use with Ubuntu if drivers aren't sorted out in a reasonable time. My Zotac amped edition card is just really huge, x3 pci slots, and is a power hog.

I was planning on doing a clean install to 16.04 fairly soon so maybe I will wait to see if I'll have to go with 16.10 to get support. I prefer to use LTS releases though since 3rd party software typically tries to support those.

---

### Post by anon24 on 2016-05-13
So, the driver may be "ready" by that time... But ready is relative. The Nvidia GeForce GTX 970M isn't old and isn't new. Technically, the drivers have been out for it, but they don't work properly. And there is no telling when they will work. Frankly, I think that this card and other cards on with this issue should be listed in the incompatibility list. At this point, the Nouveau driver works better, however I can't play any games that have 3D graphics with it, but at least there isn't heavy tearing everywhere.

I know that you have your eye set on this particular card, but if you are serious about using Ubuntu I highly suggest a different brand. I'm not the only one having issues with Nvidia technology in Ubuntu. I mean, if you're ok having a really expensive graphics card that you can't really use for heavy graphics related purposes such as gaming... Then by all means, go for it. Just seems like a waste of money to me.

---

