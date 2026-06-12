---
title: "Battery moniter on HP X2 detachable"
date: 2018-10-12
forum: Hardware
---

### Post by benji21629 on 2018-10-12
So I have an odd one here... according to ACPI i dont have a battery in my laptop. 

ACPI -V dump is as follows

Adapter 0: off-line
Thermal 0: ok, 52.0 degrees C
Thermal 0: trip point 0 switches to mode hot at temperature 89.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 87.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: PNIT no state information available
Cooling 2: soc_dts1 no state information available
Cooling 3: Processor 0 of 10
Cooling 4: STR0 no state information available
Cooling 5: Processor 0 of 10
Cooling 6: STR2 no state information available
Cooling 7: intel_powerclamp no state information available
Cooling 8: soc_dts0 no state information available
Cooling 9: iwlwifi no state information available
Cooling 10: Processor 0 of 10
Cooling 11: INT3400 Thermal no state information available

This is a fresh install of cuttlefish, on a HP x2 detachable tablet pc with an atom x5-z8350 SoC.

---

### Post by Autodave on 2018-10-13
I have run into that before: only on HP though....kinda weird.  I have had it more often when there has been a non=factory battery in it.  Some things that I have done that have had varying degrees of success:

1.  Turn laptop on *without* power cord connected. Once booted and battery recognized, then connect power cord.
2.  Let laptop completely run down until it shuts off.  Keep trying to reboot it until nothing happens. Plug power cord in and see if light is telling you that it is charging. If not, unplug it, plug it in again and see. (You may have to do this a few times.)
3.  If possible (and I don't think it is on that machine) remove battery and disconnect EVERY cord from machine. Let sit like that for at least ten minutes. Re-insert battery, connect power cord only, boot machine.

---

### Post by benji21629 on 2018-10-13
I have only seen this problem on only this system while using ubuntu or ubuntu derived distros. Fedora can see and tell me how much battery i have left, but thats its own can of worms. 
booting the unit off battery still doesnt show that this thing has a battery, however ACPI does know that there is no mains adapter. While this isnt a big issue with a system that gets 8+ hours off a charge, it is kinda annoying.

---

