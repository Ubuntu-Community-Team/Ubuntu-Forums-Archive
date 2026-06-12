---
title: "Ubuntu 16.04 Firewire 1394 - no cam detected"
date: 2019-08-26
forum: Hardware
---

### Post by holger-sven-schumann on 2019-08-26
Folks,

After years not using it, I want to capture DV Cam Videos. The card was detected, but during bootup some error messages show up:

dmesg:

[    1.725080] genirq: Flags mismatch irq 0. 00000080 (firewire_ohci) vs. 00015a00 (timer)
[    1.725131] firewire_ohci 0000:03:07.0: failed to allocate interrupt 0
[    1.725189] firewire_ohci: probe of 0000:03:07.0 failed with error -5

lcpci:
03:07.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)

starting dvgrab:
Error: no camera exists

The DV cam is a JVC GR-DVL140E

Ideas?

Rgds.
Holger

---

### Post by holger-sven-schumann on 2019-08-26
...Update - the firewire card was out of an old PC, so it looks like no longer supported. Changed to an actual model which works with standard Ubuntu 16.04. Boot failures gone now.

For reference of compatible firewire chipsets
lspci:
03:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

This thread can be closed.


Rgds.
Holger

---

