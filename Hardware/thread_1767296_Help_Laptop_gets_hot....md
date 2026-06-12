---
title: "Help Laptop gets hot..."
date: 2011-05-25
forum: Hardware
---

### Post by ThatCoolGuy220 on 2011-05-25
Ok so i dished/selled parts of my old one after mint killed it....(IDK HOW :?)

but my new one is a:

HP Compaq Presario CQ41-226LA

gets hot i mean i installed a heat sensor and is at 47°C, OMG!

when touching it from below it feels hot 

Please help me i updated kernel installed lm-sensors stuff

but still Please i wanna keep this laptop.

---

### Post by ThatCoolGuy220 on 2011-05-25
I'm using 10.04
Should i update to 10.10?

---

### Post by noidian on 2011-05-25
10.04 is currently a stable release, unless you have installed other utilities which use up a lot of computing resources. 
In the terminal: ps -elf
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD

Check the programs with the largest number under the C and see whats clocking your computer.

---

### Post by IcarusR on 2011-05-25
> gets hot i mean i installed a heat sensor and is at 47°C, OMG!

Personally I don't think 47c is that hot. My Tosh Equium runs at 44 - 47c most of the time. If I do any thing CPU intensive such as video re-encoding it goes upto 70c but always drops back.

Make sure you do not block the air vents on the under side.

---

### Post by ThatCoolGuy220 on 2011-05-25
ok im upgrading to check since new releases could support new drivers and stuff i wil tell you guys how it is doing ok

---

### Post by tgalati4 on 2011-05-25
Exactly how did Mint kill your last laptop?

---

### Post by ThatCoolGuy220 on 2011-05-26
-Overheat i was compiling on netbeans them laptop sutted down and never turned on again even the repairman told me: Get a new one this motherboard is fried, very odd though.


 And now its happening with this one i must add to the issue:

The directory: /proc/acpi/fan, is empty

Also: /pro/acpi/fan/thermal_zone/trip_points, says:

critical (S5):           105 C
hot (S4):                100 C
passive (forced):<not set>

---

### Post by ThatCoolGuy220 on 2011-05-26
Somebody told me in natty narwhal this problems are fixed is that true?

---

### Post by ThatCoolGuy220 on 2011-05-26
Sorry for double Post 

I readed was still on beta so not stable.

---

### Post by phredbull on 2011-05-26
My Compaq Evo N610c runs very hot, but it has a P4 processor, which I don't think yours has.

---

### Post by ThatCoolGuy220 on 2011-05-26
I think mine is AMD but fans arent working

---

### Post by phredbull on 2011-05-26
Not sure if Natty fixes your problem, you should seek out some user  testimonials from users w/the same cpu as you here on the forums.
Natty is no longer it in beta, it is officially released, but generally  with any new Ubuntu release, bugs continue to be found and fixed. It's  usually a month or so after official release that Ubuntu gains some  semblance of "stability".
BTW, I'd be very careful about using your computer with no functional cooling. Are you sure it's not a hardware problem?

---

### Post by ThatCoolGuy220 on 2011-05-26
My model is not common though i havent find info: 

but with the other laptop i was looking help and one guy told me natty have support

though i need help because it seems that the controlers or sensors fo dan weren installed

---

### Post by asd1618033 on 2011-05-27
here the specs:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01989786&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=4126069](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01989786&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=4126069)

AMD M330 CPU + ATI 4200

ub 11.04 have k10temp module for lm_sensors by default.
In previuos releases you have to add it by some user repository or compiling it. 

I think that if your laptop goes hot is for power management not present for your graphics.
Ensure that, in xorg.0.log, there are no errors/warnings about proprietary drivers, if you use it (fglrx -> ati catalyst).
If you use radeon open drivers, try using infos on arch wiki:
[https://wiki.archlinux.org/index.php/ATI#Powersaving]("https://wiki.archlinux.org/index.php/ATI#Powersaving")
I'm sorry but I have no experiences with ubuntu

Btw, <50 °C is not hot.

---

