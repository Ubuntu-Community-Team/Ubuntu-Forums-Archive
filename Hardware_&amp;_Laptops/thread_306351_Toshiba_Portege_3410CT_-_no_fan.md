---
title: "Toshiba Portege 3410CT - no fan?"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by Bauldrick on 2006-11-24
Hello, first post - first time with (K)Ubuntu, so bear with me please.

I installed Ubuntu over XP with a program that escapes me now, and installed KDE - everything pretty cool and I like the speed on my slow little machine.

Just got my Belkin F5D7010 wireless card seeing my network, so I'm happy.

All that aside, I don't think the fan inside my laptop is working atall, pretty sure it's not broken, just not turning on. How do I configure it, command line or program.. whatever. It seems to be roasting :confused: 

cheers in advance

---

### Post by Bauldrick on 2006-11-25
I know I'm new but.....

Anyway it seems that I can turn my fan on by :

**sudo pico /proc/acpi/fan/FAN/state**
and changing :

**status:          off**
to

**status:***(any number between -10 and 10)*

Thing is, I can't turn it off again and it seems to slow things down ridiculously.
When I boot up, xsensors shows the board temp at <>38C and cpu <>35C, I don't consider this to be very hot (if it is correct?), but to have no fan running atall can't be very good surely?

That fan seems to be the only one I have on this l'il laptop?

ls /proc/acpi/fan
FAN

I've been through alot of posts and howto's (lm-sensor's...)

I very much doubt anyone has my machine, but a hand with starting and stopping the fan would be good

---

