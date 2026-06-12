---
title: "HP LaserJet 2100 Prints Only One Line of Garbage"
date: 2014-01-25
forum: Hardware
---

### Post by Lane_Lester on 2014-01-25
Someone gave me an HP LaserJet 2100, and I've hooked it to my Ubuntu 12.04 system with the parallel port. The printer's internal test page prints OK, but I anything I try to print from Ubuntu prints just one line of garbage characters and then ejects the paper.

A minor nuisance is that the print job goes to the printer, but it will not print until I press the Go button.

I changed the BIOS parallel port setting from SPP to EPP+ESD (or whatever those two were). It had no effect.

I've tried both the recommended non-PS and PS driverslisted for this printer, but they both produce the same result.

I'm using this connection in CUPS: parallel:/dev/lp0

I should mention I read about 20 threads about similar problems, but none provided a solution that worked for me.

Lane

---

### Post by Lane_Lester on 2014-01-26
OK, I finally found another computer old enough to have a parallel port (ancient HP laptop). The printer worked fine on it, so the problem is with my desktop machine. The parallel port is on the motherboard, so I may think about trying a separate parallel adapter in it.

Lane

---

### Post by LaneLester on 2014-01-29
I bought a Belkin parallel to usb adapter and followed the following procedure
[INDENT]Add your printer by selecting a different connection type (since usb and parallel will not be listed)
Close CUPS in browser.
Edit the file /etc/cups/printers.conf
Change the DeviceID line to read: DeviceURI parallel:/dev/usb/lp0 

You probably need to execute this to get the dev to show up:
modprobe usblp[/INDENT]

Lane

---

