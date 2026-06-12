---
title: "AGP graphics card upgrade question"
date: 2009-07-21
forum: Hardware
---

### Post by Miester_M on 2009-07-21
I'm a newbie in the ubuntu world but I'm starting to get the hang of it. I just bought a couple of trinkets for my aging socket 478 mobo to give a little boost in the horsepower department. I bought a p4 3.0 ghz prescott socket 478 cpu & a zalman 9500 cpu cooler. I wanted to turn my rig into a decent gaming machine that can also handle hd content while being ubuntu friendly. However, here lies the dilemma. Judging from what I read in the forums, the gpu(s) I want currently have driver compatibility issues w/ ubuntu. I was debating between ati radeon hd 3850 or 4650. They both have decent specs and have dedicated decoding @ least 720p hd content (i.e h.264). That's a major plus due to the fact that the prescott is an outdated cpu. Btw, my current specs are listed in my signature. :D

Here are the gpu(s): click on the "[COLOR=Red]@[/COLOR]" for the newegg link.

**[SIZE=1]SAPPHIRE 100228L Radeon HD 3850 512MB 256-bit GDDR3 AGP 4X/8X HDCP[/SIZE]** - [COLOR=Red][@]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814102730")[/COLOR]
[SIZE=2]**[SIZE=1]XFX HD-465X-ZPF2 Radeon HD 4650 1GB 128-bit DDR2 AGP 8X HDCP[/SIZE]** [/SIZE]- [COLOR=Red][@]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814150433")[/COLOR]

Do any of you guys experienced any problems running these cards on ubuntu 9.04? What's your take on it? What else would you guys recommend? Thanks guys!

- RL

---

### Post by configt on 2009-08-07
I have not been able to get the XFX HD 4650 AGP 1GB DDR2 video card to work in my D865PERL mobo with any open or closed drivers.  XFX website doesn't even offer a linux driver at all.  ATI does, but it didn't work (screen garbled).

Good luck.  If you find another solution, please share.

---

### Post by Miester_M on 2009-08-07
@ configt: I was actually planning on buying the Sapphire card but my mobo just recently crapped out due to my power supply malfunctioning. It happened right after I installed my prescott cpu. I didn't know that a prescott could really stress my generic 430w psu to point that it started smoking. I bought an Antec psu to replace my old one. My mobo powered up fine but I didn't have any display. I reseted cmos and restarted. I realized that my mobo's fate was sealed the minute my psu started acting up. I was bummed out but I guess this is an opportunity for me to update my mobo. I just recently purchased a brand new asus mobo w/ other essentials @ tigerdirect.
 
- Asus M4N78 Pro w/ Athlon II X2 3.0 ghz Regor dual-core cpu
- OCZ Platinum DDR2 1066 mhz ram (4 gb)
- Zalman 9500a
- Antec Truepower 550w psu
 
I purched the mobo, memory modules, &  cpu for about 250-ish w/ shipping on tigerdirect. The new mobo has an onboard Geforce 8300 chipset to boot. I read that it has no problem working on Ubuntu. Plus, @ this point Nvidia has way better Linux support than Ati. Hopefully, Ati will get start getting their act together soon.

---

### Post by khelben1979 on 2009-08-07
> **configt said:**
> I have not been able to get the XFX HD 4650 AGP 1GB DDR2 video card to work in my D865PERL mobo with any open or closed drivers.  XFX website doesn't even offer a linux driver at all.  ATI does, but it didn't work (screen garbled).

Good luck.  If you find another solution, please share.

Did you get the correct driver? Also, does it work with Windows? (it would reveal if there's a hardware problem)

---

### Post by xandones on 2009-09-12
I'm using Windows Seven. To install on it you must force the installation through the INF files located on "C:\Ati\..." that appear after you try to install through Setup program. On Win XP I couldn't install recent Catalyst drivers (Version 9.X) the installer always crashes and says I have an uncompatible video board, it works only with the old drives that came on the CD (version 8.X). I'm also having problem installing the video driver on Ubuntu (the system works fine until I install the video drivers from AMD, then it crashes without recouvery).
If anyone has a solution for Ubunut, please help!!!

:confused:

---

