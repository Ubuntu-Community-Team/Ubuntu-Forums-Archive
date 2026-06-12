---
title: "Toshiba Satellite A500 fan won't stop"
date: 2013-10-01
forum: Hardware
---

### Post by Lukas_Homza on 2013-10-01
[COLOR=#333333][FONT=UbuntuRegular]I bought a new SSD disk and installed Ubuntu 13.04 on it. Everything works fine with except that the fan won't stop cooling. I suspect its running somewhere around 70%. Sometimes it stops for 10 seconds and starts again. Even if I won't touch anything for 5 minutes, it won't stop.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]It's not overheating, laptop is cold (both cores at 35 degrees), air out of the vent is also cold. I didn't have this problem with Windows 7 at all.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
At first I suspected it was the SSD disk causing problems so I have updated BIOS to 2.00. No change. Then I swapped SSD for my old toshiba HDD and installed Ubuntu on it. No change.[/FONT][/COLOR] [COLOR=#333333][FONT=UbuntuRegular]Downgraded to Ubuntu 12.04 - no change.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
I also tried lm-sensors and fancontrol. However after sudo pwmconfig I always get There are no pwm-capable sensor modules installed.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I also tried to [Linux Kernel 2.6.38+ power issue workaround]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html").[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I would like to use Ubuntu, but not like this...[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Here are the specs:[/FONT][/COLOR]

[LIST]
[*]Intel® Core&#8482;2 Duo processor P8700
[*]Intel® GM45 Express chipset
[*]4,096 (2,048 + 2,048) MB DDR2 RAM (800 MHz)
[*]ATI Mobility Radeon&#8482; HD 4650 supporting HyperMemory&#8482; technology
[/LIST]

---

### Post by Lukas_Homza on 2013-10-02
I managed to fix it. 

By going back to Windows.

---

