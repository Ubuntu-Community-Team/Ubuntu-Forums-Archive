---
title: "Power Management and Ubuntu: what can/should I enable?"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by wernst on 2005-03-12
All,

OK, stupid question about power management: APM, ACPI, SpeedStep and CPUs, hard drive spin downs, and so forth.

How to I enable any of these? What does Ubuntu (warty, in my case) already enable on my notebook by default?

Thanks,
Warr

---

### Post by angrylittleman on 2005-03-12
I have to pass apm=on apci=off on the kernal to get my computer to suspend (it worked in Warty, have not tried suspend in hoary)  I have a IBM X24.  What kind of computer do you have?  If you check the harward databased on [www.ubuntulinux.org](www.ubuntulinux.org)  you can find your model and install notes.  Helped me alot.

---

### Post by wernst on 2005-03-13
I can't find a hardware database on the main Ubuntu website. A URL would be cool.

I have a Compaq Armada E500 laptop, which uses a BX chipset, a mobility Rage video card, and a nice 1400x1050 display, and runs a 850 MHz. It runs Ubuntu exceptionally well.

I'm just noticing that its cpu fan runs more under Ubuntu than Windows, so I figure that various powersaving modes aren't enabled.

That said, it is able to read the battery levels just fine, and the display dims slightly when it runs off battery too, just like Windows.

-Warr

---

### Post by malmjako on 2005-03-14
[QUOTE=wernst]I can't find a hardware database on the main Ubuntu website. A URL would be cool.[/QUOTE]
If you're looking for laptop support, this might be what you are looking for:
[http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops)

---

### Post by prizrak on 2005-03-16
Hey, 
I have kind of an opposite question :) I'm a complete noob to Ubuntu and ACPI in general, I tried searching the site but found no info on how to edit CPU speed settings, as my CPU runs at 54% even when plugged in. Also I would like to know if it's possible to set up hibernation.

Hardware:
Toshiba Satelite A-10
CPU is a P4- 2.1GHz

---

### Post by wernst on 2005-03-16
I'd like to know the answers to these questions too.

BTW, I have a Compaq Armada e500, which others have reported FULL COMPATIBILITY with Ubuntu. I agree. Warty recognized literally everything in this computer, including the PCMCIA USB2 card, the Orinoco wireless card, the super-hi-res display (1400x1050), the synaptics pad, and even the freaking volume up/down buttons on the front of the case.

Its just that the battery life under Ubuntu is around 1/2 to 1/3 less than under XP, and the CPU fan seems to run more.

-Warr

---

### Post by prizrak on 2005-03-17
Through playing around I just figured out that the CPU runs at 54% of the speed normally, but goes all the way to a 100% if needed. I.e. opening firefox or synaptic.

---

### Post by siroj on 2005-03-24
I have a Dell Dimension 5000 (desktop) PC running an up-to-date Hoary. Using Windows I can put this computer to "sleep". I'd like to have the same functionality in Ubuntu. Is this at all possible? I've looked through quite a few websites on "power management" but nowhere could I find how (and what) to enable...

Right now I have to shut down my computer every evening and boot every morning, this is a bit stupid... any answers would be appreciated...

---

