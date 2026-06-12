---
title: "Problems with Nvidia Driver"
date: 2009-12-31
forum: Hardware
---

### Post by emufreak on 2009-12-31
I installed the new Ubuntu Version (9.1 64 bit) on my HP Pavillon dv6666ez. I'm having problems playing games that worked great on Ubuntu 8 (64bit). The games run very slow. I first tried the latest driver that was included in the official repository (version 185). Afterwards i tried the following:

I installed driver version 190 and 195 from debpackages
I installed the binarydriver version 190 from the nvidia website

I got the same results with all drivers. Basic 3d functionality since to work fine. Glxgears gives back reosonable framerate (around 4000 fps). Tuxracer works fine with basic settings. But as soon it gets more complex (example Tuxracer with higher resolution) it gets very slow.

I noticed that the amount of videoram that nvidia-settings shows is to high. My Card Geforce 8400M GS can have a maximum RAM of 256MB. Nvidiasettings show 512MB. Maybe there is the problem.

Thanks for your help

---

### Post by emufreak on 2010-01-02
I was finally able to solve my problem. I'm experimenting with Kairo Doc. To get this to work i turned on apps-metacity-general-compositing manager. I've turned this off again. My Games work fine again. I also turned off all Desktop effects in appearance.

---

