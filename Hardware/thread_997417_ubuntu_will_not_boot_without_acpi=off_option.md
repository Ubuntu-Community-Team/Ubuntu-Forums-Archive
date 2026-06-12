---
title: "ubuntu will not boot without acpi=off option"
date: 2008-11-29
forum: Hardware
---

### Post by feydrutha on 2008-11-29
I have installed intrepid on an asus a6km (a6000km, this is an oldish model with an AMD sempron CPU).

The system would not boot (also the desktop installer would not boot) until I quite randomly discovered that I needed to add acpi=off to the boot options.

Without this option it simply hangs as soon as it starts to boot.

The last version of ubuntu I had tried on this machine was feisty, which worked ok as far as I can remember, at least it did not have this specific problem.

Now I have 2 strange things happening on this machine which may be connected to acpi being disabled:

1- there is no cpu frequency scaling (CPU always runs at max clock rate)
2- system doesn't power itself off when I shut it down

So my questions are:
anyone have an idea of how I can figure out what's wrong with acpi and how to work around it?

what are the consequences of acpi being disabled? are those 2 issues direct consequences or should I be looking for separate causes?

thanks in advance

EDIT: actually, now that I think of it feisty also had some acpi problems, just different ones. It would hang on boot if a USB mouse or keyboard was connected, as was reported here: [https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6Km](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6Km)

---

### Post by feydrutha on 2008-11-30
Ok, I have investigated the matter a bit further, this is in fact the same bug I had under feisty, I had just found a different workaround. So much for posting at 3 am.

The system will hang on boot if ANYTHING is plugged into it's USB ports, unless acpi=off is set in the boot options.

Without the acpi=off option the cpu frequency scaling and shutdown issues I was having disappear.

I think for now I will choose the "unplug usb devices at boot" workaround.

If I can find a better solution I will report it here.

Any suggestions are still welcome.

---

