---
title: "Video / Graphics Card Hardware Recommendation(s) -- UltraWide monitor (native driver)"
date: 2018-01-15
forum: Hardware
---

### Post by mr.charles on 2018-01-15
**First Post** *(expecting to be skewered, have at it)* ... 

**Setup:**
HP Z800 (v2, 2010) w/ AMD/ATI FirePro v3700 (mfg).

**OS:**
Xenial

**Issue:**
Got an LG 34UM61 for Christmas. *(Unexpected gift, no plans to upgrade video, so, here I am going fishing.)* UltraWide monitor. LG 34UM61 has a max resolution of 2560x1080, but I can't get anything above 1920x1080. The higher resolution is theoretically supported by the AMD/ATI FirePro v3700. However, this card is more than a few years old. *(Sorry, gamers, I'm not classy like you; I'm satisfied with the basics for programming.)*I tried loading the proprietary drivers from AMD, and, that didn't fix or help anything. Part of the problem may be the DVI-to-HDMI interface and/or cables. *(Some people say this makes a difference, I've tried different cables and connectors without luck.)*

**Ideally, here's what I'm looking for:**


[LIST]
[*]Workstation Graphics (gaming is okay, I'm just not paying top dollar; nor am I interested in fancy-spanking-new or hella-GPU) 
[*]VG Card can be a few years old, as long as it can be bought new. 
[*]VG Card needs to be PCIe x8 or x16 complaint (Z800 slots) 
[*]VG Card ***should have* HDMI 2.0+** *(not VideoPort or DVI -- don't want cable or connector issues, straight HDMI-to-HDMI preferred)* 
[*]****Works out-of-the-box with native graphics drivers, high resolution instead of having to load proprietary drivers.**** 
[*]Native meaning: Should work with multi-generations of Live CD's without patching or relying upon another monitor. 
[*]Completely indifferent about AMD/ATI vs Nvidia (I'll go-in for either, but have a preference for Quadro). 
[*]Offshoot: Lower-power is better; all the new, additional, modern, fancy power connectors for video cards is questionable without needing an additional adapter (HP Z800 is workstation, not gamer-gear).
[*]Can be multi-slot (nothing that can't be shifted or removed is taking-up too much space; as long as multi-slot doesn't imply extreme power requirements). 
[/LIST]

If anybody knows of specific VG cards matching these criteria; supports 2560x1080 HDMI 2.0+ *(native drivers, without having to load the proprietary drivers)*, I'm all eyes.

On my own part, I've done a small bit of research -- but I'm not a graphics guru or the likes, and, all of the whimsical selling-points that don't interest me obscure searching for the selling points I'd prefer -- what I'm really looking for are people with similar mindset and experience who can point me in the right direction. (I can take it from there.)

---

### Post by him610 on 2018-01-15
These cards may fit your requirements...

[https://www.amazon.com/s/ref=nb_sb_noss_2?url=search-alias%3Daps&field-keywords=nvidia+gt+730]("https://www.amazon.com/s/ref=nb_sb_noss_2?url=search-alias%3Daps&field-keywords=nvidia+gt+730")

---

### Post by mastablasta on 2018-01-17
i have GT 730. all nvidias will need to load proprietary drivers to work at their full capacity. mostly basic support is provided by nouveau. nouveau is not so good as it is reverse engineered. but it will often work well enough for desktop activities.

to have strong GPU and opensource drivers, you need to use one of the newer AMD cards.

---

### Post by Yellow Pasque on 2018-01-17
> **mr.charles said:**
> UltraWide monitor. LG 34UM61 has a max resolution of 2560x1080, but I can't get anything above 1920x1080. The higher resolution is theoretically supported by the AMD/ATI FirePro v3700. ... Part of the problem may be the DVI-to-HDMI interface and/or cables. Some people say this makes a difference, I've tried different cables and connectors without luck.

Did you try adding the resolution with xrandr? You're using a dual-link DVI connector/adapter? [https://en.wikipedia.org/wiki/Digital_Visual_Interface#/media/File:DVI_Connector_Types.svg](https://en.wikipedia.org/wiki/Digital_Visual_Interface#/media/File:DVI_Connector_Types.svg)

> VG Card ***should have* HDMI 2.0+** [I](not VideoPort or DVI -- don't want cable or connector issues, straight HDMI-to-HDMI preferred)

Your monitor is HDMI 1.4, so I'm not sure why you insist on HDMI 2.0 card. If you're trying to future-proof, DisplayPort is a better option (more bandwidth available).
Also, only more recent cards have HDMI 2.0, so that's at odds with your requirement that everything works out of the box on "multiple generations" of LiveCD/USB (because older cards are more likely to work on older Ubuntu versions).

Was that sufficient skewering?

---

