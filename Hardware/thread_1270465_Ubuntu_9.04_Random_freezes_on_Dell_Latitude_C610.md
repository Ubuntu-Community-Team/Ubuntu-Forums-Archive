---
title: "Ubuntu 9.04: Random freezes on Dell Latitude C610"
date: 2009-09-19
forum: Hardware
---

### Post by echo_echo on 2009-09-19
Hi,

I'm just trying out Ubuntu and am a new to LINUX in general.

I have a old(-ish) Dell Latitude C610 which I've installed Ubuntu 9.04 on.  Among several small issues, the biggest headache has been its unwavering ability to freeze randomly.  I could be in menus selecting something or maybe just using Firefox, but sometimes just doing nothing.  When it freezes the scroll lock + num lock LEDs on the keyboard would flash so I understand this as a 'kernel panic'?

I've tried mucking around with the xorg.conf and even the system clock source (using hpet at the moment).  The only active line in the "Device" section is simply:

  Device 'radeon'

So my questions are:
1.  I know this problem was prevalent in older distributions of Ubuntu - what is the solution to it?
2.  What is the 'optimal' configuration for the graphics driver?  The system in general feels slow and is improved with Desktop effects at 'None'.

The laptop is:
- Dell Latitude C610
- PIII 1GHz processor
- 1GB RAM
- ATI Mobility M6 LY w/ 16MB graphics memory

It's interesting to note my desktop computer w/ an AMD 1GHz Thunderbird processor runs perfectly with its ATI Radeon 9200SE (RV280) graphics card...

*Any* help would be appreciated - I like what I see so far with Ubuntu.  Thanks.

---

### Post by guimaster on 2009-10-23
Hey echo_echo,

 I have a Dell C610 with the exact same specs as you!

 The laptop is:
- Dell Latitude C610
- PIII 1GHz processor
- 1GB RAM
- ATI Mobility M6 LY w/ 16MB graphics memory

 I haven't experienced any of the "freezing" issues that you have, except when running some poorly programmed/incomplete Linux games. Playing those games I think I may have experienced the lights flashing also with the freezing up. During those times I had to power off the computer the hard way.

 My guess is that you are using a program that is problematic like I was. I have never had any issues with any of the default software that comes with Ubuntu 9.04, nor with my ATI card. Well actually... I believe there is an ATI driver in Add/Remove that I installed once and had problems with after and then I uninstalled it and all was fine. Maybe that is your issue.

 Personally I find Jaunty sluggish on my C610 and I really think that the new versions of Ubuntu are just too resource hungry for the C610, even with the GB of ram. I am looking into Xubuntu right now to solve that. I also have read that Karmic's requirements are 1Ghz processor and 512 ram, and that's just the minimum requirements. No more Ubuntu for my C610.

 We could run Ubuntu Hardy LTS but the packages are out of date so it's not much good. Xubuntu is the only way to go for the C610 now I'm afraid.

 Take care!

---

