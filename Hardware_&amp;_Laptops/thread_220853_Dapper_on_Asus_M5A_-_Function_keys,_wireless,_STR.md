---
title: "Dapper on Asus M5A - Function keys, wireless, STR"
date: 2006-07-22
forum: Hardware &amp; Laptops
---

### Post by dud_BOLT on 2006-07-22
Hi everybody,

I have just installed Xubuntu Dapper on my M5A and for the most part, it works very well. The main issues that I have at the moment are:

Function keys:
The function keys for brightness, LCD on/off, and sleep work. The rest of them (mail, browser, volume controls) do not. I have tried using xev to get the keycodes for these particular keys, putting them in ~/.Xmodmap and including ```
/usr/bin/xmodmap /home/mike/.Xmodmap
``` in my .xsessions. However, when mapping them in XFCE's keyboard config, the map comes up blank.

Wireless network
The wireless adaptor in this system is the Intel PROSet/Wireless 2200 and I'm using the ipw2200 module included with Ubuntu. The wireless "kill switch" will only turn the adaptor off and not back on. The problem is (as I have found through much searching) common to many systems with the 2200. Out of frustration, I have tried installing Asus's power management software for windows under wine (it appears to also control the adaptor in windows) but it exits with a poorly constucted engrish message saying ```
Current system do not support this utility. Program stop!
```I was wondering if there was any newer solutions to this.

Sleep
The system appears to have no problems sleeping, but it can't resume. When trying to resume from "standby" (STR) I get a black screen and the CPU fan goes at full power. When trying to resume from "hibernate" (STD) the system crashes horribly trying to load the root filesystem.

Wow. I hope someone can make sense of this mess and thanks to anyone who has any suggestions.

---

