---
title: "eee pc 1000ha battery not charging"
date: 2016-03-10
forum: Hardware
---

### Post by jgw on 2016-03-10
I cannot get this to charge the battery.  I have bought two new batteries, neither works.  The seller has offered to send me another but I don't think its the battery and they have no clue.  I also contacted asus and they too seemed to be stumped.  The support guy, after having me run through some things, said that he thought that the power was simply not getting to the battery.  Both batteries, incidentally, have a slight charge in that I can disconnect the power and the machine will run for about 1 minute before stopping.  

I have run everything I could find that might point to something, here is what I have:
$ acpi -V
Battery 0: Charging, 0%, charging at zero rate - will never fully charge.
Adapter 0: on-line
Thermal 0: ok, 0.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 85.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 82.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: Processor 0 of 10


~$ acpitool
  Battery #1     : Charging, -nan%
  AC adapter     : online 
  Thermal info   : <not available>

upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               ASUS
  model:                1000H
  power supply:         yes
  updated:              Thu 10 Mar 2016 03:34:20 PM PST (24 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:                 yes
    rechargeable:         yes
    state:                    charging
    energy:                 0 Wh 
    energy-empty:       0 Wh
    energy-full:            0 Wh
    energy-full-design: 0 Wh
    energy-rate:          0 W
    percentage:          0%
    capacity:             100%
    technology:          lithium-ion

Thoughts?

---

### Post by QIII on 2016-03-10
Hello!

How old is the machine?  Can you RMA it?  That sounds like hardware.

---

### Post by jgw on 2016-03-10
The machine is VERY old (at least, I think, 5 years) - no rma <g>  I talked to Asus about this and they thought that the battery was not actually getting any power and blamed the battery.  The battery seller was willing to send me yet another battery but I already have two.  I continue to pester on this one.

---

### Post by jgw on 2016-03-16
I have now contacted ASUS about this.  I have sent them any number of emails and their response is always the same; "call this number and the support tech will help you".  I have now talked to them three times.  First, the persons I have talked to speak really bad english.  Then they want to blame everything on the battery (I have now put 2 new ones in and they will not charge).  Then they want me to send the machine to a repair place.  The basic problem is that they have, basically, refused to help me fix this problem.  I have always liked ASUS stuff (mostly motherboards) but I think I will no longer deal with them because, if there is a problem, you stand little or no chance to get any help from them.   I don't want to spend any money on this as I am giving it away to somebody and just wanted to see if I could make the battery work before letting it go.  I failed............

I am going to set this to solved.  Not because it is but because, as far as I can tell, there is no place to go on this one.

---

