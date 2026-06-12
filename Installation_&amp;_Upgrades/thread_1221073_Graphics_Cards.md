---
title: "Graphics Cards"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by watchout5 on 2009-07-23
Ok so I've decided I'm going to upgrade my system soon, like very soon.  I'm planning on an i7 with 6gb of ram and I'm looking around for graphics cards.  Every single graphics card (mainly NVIDIA) I've ever tried to use in linux has failed, recently ubuntu has given me the worst time with my geforce 7600's (3d acceleration is almost never supported, without that what's the point?) and I'm looking to replace them with just a single card (because you can't run the TV and SLI at the same time and I use my TV more than I play games that require SLI).

Here's my question, I'm looking around at hardware and none of them say linux supported, I'm hesitant because every other card I've got has never worked properly before (3D acceleration is top priority).  I've checked around the site and can't find anything specific to graphics cards, what's one of the latest cards to come out in full 3d acceleration support in ubuntu?  I was looking kinda at the geforce 9 series, would one of those work better than my 7600's in ubuntu for sure?  I'm really trying to switch over from windows, I'm really almost there but unless I can get solid 3d acceleration support (or maybe a website with a list?) I can't see myself switching over.  Thanks for any and all help!!

---

### Post by Revolutionary101 on 2009-07-23
Did you try to download and install the drivers from NVIDIA'S website? That might help because NVIDIA provides linux drivers for most, if not all, of its graphics cards.

---

### Post by watchout5 on 2009-07-23
> **Revolutionary101 said:**
> Did you try to download and install the drivers from NVIDIA'S website?

oh good lord, I've tried their website and several others without any luck, I couldn't even get beryl to run.  I had a buddy of mine who could get the system to run but still without 3d acceleration.  I also tried on 3 different fresh installations without any luck, searching on the googles found to be some kind of common problem with 7600's not being supported in linux, like every other flipping card I've tried to use.  Do the geforce 9 cards have linux drivers these days?

---

### Post by Revolutionary101 on 2009-07-23
I don't know if the Geforce 9 is supported. Did you try to search for drivers via system>administration>Hardware Drivers?

If you do get a new graphics card then I suggest trying ATI Radeon. That should work with Ubuntu.

---

### Post by tuxxy on 2009-07-23
Any modern nvidia card will run fine, Geforce 9 is supported so you should look at the 8 & 9 series, like 8600, 8800, 9500 etc

---

### Post by watchout5 on 2009-07-23
> **tuxxy said:**
> Any modern nvidia card will run fine, Geforce 9 is supported so you should look at the 8 & 9 series, like 8600, 8800, 9500 etc

Thanks so much this is exactly what I needed :D

---

### Post by Arup on 2009-07-23
Only nvidia is serious about Linux, their drivers support vdpau and their latest beta supports Open GL 3.2 Nvidia's cheapest 8400GS will give you VDPAU and far better performance than ATI's costliest, this I speak from personal experience.

---

### Post by pwc on 2009-07-24
I've got both the Geforce 8800GT and the Geforce 275 and both work with no problems. Compiz works well with both.

---

### Post by Ratscallion on 2009-07-24
You can always edit the compiz configuration to un-blacklist your card (if it's blacklisted)
sudo gedit /usr/bin/compiz
Head down to blacklisted section and shove a # in front of the lines with cards listed. (there's about 6)

---

