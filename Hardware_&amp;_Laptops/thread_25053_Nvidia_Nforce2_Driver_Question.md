---
title: "Nvidia Nforce2 Driver Question"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by sinbad782 on 2005-04-09
Hi all,
   I recently built a SFF machine using an Epox mATX motherboard with an nforce2 chipset. I have had Ubuntu installed for a few weeks now and, having set up Debian machines before from scratch, I have been very pleased with the improvements in the installer and the general ease of use. 

I was wondering if it is necessary to install the platform driver from [www.nvidia.com](www.nvidia.com) in order to get the best from my motherboard? If you surf to their site, they list both drivers for graphics cards and platforms (nforce2 chipset based machines etc.) I am assuming this isn't included in the nvidia-glx package?

My graphics card is also Nvidia (Geforce FX5200 low profile) and I have already installed the nividia-glx package. I have tested gl performance using glxgears (and a few games of Enemy Territory) and this seems fine. Average framerate in glxgears is about 850 or so.  I also haven't got checked that sound is working yet as I need to buy some extra speakers for my new machine. 
  
Any advice gratefully received,

PJS

---

### Post by soul_rebel on 2005-04-10
I think the nvidia.com's driver is about onboard ethernet and audio. I am using nforce 2 with open drivers. Also try a modprobe cpufreq-nforce2, you will have a pleasant surprise.

---

### Post by sinbad782 on 2005-04-10
Thanks for the tip - sounds like a really useful module to have loaded. I might not do this at the moment as I really need to get a better cooler for my Athlon XP 2500+ Barton Core CPU. I have been running it at only 100Mhz FSB as, if you use a higher FSB, the chip gets too hot. 

At 333Mhz FSB, the SFF case means it gets really hot (sometimes up above 60 degrees C) and I have had it do a thermal shutdown on me before.  :shock: 

This system is ultimately going to be used as a PVR in my living room, with MythTV installed on it. When I have some more cash I am thinking about putting a quiet water cooler on it, or perhaps cutting a blowhole in the aluminium for a large 120mm exhaust fan. 

PJS

---

### Post by soul_rebel on 2005-04-10
that module isn't supposed to do overclocking or similar, it is supposed to save energy and reduce temperatures. if you use it with powernowd (from ubuntu) it scales down cpu freq when you don't need it. I wouldn't worry about my cpu temp until 65-70°. Anyway consider buying a couple of case fan and (i suggest ) put them at 7 volt, to have a quiet and cool pc

Here my configuration

amd barton Mobile 2600+ @ 3200+ (200*11) vcore 1.575
4 case fans at 5 volts
coolermaster areo 7 on the cpu (fan speed is adjustable from the front of the case) 

With cpufreq it stays at 39 keeping the fan slow (and quiet); when gaming or similar i put the cpu-fan to the max and the cpu reaches only 45- 46.

Perhaps yours is a voltage setting problem? see in the bios if you can set it lower

---

