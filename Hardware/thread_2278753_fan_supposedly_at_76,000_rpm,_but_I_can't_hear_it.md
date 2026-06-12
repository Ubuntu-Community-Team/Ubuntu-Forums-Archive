---
title: "fan supposedly at 76,000 rpm, but I can't hear it"
date: 2015-05-18
forum: Hardware
---

### Post by Allen McBride on 2015-05-18
My laptop (Dell Inspiron 7737 17") did a hard shutdown randomly a little while ago. At the time, I was playing Battle for Wesnoth for the first time since doing a clean install of Ubuntu 15.04 a couple weeks ago. So more processor-intensive than most of what I do but nothing crazy. And I didn't have my Nvidia card enabled so it should have been using Intel integrated graphics. My battery levels were fine so I thought maybe the CPU overheated. I found the "sensors" command by googling, and when I run it my fan speed is reported sometimes as 0, but usually as something around 76,000 rpm. [COLOR=#d3d3d3]But I can't hear the fan at all. And thinking back now, I'm not sure when the last time I heard my fan running was. When I put my head up to the base of the laptop, I can hear a faint hum/buzz. Is my fan broken? Or do I have a software problem? What should I do?

[/COLOR][EDIT: I updated the BIOS and now the fan comes o[COLOR=#000000]n. The rpm readings are still way off. But I found this bug report... [https://bugs.launchpad.net/ubuntu/+source/sensors-applet/+bug/200449](https://bugs.launchpad.net/ubuntu/+source/sensors-applet/+bug/200449) ... If I'm interpreting correctly, Dell laptop fan speed can't be read correctly and the bug can't be fixed. Still, I'll leave this question up, because I'd be curious if anyone has any insight, and the last post on the bug report was a year ago.]

[/COLOR]Here's sample output from "sensors":

acpitz-virtual-0
Adapter: Virtual device
temp1:        +46.5°C  (crit = +84.0°C)

i8k-virtual-0
Adapter: Virtual device
fan2:        77100 RPM
temp1:        +46.0°C  
temp2:        +48.0°C  
temp3:        +43.0°C  
temp4:        +16.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +46.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:         +43.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:         +48.0°C  (high = +100.0°C, crit = +100.0°C)

---

### Post by dino99 on 2015-05-19
76000 rpm is not a valid number indeed
be sure your laptop can get some fresh air: remove dust as much you can

---

### Post by mattharris4 on 2015-05-19
I don't know if your fan is defective or not but temps in the 40's C aren't bad for a computer.  Some run in the 70's C without any issue.  The 16 C temp is obviously not correct and I can't imagine a CPU fan running at 76K RPM.  My desktop runs in the high 30's C and my laptop runs between 46 C and 52 C, both are lower line computers not intended for gaming or CPU intensive use and I do not attempt to use them in that manner.

---

### Post by Kenneth_Benson on 2015-05-19
If your fan was doing 76000rpm, you're machine would have been flying and probably doing about mach 2...  0_o

---

### Post by Allen McBride on 2015-05-19
Thanks, everyone. I think I should just be happy my fan is running at all now. To get accurate sensor readings from a Dell fan (or control it), apparently the first thing you have to do is learn to use i8kmon, which requires understanding how to "swallow gnome panel applets". I installed gnome-flashback to try to make that happen, but I couldn't get the applet to run. I think I should give up, because I'm not even sure the instructions I found are current enough to work, plus that bug report I linked makes it sounds like the sensor readings might not mean anything even if I did understand how to use i8kmon.

---

