---
title: "CPU fan problem"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by TjiffTjoff on 2007-12-03
Hi!

I'm installed UbuntuStudio 7.10 a couple of weeks ago and I love this OS.
Until now I've been a steady Microsoft-user but I've truly grown tired of the
tons of spyware and virus I have received during the time.

Everything works like a charm after some digging and customizing except
for one thing; my CPU fan. It never stops...! I mean it does stop when I turn
the computer off. With this kind of fanspeed it's a lot noiser than my old 
desktop.

In Windows I had a tool named Power4Gear where I could choose some power-
profiles, ex. SuperPerfomance, Gaming, Quiet Office and BatterySaving. When I
chose Quiet Office the fan went silent and it became a pleasure to work with it
since I didn't need any earplugs to keep the noise out. 

When I boot into Ubuntu (I'm using DualBoot at the moment) the fan goes wild.
BUT, if I first boot into XP and choose the "Quiet Office"-profile, restart the laptop
and boot into Ubuntu, the fan is silent. But then it never kicks in. So my options
at the moment are booting directly into Ubuntu and listen to the helicopter-like 
fan-noise or boot into XP, then Ubuntu and lose the fan completely.

Any ideas? :confused:

My laptop is by the way an Asus F3F (a.k.a. Z53F).

---

### Post by bobyy on 2007-12-03
what processor you have ? linux have good daemons to to cool down your CPU :)
tell me what is the processor ...
you can use powernow  or CPUfreq i thik the both are in repositories
after you instal this you can add the CPU frequenci scaling monitor applet...and set what CPUfrequncy you want..
powersave
ondemand
performace....
for celeron /intel try thys 
> [http://ubuntuforums.org/showthread.php?t=582069](http://ubuntuforums.org/showthread.php?t=582069)
AMD
> [http://ubuntuforums.org/showthread.php?t=248867&highlight=AMD+cpufreq](http://ubuntuforums.org/showthread.php?t=248867&highlight=AMD+cpufreq)

---

### Post by TjiffTjoff on 2007-12-03
I'm having an Intel Centrino Duo, 1,66 Ghz. I think the name of it is T5200.
I've enabled the scaling and I'm almost always running on Powersave. But
still the fan spins on as if it prepared to take off.

I have also installed lm-sensors and I usually get temperature around 35-45 C
from each core. 

The strange thing is the fanspeed seems to depend on my fantool in Windows.
The reason I desperately trying to reduce the fannoise is because I use to
record music with my computer and I don't really enjoy a "brrrrrrrrrrrrmmm"
in the background of my tracks... :(

---

### Post by bobyy on 2007-12-04
so.in this case maybe you must check the BIOS setings....i never heard about something like this ...sorry dude

---

### Post by TjiffTjoff on 2007-12-04
Thanks for trying.

Already been down that road. My BIOS is a very simple one with only a small number of
settings to change. Nothing about any CPU or fancontrol.

I've heard about trip_points. Is this something that can be relevant in my search for
the answer?

---

### Post by PmDematagoda on 2007-12-04
Yes, it must be a BIOS issue, in my own PC I have the choice of running the fans all the time at low speed or turning them off when the temperature is low enough.

---

### Post by TjiffTjoff on 2007-12-04
So, there's nothing I can do about it then? :(

The weird thing is just that the settings in Windows stays when I boot into Ubuntu.
Since the speed is set by a program in XP, shouldn't I be able to change it in Ubuntu?

---

### Post by bobyy on 2007-12-04
can y sugest you something?
try to see how it is working just with Live CD ,.....or maybee Live CD from other distribution....it is  a start point to see what a hack is going on...
also can you tell what is the average of procesor load ?and the temperature in the same time ?

---

