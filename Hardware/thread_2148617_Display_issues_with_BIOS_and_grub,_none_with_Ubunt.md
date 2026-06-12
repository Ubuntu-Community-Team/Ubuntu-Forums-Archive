---
title: "Display issues with BIOS and grub, none with Ubuntu. Booting issues"
date: 2013-05-26
forum: Hardware
---

### Post by crabpot8 on 2013-05-26
I just replaced the laptop shell and the display bezel on a latitude D620. To do so I had to unplug the CMOS for some time (>30 minutes). Now the display is frequently (~90% of the time) completely blank for BIOS/grub. I've turned on some sounds and I hear beeps, but no display. When the boot process makes it to Ubuntu the display seems to "recover" and I see the splash screen fine. However, booting does not always work, sometimes I'm stuck with a black screen indefinitely. 

Any ideas on how to fix this? I'm currently trying to reset the BIOS (either using factory defaults or by reflashing) but with very little luck. Being unable to see grub is preventing me from flashing the BIOS. I can occasionally (if very lucky, seems to happen if I restart from inside a working ubuntu instead of a boot from nothing) get into the BIOS setup, but I normally only have about 30 seconds before the display goes black. I've entered the BIOS about 3-4 times in the last few hours trying to quickly reset stuff, but no luck so far. I did notice that the BIOS clock was originally incorrect. I changed it (should have insta-updated, the clock doesn't wait for save and exit), but when I re-entered the BIOS later the clock was incorrect. 

My current thought is to unplug the CMOS and leave it overnight, but I'd love to actually fix this. I'm currently unable to reliably boot into ubuntu at all

:confused:

---

### Post by 2F4U on 2013-05-26
When you say the screen is blank/black when the machine is turned on I would suspect some issue with the connection between display and mainboard. Incorrect settings in the BIOS clock can produce funny effects and even lead to a non-bootable system. I am assuming that when you changed the clock you saved the settings in the BIOS. If the clock isn't correct afterwards there seems to be something wrong, maybe the CMOS battery is weak or non-functional.

---

### Post by crabpot8 on 2013-05-26
> **2F4U said:**
> When you say the screen is blank/black when the machine is turned on I would suspect some issue with the connection between display and mainboard. 
Agreed, although I'd not expect the OS to suddenly resolve a cable-based issue, so I re-checked all cables/connectors and then decided the problem wasn't this easy

> **2F4U said:**
> Incorrect settings in the BIOS clock can produce funny effects and even lead to a non-bootable system. I am assuming that when you changed the clock you saved the settings in the BIOS. If the clock isn't correct afterwards there seems to be something wrong, maybe the CMOS battery is weak or non-functional.
Thinking back, I doubt the settings were saved. The actual words on screen were that "clock changes take effect immediately", which doesn't sound like the same thing as saved permanently. I'm not sure where the BIOS or GRUB get their display settings (reading now...), but maybe unplugging/replugging all cables messed up some display numbering. Or it's the clock as you say - the date wasn't totally off (like 1960), it was just ~26 hours ahead

---

### Post by malawito on 2013-05-26
Howdy guys, 

Have you tried to remove the bezel and the shell back again and simply connect it without those parts. My bet is that the shell might be pushing/touching some hardware parts making it to crash.
BTW: If you just wanna clean/reset the bios simply remove the cell and wait 1 min. For flashing it, I guess you'll need a bootable system.

---

### Post by crabpot8 on 2013-05-28
So the issues are resolved, but definitely not to (my) satisfaction. I basically took everything apart, removed all non-critical components (speaker, modem, wlan, palm rest (for touchpad) ) and disassembled the entire screen. I tested the LCD inverter and bulb using another laptop and both seemed good. Reconnected components and the display suddenly started working. I'm guessing there was an issue with a wire out of place or an overly tightened screw, I have no idea why I was getting no display for the bootup but a working display for the OS. 

Anyways, thread is solved but I have no idea what the actual issue was :-/ I partially suspect that I didn't properly push down the palmrest when installing, there's a connector between the palmrest and the system board that may have been loose.

---

