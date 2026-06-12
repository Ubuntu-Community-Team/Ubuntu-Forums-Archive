---
title: "New Hardware - do I need to do anything"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by terryeden on 2007-02-19
My CPU burned out last night and I'm wondering how this will impact my Ubuntu install.

I have two options

1) Replace the Sempron 2800 with an Athlon XP 3000 (both Socket A).
2) Get a whole new computer.

If I replace the CPU, will I need to do anything to Ubuntu (6.10)?  Will it recognise the new CPU and adjust according ly?

If I place my HDD into a brand new box, what will I need to do to get Ubuntu up and running again?  I remember with XP I "merely" had to reboot half a dozen times and manually install drivers etc - is Ubuntu any better?

Thanks

Terry
PS - never say "Hmmm I wonder how hot it will get without a fan...."

---

### Post by xelink on 2007-02-19
no you'de be fine, it would be a straightforward upgrade nothing to change or reconfigure, just swap and go.

same goes for windows.

---

### Post by gradedcheese on 2007-02-20
> PS - never say "Hmmm I wonder how hot it will get without a fan...."

Most CPUs have a temperature sensor.  When the temperature reaches a certain point, the CPU shuts off (this looks like a crash from your perspective).  And that's it... plug the fan in, wait for it to cool, and turn it on again.  if it's cooled down enough, it should just work.  That said, check your motherboard: look at the electrolytic capacitors next to the processor (there should be a whole bunch of them) and make sure none look like they've failed (they usually leak when they fail).  Those fail much more often than the CPU, and they are part of the voltage regulator circuit.  if they are the reason for the failure, then your new CPU will die as well...

---

### Post by terryeden on 2007-02-23
> **xelink said:**
> no you'de be fine, it would be a straightforward upgrade nothing to change or reconfigure, just swap and go.

same goes for windows.

Worked like a charm.  Dropped in the new CPU (with MASSIVE heatsink and fan) and Ubuntu popped up like magic.

T

---

### Post by terryeden on 2007-02-23
> **gradedcheese said:**
> Most CPUs have a temperature sensor.  When the temperature reaches a certain point, the CPU shuts off (this looks like a crash from your perspective).  And that's it...

Big brown mark on the CPU and a faint whiff of magic smoke... it's starting life anew as a keyring!

---

