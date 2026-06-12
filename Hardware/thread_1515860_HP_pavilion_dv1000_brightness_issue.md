---
title: "HP pavilion dv1000 brightness issue"
date: 2010-06-23
forum: Hardware
---

### Post by punkmexic on 2010-06-23
i would like to make my screen go darker..because it has 100% brightness and its getting me blind....fn keys sometimes works but they only switch from 100% to 99% brigthness and its not noticeable
i have weeks trying to get some help..on irc or forums..
gnome brightness applet doesnt work 
i tried kde battery applet and it didnt either..


this is my laptop
i686 Intel(R) Pentium(R) M processor 1.60GHz GenuineIntel GNU/Linux

the function fn plus f7 and f8 works..
but the gnome brightness applet doesn't

for example: my laptop is at 100% brightness
and i would like to be able to put it at 30% if i want.
with the gnome brightness applet or with any program
because the key bindings only tweak like 5 or 15% is not super noticeable the changes made to the brightness using key bindings


i have already tried different methods :

* Using xbacklight did not work: No display has backlight capabilities ...

* Gnome Brightness Aplet just shows a red sign and is not working

* /proc/acpi/video - > not existent, modprobed video module -> /proc/acpi/video is there but empty

* nvclock -f -S  not working, complaining about not compatible etc

* xrandr Method --output ... --SET BACKLIGHT ... (not working)
i dont know if i tried well these methods because im new..

i can follow you in gtalk, irc, msn wherever you want.

im 99% that this can be fixed..but lots of people give up easily helping me 


i haven't tried the setpci method



< @.com>	 Tue, Jun 15, 2010 at 7:39 PM
To: k@.com
lspci -x
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00: 86 80 90 25 06 01 90 20 03 00 00 06 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 80 30
30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00: 86 80 92 25 07 00 90 00 03 00 00 03 00 00 80 00
10: 00 00 08 b0 01 18 00 00 08 00 00 c0 00 00 00 b0
20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 80 30
30: 00 00 00 00 d0 00 00 00 00 00 00 00 0a 01 00 00

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00: 86 80 92 27 00 00 90 00 03 00 80 03 00 00 80 00
10: 00 00 00 44 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 80 30
30: 00 00 00 00 d0 00 00 00 00 00 00 00 00 00 00 00

---

