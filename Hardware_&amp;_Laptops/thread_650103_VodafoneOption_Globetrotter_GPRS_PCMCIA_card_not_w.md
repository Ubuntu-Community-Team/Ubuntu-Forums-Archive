---
title: "Vodafone/Option Globetrotter GPRS PCMCIA card not working"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by Truthiswithin on 2007-12-25
Trying to get a Vodafone Mobile Connect Card (aka Option Globetrotter WP0239A0PD) GPRS PCMCIA card working under Gutsy, to no avail.  I've tried the howto on pharscape.org but when I stick the card into the slot, then check dmesg, it says something like:

PCMCIA: CIS Filename is too long

I tried it on another notebook and got the same error and another error after it, something like:

serial_cs: ttyS01 at port 0x02f8 (irq = 3) error

sorry, can't remember the exact error right now, as that notebook is not here now.  Using WinXP to write this now, under which the supplied Vodafone driver works fine.

Any other links or helpful suggestions I've missed?

---

### Post by Truthiswithin on 2007-12-29
Here's the exact error sequence on the second notebook:

Dec 29 08:28:05 noah-laptop kernel: [ 1178.312000] pccard: PCMCIA card inserted into slot 1
Dec 29 08:28:05 noah-laptop kernel: [ 1178.312000] pcmcia: registering new device pcmcia1.0
Dec 29 08:28:05 noah-laptop kernel: [ 1178.312000] pcmcia: CIS filename is too long
Dec 29 08:28:05 noah-laptop kernel: [ 1178.320000] pcmcia: CIS filename is too long
Dec 29 08:28:05 noah-laptop kernel: [ 1178.360000] serial_cs: serial8250_register_port() at 0x02f8, irq 3 failed
Dec 29 08:28:05 noah-laptop NetworkManager: <debug> [1198891685.675796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 

I understand that the problem is that the CIS filename (GLOBETROTTER.dat) is longer than the allowed 13 bytes.  I've tried redirecting it in the /etc/pcmcia/config.opts to a flie called /etc/pcmcia/cis/GLOBE.dat but the error is the same.

I have seen that I can patch the kernel, but I have no idea how and without a good internet connection, not much hope of downloading and compiling the source.

Any help?

---

