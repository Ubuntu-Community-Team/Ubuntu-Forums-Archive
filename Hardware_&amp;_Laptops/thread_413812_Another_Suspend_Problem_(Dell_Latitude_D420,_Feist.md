---
title: "Another Suspend Problem (Dell Latitude D420, Feisty)"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by Bubbel on 2007-04-19
Well, I'm surely not the first, but I have problems with suspend/hibernate.
I've seen it working with an erarly (beta) kernel version of Feisty, but now it doesn't go to standby.

The screen will turn off (Suspend) or I get a blinking cursor (Hibernate). It won't go to standby mode.
Num-Lock still works, but the machine is not responding any further. A hard power-off is the only option.

Tried:
 Compiz off
 Ndiswrapper for WiFi
 Hibernate/Suspend2
 Uswsup (s2ram/S2disk)

. . .Help. . .?

---

### Post by bloodniece on 2007-04-19
I had the opposite problem of Feisty going to sleep and never waking up.  After upgrading to beta it stopped doing that.  Maybe /enabledisable acpi at the BIOS level would help.

---

### Post by Bubbel on 2007-04-20
Well. Tried to find that one, but the BIOS of this laptop doesn't have the option to turn ACPI off. It also lacked support to select S1 or S3 Suspend.

Thanks for the tip. Do you have any more to try out?

---

