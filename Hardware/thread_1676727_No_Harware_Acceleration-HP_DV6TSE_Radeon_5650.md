---
title: "No Harware Acceleration-HP DV6TSE Radeon 5650"
date: 2011-01-27
forum: Hardware
---

### Post by drivelikebrazil on 2011-01-27
I'm a newbie to linux, so sorry for any ignorance I may portray.

I have been trying to get Ubuntu 10.10 up and running on my laptop, but have run into a wall on getting my discrete graphics up and running. My laptop has switchable graphics, and I've read about (and experienced) the incompatibility of the proprietary drivers with this setup, and the dumb HP BIOS hides the option to disable the switchable graphics so I decided to try to work with the open source drivers.

Hardware acceleration is enabled for the Intel integrated graphics, but when I use vgaswitcheroo to go to the ati discrete card, the opengl render string goes to software rasterizer. I'm using the updates from the xorg-edgers ppa, and this significantly increase the Intel card's performance, but I still get the software rasterizer when I switch to the ati card.

From what I've looked up, the 5650 is a REDWOOD card, which makes me think that it *should* be able to work, but I honestly am a bit clueless on the inner workings of this stuff.If anyone can help, I'd be extremely grateful! This graphics card issue has been my only detriment to switching over to linux as my main system, so I hope there's either something in the works or already working for this.

---

### Post by gordintoronto on 2011-01-27
There are many complaints about switchable graphics.

When the ATI card is active, have you run Administration/Additional Drivers?

---

