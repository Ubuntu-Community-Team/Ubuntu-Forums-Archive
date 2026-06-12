---
title: "Fix for excessive Load_Cycle_Count Hardy"
date: 2008-12-01
forum: Hardware
---

### Post by stchman on 2008-12-01
I found a wiki that fixed my excessive Load_Cycle_Count.  I applied the fix and left the laptop on for over two hours without the count increasing.

[https://wiki.edubuntu.org/PowerManagement](https://wiki.edubuntu.org/PowerManagement)

Go to the section 

How to get disks idleing correctly (without excessive load cycling)

This worked perfectly on my Toshiba laptop.  Do what the four bullets tell you.

---

### Post by bluelamp999 on 2008-12-03
Hi,

So all you have to do in 8.10 is the below?

Current state in Ubuntu 8.10 is:

You still need to "ENABLE_LAPTOP_MODE=true" in /etc/default/acpi-support (Bug 244838 fixed in acpi-support 0.111?)

Cheers

---

