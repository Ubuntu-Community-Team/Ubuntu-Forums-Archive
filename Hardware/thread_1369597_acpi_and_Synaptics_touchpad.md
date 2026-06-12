---
title: "acpi and Synaptics touchpad"
date: 2010-01-01
forum: Hardware
---

### Post by james_mcl on 2010-01-01
I recently booted into Karmic with acpi=off (I was trying to find out if a bug I've been experiencing was kernel bug 9147). This had the side-effect of disabling my touchpad.

I tried adding i8042.nomux=1, but this didn't help.

Does anyone know of a workaround I can use to get the touchpad working with acpi=off, or is there nothing for it but to remove that boot option?

Thanks,

James.

---

### Post by james_mcl on 2010-01-05
bump

---

### Post by silent_shade on 2013-03-12
That's a pretty old thread but the problem remains so here are my two cents.

After kernel upgrade I've got cpu soft lockups during boot which was cured by adding 
"acpi=off" to /etc/default/grub. This solution killed my touchpad though, just as it did for james_mcl above.
Luckily, acpi=off is not the only possible option. There are also
acpi=oldboot
Deactivates the ACPI system almost completely; only the components required for the boot process will be used.
acpi=ht
Deactivates the ACPI system almost completely; only the components required for hyper threading will be used.
acpi.power_nocheck=1 OR acpi_osi=linux
The first one, acpi=oldboot, worked for me, although the boot duration increased somewhat.

I'll add some generalized instructions in case someone would need them 
To try things out at the boot time, when GRUB starts, press "e" - that's for editing, and add various options one at a time, them Ctrl-x and see what happens. With the best variant go to /etc/default/grub and don't forget to sudo update-grub to preserve changes.

This is hardly a solution, but it brings the usable laptop back

---

### Post by overdrank on 2013-03-12
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

