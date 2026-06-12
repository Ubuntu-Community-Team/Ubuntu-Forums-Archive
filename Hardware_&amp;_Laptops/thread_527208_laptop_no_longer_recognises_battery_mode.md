---
title: "laptop no longer recognises battery mode"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by insane_alien on 2007-08-16
my thinkpad R50e no longer detects that it is a laptop and the power manager gives no option for setting 'on battery options' and does not acknowledge when the power cable is disconnected although it still makes a beep.

it was fine before i went on holiday and the battery still functions perfectly.

i'm lost as to how to fix this.

---

### Post by jnorthr on 2007-08-16
have there been any changes to the acpi settings in bios ? Many machines have a small battery to keep the bios settings, if it wears out, you loose the bios settings, any chance of this ?

---

### Post by insane_alien on 2007-08-16
BIOS battery is fine (tested it with multimeter). haven't touched the BIOS in ages.

i looked through them and haven't noticed any abnormalities.

---

### Post by insane_alien on 2007-08-17
nothing?

the LiveCD will recognise that it is a laptop incase that helps.

---

### Post by DiamondX on 2007-08-17
Something similar happened to my laptop - it no longer can tell the charge left in the battery. It knows when it is running off the battery or power cable, but the only way to check the charge is to press the little button on the battery. It also seems to run less on the battery than before.

---

### Post by insane_alien on 2007-08-18
see, the power applet thing doesn't recognise the difference between battery and AC mode. even though the otions i set in the BIOS when i got the laptop (and it was still running XP) still go. acpi -V still detects when the battery is discharging. i thought this was how the power manager applet worked.

---

### Post by Hillerd on 2007-08-19
I found this (in German, but the link BUG points to something english): [[http://forum.ubuntuusers.de/topic/97072/?highlight=power+management]](http://forum.ubuntuusers.de/topic/97072/?highlight=power+management])
it says, that in kernel 2.6.20-16 there is a bug so that the system does not recognize your battery any more. I am back on -15 now and it works fine. (though I just read that -15 cannot burn CDs).

---

### Post by DiamondX on 2007-08-19
Thanks hillerd. Im just going to wait till -17. Its not that importaint to me, but Im glad its not my computers fault.

---

