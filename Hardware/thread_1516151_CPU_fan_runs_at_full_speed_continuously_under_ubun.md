---
title: "CPU fan runs at full speed continuously under ubuntu"
date: 2010-06-23
forum: Hardware
---

### Post by mankind117 on 2010-06-23
Hi,
I have an HP pavilion with a core i7 processor and nvidia GTS 250 graphics card
 that is about a year old.  I want to
put ubuntu or any linux distro 
on it. Everything works fine when I run 64 bit ubuntu 10.04 off the live cd or through
wubi with one exception.  When first booting a fan (the cpu fan I assume or maybe the
graphics card fan? ) goes full blast but slows down when you boot into windows.  When
booting into linux though this fan just keeps going at full blast even after ubuntu is up and running
and is quite annoying.
(I have also tried this with centos and the fan also does not shut off).  Does anyone have any suggestions about how to even beginning diagnosing what is going on or how to fix it? Is there some way
from the command line to see what the fans are doing?  Is linux just confused about how
hot the CPU actually is and are there some options one can set to control what the cooling
fans are doing?

---

### Post by yossell on 2010-06-23
Running off the live cd, and when I first installed, Ubuntu ran hot for me too, certainly hotter than windows.

Once installed, the nvidia drivers added, the cpu governor on downclocking the chip, plus a few tweaks, my computer ran as cool as under windows. You might try adding the cpu frequency scaling monitor to gnome panel, and setting the chip to 'ondemand.' You might also try downloading the powertop program, running as root from terminal, and following its suggestions.

There are some people who, even with tweaking, still find that their computers run hotter under 10.04. I don't, but it probably depends a little on hardware.

---

