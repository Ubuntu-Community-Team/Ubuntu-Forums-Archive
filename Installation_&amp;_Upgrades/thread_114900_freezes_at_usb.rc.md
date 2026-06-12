---
title: "freezes at usb.rc"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by squimmy on 2006-01-09
Hello,

My computer will not correctly boot into ubuntu to continue with the installation. The boot-up will come to a total standstill at /etc/hotplug/usb.rc. I am hoping, that there is some command which will allow me to continue with the installation. This is not a laptop.

It is a Compaq Presario, I'm not exactly sure what model number, but it comes with a amd 64 3200.

Thank you for any help.

---

### Post by squimmy on 2006-01-09
If knobody knows anything about this, can anybody please then tell me if another distrbution of linux is more likely to work?

---

### Post by squimmy on 2006-01-10
Is there any way I can get the install process past this?

---

### Post by squimmy on 2006-01-14
I cannot get past this. Is there a way to disable usb probing?

---

### Post by JKBurton on 2006-01-19
Mine worked by specifying: 
linux noapic nolapic
...at the "Boot:" prompt.

Good luck!
Keith

---

### Post by ajosifoski on 2006-01-20
[QUOTE=JKBurton]Mine worked by specifying: 
linux noapic nolapic
...at the "Boot:" prompt.

Good luck!
Keith[/QUOTE]

can you be more explicit about this (noapic at the boot: prompt) please :confused:

---

### Post by invader980 on 2006-01-20
im new to linux all together but i beleieve  he means @ install  from the "Boot:" prompt.

use Boot: linux noapic nolapic

i hope so cause im goin to try <<<< having the same problem my system dreezes @ starting hotplug subsystem......   

im new to linux tho .... new as in never even got a distrubution correctly installed yet  lmao so thats just what i gathered.   

speaking of which dose anyone know a 100% fullproof distrubution because ive downloaded about 6 and burned and installed  all of them with no luck, the only one i got function was a server which i realy couldnt figure out it was so confusing with little to no options lol

this is thee 2nd computer iv tryed ubuntu on and its driving me nuts... :( i just wanted to try something new lol

---

### Post by invader980 on 2006-01-20
... not to steal ur post i was just asking for a quick suggestion  sorry

---

### Post by johnnymo87 on 2006-05-02
[QUOTE=squimmy]I cannot get past this. Is there a way to disable usb probing?[/QUOTE]

I have been fiddling around with boot options with my live CD.

Boot up the live CD, and on the boot line type:
*live debian-installer/probe/usb=false*
There are other modifiers for the boot process. Press F1 to see a tree of them.

---

