---
title: "Dell XPS M1730 LED's"
date: 2008-10-27
forum: Hardware
---

### Post by Antics on 2008-10-27
Hi, I recently bought a dell xps m1730 laptop and installed Ubuntu on it. When it was running Vista there were options to change the LED light colors coming from the speakers and mousepad, but due to the change this option is gone. I was wondering if these drivers would be available somewhere or if there was something else that has been written to control the LEDs. Thanks

---

### Post by macabro22 on 2008-11-04
Yeah, that'd be pretty nice indeed.

---

### Post by wiresquire on 2010-05-26
Digging up an old post, but thought thread mining was better than creating a new post...

I was looking through some things recently after installing 10.04, and found that there is indeed a way to get access to the XPS M1730 LEDs now.

dellLEDctl has been contributed to libsmbios. 

To access the LEDs:

[LIST]
[*]Install libsmbios2 and smbios-utils from synaptic
[*]Once installed, the command to use is 
dellLEDCtl <LED> <Num> where LED is which LED, and Num is the colour.
Eg sudo dellLEDCtl -z1 1 turns the touchpad Ruby.
Set to 0 to turn off.
[LIST]
[*]LED: z1 = touchpad, z2 = left speaker, z3 = right speaker, z4 = back
[*]Num: Off = 0, Ruby = 1, Citrine = 2, Amber = 3, Peridot = 4, Emerald = 5, Jade = 6, Topaz = 7, Tanzanite = 8, Aquamarine = 9, Sapphire = 10, Iolite = 11, Amythest = 12, Kunzite = 13, Rhodolite = 14, Coral = 15, Diamond = 16
[/LIST]
[/LIST]

There's also a simple GUI interface that's written in python called [XPS LED changer]("http://xpsledchanger.sourceforge.net/index.html"). Once you have the above installed, to use it simply download and install the Debian package from the link above.

And enjoy your lights!

I'm wondering how hard it might be to rig something simple to change lights based on music etc :D

hth
ws

---

### Post by macabro22 on 2010-05-27
SWEET!

I am gonna try it as soon as I get home from work.

Thanks a lot.

---

