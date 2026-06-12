---
title: "Random Computer Freezes"
date: 2008-07-27
forum: Hardware
---

### Post by Strongbad on 2008-07-27
Hi, I just built a new desktop and I've been having issues with it freezing up randomly. It's been happening in both Windoze and Ubuntu, so I figured it might be hardware related. It doesn't seem to be getting overly hot, and all the connections inside are snug. I don't get any error messages when it does this, it usually just quits and I have to hard reset. Last time, X died and it froze when I tried restarting it.

Sorry I can't really give any more information, here's my hardware specs:

AMD Phenom X4 9750 2.4GHZ
ATI Radeon HD 3600 PCI-E 2.0 512MB GPU
4GB GSkill DDR2 1066 RAM
Gigabyte S-Series GA-MA770-DS3 MOBO
500 watt power supply
Creative Audigy 4 sound card
WD Caviar 640GB SATA HDD
Light-On Lightscribe SATA DVD Burner
Ubuntu 8.04 AMD-64/Vista Home Premium X64

The bios settings are set on optimized defaults

Thanks!

---

### Post by argosreality on 2008-07-27
Generally random locks and restarts are either heat related, bad memory modules or (less common in my experience) a bad power supply. The easiest way to test would be to download a copy of memtest86+, remove a stick of memory and test just one stick at a time. That'll narrow down to see if you have a bad stick of memory.

To test the CPU (and to some extent memory) you can also boot into windows or Linux and run a copy of Prime95 (or orthos to test all cores) but keep a system monitor window open to keep on eye on CPU temperatures as well.

Powersupply testing would require a dedicated tool for that which many people dont have any can range from fairly cheap to quite expensive. I'd start with the first too first.

However, do you have the latest BIOS releases for your motherboard? That can often fix random issues with memory compatibility as well

---

### Post by argosreality on 2008-07-27
Also I'd keep in mind that your memory is not on their supported list which could cause some fun issues. I've had difficult in the past with Gskill memory on some boards. You might have to relax the memory timings or reduce the speed it runs at

---

### Post by Strongbad on 2008-07-27
Thanks! I'll give those a try and post any results. Yeah, I was having issues with my onboard audio originally and in the process of trying to get that to work, I upgraded the bios. I never got the sound working well so I just put the Audigy card in instead.

---

### Post by Strongbad on 2009-11-19
Wow, this was a while back, but I figured I should mention that I solved this by sending a bad stick of ram back to newegg. I now use patriot memory.

---

