---
title: "Cell Phone"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by parrimin on 2007-06-12
Hi,
Im very nearly to remove completely my XP installation;). There is only one thing i can do in XP i cant in ubuntu, connect my cell phone. I have a motorola L7, and in windows, i found somewhere some not official drivers, that allow me to connect my cell phone, and change my internal files (music, photos,...)  with a program named "p2ktools" i think. Now, i discovered wine, and i think im capable to run this program, but... how to make ubuntu detect my cell phone properly? 
I read some months ago searching for my wifi card problem, that exists ndiswrapper? Do you think i can install the cell phone using that?

---

### Post by christhemonkey on 2007-06-12
Not with ndiswrapper no.

Plug in your phone and give us the output of this command:
```
dmesg | tail 
```

---

### Post by christhemonkey on 2007-06-13
Also see this howto as this software seems to be exactly what you want:
[http://ubuntuforums.org/showthread.php?t=56253](http://ubuntuforums.org/showthread.php?t=56253)

---

### Post by parrimin on 2007-06-13
Hey, christhemonkey! I didnt know that an app like that exists. Well, im having problems to install it, in ubuntu feisty, when i type: > cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login
It give me to type password, i press enter, and thats all, there are no more messages, while i type anything, until i type Ctrl + C to interrupt. This is the first time i install anything from cvs, Do you know what am i doing wrong?

If I type dmesg | tail, the result is:
[QUOTE][10936.852000] input: Lid Switch as /class/input/input15
[10936.852000] ACPI: Lid Switch [LID]
[10937.252000] ACPI: Thermal Zone [THRM] (40 C)
[10937.432000] ACPI: AC Adapter [ACAD] (on-line)
[10937.500000] ACPI: Battery Slot [BAT1] (battery present)
[10942.196000] wlan0: no IPv6 routers present
[11909.340000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[11909.340000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[11909.352000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[11909.352000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[QUOTE]
Its that right?

---

### Post by christhemonkey on 2007-06-13
Ah ignore that howto, in feisty, you can just do:
```
sudo apt-get install moto4lin 
```

And then continue the howto from the "#Configure moto4lin" section

---

### Post by Hendrixski on 2007-06-13
don't most motorola phones run on embedded linux anyway?  should be easy to connect to from linux, shouldn't it?

---

