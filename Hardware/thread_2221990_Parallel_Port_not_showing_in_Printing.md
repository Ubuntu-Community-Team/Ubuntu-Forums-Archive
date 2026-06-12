---
title: "Parallel Port not showing in Printing"
date: 2014-05-04
forum: Hardware
---

### Post by Tteddo on 2014-05-04
Hello! I just installed 14.04 (running Gnome Classic) and I can't get my old parallel printer to work. The parallel port does not show up with the command lpinfo -v, just my USB printer. 
When I go to add a new printer, LPT1 or any parallel port isn't even an option. I added parport0 to /etc/modules then rebooted but running "dmesg | grep par" results in the following

[    4.926289] parport0: Printer, Hewlett-Packard HP LaserJet 5L
[    4.926710] lp0: using parport0 (interrupt-driven).

but later on down it says this:

[  373.525865] lp0 releasing parport
[  373.525878] parport0: lp tried to release parport when not owner
[  375.745409] parport0: lp tried to release parport when not owner

I am a member of the lp and lpadmin group. It printed fine under 12.04 this morning.
Any help would be greatly appreciated!

---

### Post by Tteddo on 2014-05-08
So it was a bug:

[Bug Report]("https://bugzilla.redhat.com/show_bug.cgi?id=699052")

Turns out you have to remove the package libsane-hpaio. The version that comes with 14.04 is broken and siezes control of LPT1 and won't let it go. I don't have an HP scanner so I don't need it.

---

