---
title: "Alcor Micro Corp. webcam just works"
date: 2009-04-06
forum: Hardware
---

### Post by Nathanael Culver on 2009-04-06
After a frustrating week trying to get my laptop's webcam working -- apparently a lost cause -- and another prowling stores and googling the net (Logitech seems to be a bit of a crap shoot, and a pain to install in any case), today I walked into a store and found a US$10 webcam with "Linux" on the box and nothing but a webcam and warranty card inside. Brought it home, plugged it in, fired up Ekiga, and was amazed to be looking back at myself. The hardest part of the whole process was removing the twisty. True plug and play!

The brand is Chinese (I live in Shanghai), but lsusb reports the following:

**Bus 002 Device 005: ID 058f:198b Alcor Micro Corp.**

Alcor Micro Corp. is a Taiwanese firm that OEMs media chips, amongst other things.

--Nathanael Culver

---

### Post by stchman on 2009-04-06
> **Nathanael Culver said:**
> After a frustrating week trying to get my laptop's webcam working -- apparently a lost cause -- and another prowling stores and googling the net (Logitech seems to be a bit of a crap shoot, and a pain to install in any case), today I walked into a store and found a US$10 webcam with "Linux" on the box and nothing but a webcam and warranty card inside. Brought it home, plugged it in, fired up Ekiga, and was amazed to be looking back at myself. The hardest part of the whole process was removing the twisty. True plug and play!

The brand is Chinese (I live in Shanghai), but lsusb reports the following:

**Bus 002 Device 005: ID 058f:198b Alcor Micro Corp.**

Alcor Micro Corp. is a Taiwanese firm that OEMs media chips, amongst other things.

--Nathanael Culver

Thanks for the info.  What model number is the webcam?  What megapixel?  I am looking for a 2.0MP USB webcam that works OOB with Ubuntu.

---

### Post by Nathanael Culver on 2009-04-06
> **stchman said:**
> Thanks for the info.  What model number is the webcam?  What megapixel?  I am looking for a 2.0MP USB webcam that works OOB with Ubuntu.

The cam is really is a barebones thing -- no manual, no CD, not even much technical info on the box. From picture quality, I'd guess it's 1.3mp, however, there was a higher model which may have been 2.0mp.

It was made by Lian Zhong Xiang Electronics Co., Ltd., in Shenzhen, China, which is, I suspect, a local brand (I live in Shanghai) you're unlikely to find outside of China. But the chipset was manufactured by Alcor Corp, which apparently OEMs multimedia chipsets for many brands. A quick google turned up a reference over at the [Linux UVC project]("http://linux-uvc.berlios.de/") at linux-uvc.berlios.de. I suspect you'd be better off perusing their lists for actual makes and models which are supposed to be UVC-compliant.

I'm currently running Intrepid; I don't know whether earlier versions support UVC OOB.

---

