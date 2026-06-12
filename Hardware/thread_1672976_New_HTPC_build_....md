---
title: "New HTPC build ..."
date: 2011-01-21
forum: Hardware
---

### Post by OZZ_ on 2011-01-21
Hey guys, I recently converted ... permenantly to Linux and Ive been trying to get everyone I know to do the same. Im super happy to finally be rid of microsoft.
 
Anyway Ive got a central workhorse doubling as a server and one HTPC in my main living room. This christmas I bought a new flatscreen for the bedroom and am putting together an inexpensive HTPC to attach to it. Most data will be streamed from the server for playback but I do have a few questions. Im running Ubuntu 10.04.
 
Heres the parts list:
 
MB: ASUS M4A785-M 
CPU: AMD Athlon II X2 dual core @ 3.0Ghz
Ram: 2G DDR2 800
HD: 500GB WD
Wireless PCI card:EDIMAX EW-7728In
 
Firstly, the motherboard has onboard ATI Radeon HD 4200 with HDMI... Ive heard linux can be buggy with ATI. Should I have cause for concern here?
 
Secondly Im wondering if 2G's will be enough ram.
 
Thats really all Im wondering about I appreciate any input you could provide.

Thanks!!

---

### Post by cascade9 on 2011-01-22
ATI 4200s should run OK. There are more people having problems with the ATI proprietary drivers than nvidia proprietary dirvers. 

You would be better of with a cheap nVidia card to get VDPAU (nvidia hardware video decoding). A cheap GT210/GT220 wil do the job, and reduce the CPU power (and electrical power) needed to decode video.  

2GB is more tha enough for HDTV use ;)

---

### Post by OZZ_ on 2011-01-22
Thanks for the input. Its greatly appreciated.

I do have an XFX 9500GT 2.0 x16 card that I could put in there, but I wasnt sure if it was necessary (its 512MB DDR3, 128 bit). Actually, I also have a XFX 8600GT 256 MB DDR3 PCI E x16.

Once I get the parts Ill probably just put it together and give it a run to see how things go, If need be Ill slap one of those cards in there.

---

### Post by cascade9 on 2011-01-22
If it was me, I'd just shove the 8600GT in there, and use it. (lower power requirement than the 9500GT, same VDPAU features).

---

### Post by OZZ_ on 2011-01-22
I might just do that.

What are the benefits of VDPAU? What makes them preferable in this scenario then the ATI 4200?

Just out of curiosity, graphics cards are my weak point and I dont have much knowledge of them.

Thanks again for the input!

---

### Post by cascade9 on 2011-01-23
VDPAU just moves the decoding from the CPU to the GPU. The main advantages are less CPU use, less power use and less heat.

---

