---
title: "Which graphic card would you suggest?"
date: 2014-11-13
forum: Hardware
---

### Post by Ravexina on 2014-11-13
hi,

I'm running **[COLOR=#ff8c00]ubuntu[/COLOR]**+**[COLOR=#800080]openbox[/COLOR]** and it's awesome, but somehow my graphic card failed and i'm looking for a new one.
My pc is old, CPU: AMD Athlon 64 3200+ 2010 MHz, 1GB Memory, I use this PC for basic desktop usage like web browsing, movies and music, so i don't really need a high quality graphic card. my ex card was nvidia 6600 le. i need a cool one with good driver support and low energy usage, so any suggestion would be helpful.

thanks a lot.

---

### Post by bcschmerker on 2014-11-14
What motherboard your system?  The chipset is critical for a determination of what GPUs will function correctly on your rig.

As of 13 November 2014, I have a Diamond Multimedia® 5450PE3-512SB (ATi® Radeon® HD 5450 GPU, 512MB DDR3 video memory) in my Gigabyte® GA-MA78GM-S2HP-based LinUX box.  I would not, nowever, attempt to run an ATi® GPU on a system with an integrated nVIDIA® nForce® chipset such as the 785G (C77 64-bit GPU) due to a long history of hardware conflicts between ATi® and nVIDIA® products.

---

### Post by Ravexina on 2014-11-14
Motherboard is:

[WinFast NF4SK8AA]("http://www.foxconnchannel.com/ProductDetail.aspx?T=Motherboard&U=en-us0000010&Language=en-us")
Based on nvidia nforce4 SLI

5450 was one of my options :sad:

---

### Post by mastablasta on 2014-11-14
I have on 3 PC AMD card and NVidia chips. one even has built in NVidia GPU. they all work fine for many years now. are about as old as your PC. 

Get the chepest you can and with still good support. If this AMD will bring you what you need and the price is good go for it. otherwise they sell cheap Nvidia and AMD GPU cards that are ment for media playing mostly etc. they will do just fine for what you need them. just make sure they still have drivers available for Linux (ehm AMD has a history of dropping their support unexpectedly....)

---

### Post by Ravexina on 2014-11-14
I had many issues with my nvidia 6600 le on linux, for example video playback was not smooth, high temp with nouveau, almost +100°, and with nvidia driver it was around 80° , so i'm looking for something better.  I did some search and i found nvidia geforce 210 good for my needs. but reviews says it gets hot on gaming, of course i'm not gonna play on this PC but is it possible card gets hot badly on my linuxbox like my ex exprience? cuse it's uses passive cooling (just a heatsink). should i buy a card with active cooling? or it does not matter!?  another thing is, i think my motherboard PCI-Express Slot is x16 v1, can i use new versions of PCI-Expres like x16 v2 on my board?

---

### Post by bcschmerker on 2014-11-14
After reviewing options for video cards that tested reasonably well with X.org Nouveau as reported by Phoronix®, I found a mid-range Kepler that might meet your requirements in the [eVGA® 02G-P4-2651-KR GeForce® GTX&#8482; 650](http://www.evga.com/Products/Product.aspx?pn=02G-P4-2651-KR) (nVIDIA® GK107-450-A2 GPU, 2GB 192-bit GDDR5-5000 video memory), which requires one 6-pin PCIe auxiliary power feed.

---

