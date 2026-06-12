---
title: "Issues with new hard drive on HP Pavilion dv6"
date: 2014-07-17
forum: Hardware
---

### Post by choklitmello on 2014-07-17
I have an HP Pavilion dv6 that worked fine on Ubuntu 13.10 (14.04 wouldn't install-- it would display a static-like pattern on the screen when I tried to boot the CD) up until I replaced the 80 GB original hard drive with a new 1 TB drive (WD AV-25 1 TB AV Hard Drive: 2.5 Inch, 5400 RPM, SATA II, 16 MB Cache - WD10JUCT). Now it won't boot consistently. It boots fully approximately one time in every three attempts. Sometimes it'll give me a black screen with white text that reads:
```
Gave up waiting for root device. Common problems:
[it lists common problems]
ALERT! /dev/disk/by-uuid/f47dd67b-6b4f-4a1f-9b0a-ca576f06561d does not exist. Dropping to a shell!
```
Then it starts the Busybox shell. Other times it'll simply give a black screen and just stay there. When it does boot, it'll function normally for a while, then one application will become unresponsive and then all the rest will follow. I can still move the mouse at this point, but force-quitting doesn't work. If I try to shut it down using the menu, it will shut down the menu and sidebar, leaving on my desktop wallpaper on the screen, and stay like that until it is manually shut off.

 I tried installing Linux Mint. Same problem with booting, with a similar if not identical error on some of the boot attempts. I didn't try it out long enough to gather much information on whether it would freeze up like Ubuntu 13.10, but the web browser would crash occasionally. I'm now on Xubuntu 14.04 and it's not booting every time either. I was looking around and I saw someone say that this drive is an AV drive and not suitable for holding the OS, but then someone contradicted them and said it should just be fine. Needless to say, hard drives are not my area of expertise. If it is a problem with the drive, I'd like some advice on what kind to get.
Thank you very much.

---

### Post by mastablasta on 2014-07-17
it says this drive is designed for continuous use and mostly ment for video PVR devices, survailence videos etc.

 i am not sure that in your case the drive is to blame (this could be tested by running off USB for a while and see if issue reappears there as well). but i do know that for example their WD Green drives are notment for os. they also power down when not in use and i had issues with putting the OS on them. strange behaviour was noticed. and although i tried it with winXP i had similar issue as you have now on that drive (system won't always boot, system would freeze...). i though the drive is faulty and decided to test it with tools and then to test it in Linux machine. it turns out the drive works just fine as long as it is used for data.

---

### Post by choklitmello on 2014-07-17
It runs fine off of the USB. I'll probably put my old working drive back in and buy an enclosure for this one so I can use it for storage.

---

