---
title: "Laptop Battery Woes - Cannot use battery in Gutsy"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by the_nz_monkey on 2007-12-02
Hi all

I installed Gutsy on laptop with a dead battery (battery was shorted - would not charge/discharge).
Replaced battery this week with a new, working battery (tested, confirmed battery charges and runs properly in Windows on same box).
Linux will boot (Usplash progress comes up like normal), but does a hard power off at gdm screen.
I'm able to boot into Linux with AC power, but laptop will instantly power off if AC removed (battery is fully charged, and this doesn't happed in Winders).

My assumption is that there is a config file loading which tells the computer that there is no power source (ie battery), and so turns off ungracefully.

So I guess my question is - other than reinstalling do I have any hope of getting this battery to work?

Any suggestions?
Oh, and this laptop used to work quite happily on battery power with Edgy & Feisty (until, of course, the battery died, which was just before Gutsy was released)

Cheers
NZMonkey

---

### Post by the_nz_monkey on 2008-05-02
Well, I've finally traced the problem with this battery issue of mine...
The laptop itself (an Asus A2d) has a known (well, reported but ignored by the manufacturer) problem with battery calibration.
It appeared that gutsy was just quite sensitive to how the laptop reported the battery level, but that's all irrelevant now, as the laptop's effectively killed another battery.
The laptop currently has exactly no life span if the external power source is pulled.

Oh well, never mind :)

Cheers
NZMonkey

---

