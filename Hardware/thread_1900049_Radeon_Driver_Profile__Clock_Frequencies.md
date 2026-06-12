---
title: "Radeon Driver Profile  Clock Frequencies"
date: 2011-12-25
forum: Hardware
---

### Post by Prozent20 on 2011-12-25
Hi,
I have recently installed ubuntu 11.10 on my Dell Studio XPS 1645 laptop. Almost everything was recognized correctly and ubuntu runs great.

My only real problem is that my fan runs all the time. I found out that it is caused by the open-source radeon driver which does not clock down my graphics card by default.
As I use gnome 3 the proeritarty ati-driver is no option for me, so I tried changing the power consumption of my graphics card by setting values for [COLOR=#000000][B][FONT=monospace]

[/FONT]/[/B][/COLOR]sys[COLOR=#000000]**/**[/COLOR]class[COLOR=#000000]**/**[/COLOR]drm[COLOR=#000000]**/**[/COLOR]card0[COLOR=#000000]**/**[/COLOR]device[COLOR=#000000]**/**[/COLOR]power_profile

This basically works, because for the profiles low and mid the clocks are reduced drastically from 650 Mhz engine clock to about 100 Mhz, and from  800 Mhz ramclock to 150 Mhz. The other profiles auto and high leave it at the maximums of 650 Mhz and 800 Mhz ram clock.

Unfortunately 100 Mhz core clock seems to be too low for gnome 3 to run smoothly as it lags for example when switching worksapces and even when scrolling.

So I'm looking for a way to constantly adjust my gpu clock to about 200 or 300 Mhz.

Dynpm for example is able to adjust the clock frequency to about 450 Mhz, but causes too much flickering for me by chaning the clocks to often. 
Under Windows the gpu runs at about 300 or 350 Mhz while on the desktop, so I thing it shold possible to run at clocks about 300 Mhz, but i simply don't know how to tell the radeon driver.

---

### Post by BC59 on 2011-12-25
For the fan problem, the best solution is to install the proprietary graphic drivers.

From the dash search jockey and follow the instructions.

---

### Post by Prozent20 on 2011-12-25
as mentioned in my original thread I use gnome 3 and so therefore cannot use the proprietary drivers, because they run really buggy and instable with it (this applies even to the most actual versions according to my research on the web, which do not have the graphical glitches directly on the gnome top bar, but introduce other problems and instabilities to gnome 3).

---

### Post by BC59 on 2011-12-25
In such a case you could try installing the Jupiter.
[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

---

### Post by Prozent20 on 2011-12-25
Jupiter won't help. For the graphics power management it does the exaxt same thing as me: It writes values to [COLOR=#000000]**/**[/COLOR]sys[COLOR=#000000]**/**[/COLOR]class[COLOR=#000000]**/**[/COLOR]drm[COLOR=#000000]**/**[/COLOR]card0[COLOR=#000000]**/**[/COLOR]device**/**power_profile .

So let me clarify something, because maybe my first statement was not clear enough:
 - I just wan't to know if there is a way to force other clock rates for the open source radeon driver than the ones i get with the standard profiles I can set for  [COLOR=#000000]**/**[/COLOR]sys[COLOR=#000000]**/**[/COLOR]class[COLOR=#000000]**/**[/COLOR]drm[COLOR=#000000]**/**[/COLOR]card0[COLOR=#000000]**/**[/COLOR]device**/**power_profile (because I know these other clockrates are possible on my gpu).
I don't search for a nice graphical tool for ubuntu notebook power mangement in general nor for another driver.

---

### Post by Prozent20 on 2011-12-26
noone any idea?

---

