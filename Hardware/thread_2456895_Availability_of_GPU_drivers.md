---
title: "Availability of GPU drivers"
date: 2021-01-21
forum: Hardware
---

### Post by dorpapst on 2021-01-21
Hello friends,
Sorry for the annoying question, but I am new into that topic. I would like to construct a new PC and I have been waiting for **ages **that nvidiagets enough capacity for delivering their products. While I have read that it could take several more months before the next charge is ready, I had a look for alternatives.

My question is about drivers. I have read that there are usually problems with nvidia drivers and that they get built by the OpenSource community. Is there anybody who can tell me about the availability of drivers for graphic cards being similar to nvidia cards? Are there any problems with current Ubuntu versions or would it be easy to find drivers for those as well? Sorry for the stupid question, but I couldn't find proper information about it.

In fact, I am talking about GEFORCE RTX 3060 Ti cards. 
[ATTACH=CONFIG]287787[/ATTACH]

Are there any problems with the Zotac or Gigabyte cards known so far? Is there anybody who has a bit more knowledge about it than me?

Thanks in advance!

Greetings

---

### Post by CelticWarrior on 2021-01-21
Brand doesn't matter, the Nvidia chipset does.

**For the RTX3060ti you need Nvidia's proprietary driver 460.xx**. That driver is available and properly packaged for Ubuntu 20.04 LTS or newer. During installation you can select the option to install third-party drivers, codecs, etc. and the Nvidia driver will be automatically installed. No problems there, just make sure you're installing in UEFI mode and have Secure Boot disabled.

Indeed, there's also an open-source, community developed, but it'll take a very long time to catch up with that bleeding edge chips. Generally we always install the Nvidia drivers for any current hardware and use the open-source *nouveau* only for legacy hardware no longer supported by Nvidia.

---

### Post by dorpapst on 2021-01-22
Thank you very much for those information, you helped me a lot

---

### Post by mastablasta on 2021-01-22
on the other hand AMD drivers are made by AMD and open sourced. so you don't have to worry about support being cut off too much. but then again if you buy that expensive hardware you likely exchange it often anyway, so this might not be a concern to you.

---

