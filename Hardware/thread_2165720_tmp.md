---
title: "/tmp"
date: 2013-08-06
forum: Hardware
---

### Post by linuxonbute on 2013-08-06
I noticed that on booting my laptop there was a message which appeared briefly, it said 

"/tmp not ready " or something like that - I am sure it was to do with /tmp but it was so brief I could barely get my eyes focused 

on it.

Any idea if it's a real problem?

I looked at the output of dmesg and came across the following:

[   19.005273] ACPI Warning: 0x00001060-0x0000107f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   19.005286] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

Has this anything to do with the above?
tia
Norm

---

