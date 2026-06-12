---
title: "Intel &amp; Nvidia Card"
date: 2014-02-05
forum: Hardware
---

### Post by ibbill on 2014-02-05
I have installed the following card using driver version 331 

NVIDIA Quadro NVS 290 (VCQ290NVSPCIEX16PB) 256 MB DDR2 SDRAM PCI Express x16 Graphics adapter

When I boot up I get the following screen for about 5 seconds or so see attached pic

have also included my pci devices along with the computer stats Hope this is enough info. Thanks for your help.

---

### Post by grahammechanical on 2014-02-05
That is a bug in the video driver, in my opinion. A video cache on the video card is not being flushed and so you are seeing fragments of images that are still in the cache. Can you load to a desktop? If so, then count yourself lucky. In an earlier development cycle there was a similar bug in the current (at the time) Nvidia driver and we got that kind on screen image on the desktop.

I am using Nouveau on Trusty Tahr and I get a very brief flash of that kind of image just as the desktop loads after the login screen clears. Then everything works as it should.

Regards.

---

### Post by ibbill on 2014-02-05
awesome thanks very much to bad we cant just buy a intel card like the nvidia one I have. It would save a lot of problems. Thanks again for the info.

---

