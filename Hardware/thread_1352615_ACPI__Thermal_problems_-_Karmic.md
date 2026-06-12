---
title: "ACPI / Thermal problems - Karmic"
date: 2009-12-11
forum: Hardware
---

### Post by fipeflip on 2009-12-11
I own a acer 5720 laptop. I recently upgraded to karmic from jaunty. When I started working, I noticed some heat problems. Using lmsensors, I see core temperature increase constantly (raising even to 85 C), but acpi temperature does not suffer any change. 
I found this issue:
 ACPI: BIOS _OSI(Linux) query ignored
 ACPI: EC: non-query interrupt received, switching to interrupt mode
 ACPI: Interpreter enabled
ACPI: (supports S0 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
 ACPI: EC: driver started in interrupt mode
ACPI: No dock devices found.
ACPI Warning: \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 20090521 nspredef-328
 ACPI: PCI Root Bridge [PCI0] (0000:00)


I have update to the newest kernel, but the problem was not solved.
What could I do?
Thanks.
Greetings from Brazil.

---

### Post by fipeflip on 2009-12-12
any ideas?

---

### Post by thegladaitor on 2009-12-12
My laptop is overheating ever since I installed updates .

---

### Post by peterroots on 2009-12-12
this might help
[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)
but it did not work for me
see also
[http://ubuntuforums.org/showthread.php?p=8485744](http://ubuntuforums.org/showthread.php?p=8485744)

---

### Post by mhousel on 2009-12-29
> **peterroots said:**
> this might help
[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)
but it did not work for me
see also
[http://ubuntuforums.org/showthread.php?p=8485744](http://ubuntuforums.org/showthread.php?p=8485744)

Neither of these fixed anything on my Toshiba P105 that the fans run TOO SLOWLY on.

Lots of people worried about fan noise and wanting them to be oof, heck I'd love to have that problem.

I'm wondering if there is anyone on this forum that really knows, in detail, how all of this ACPI control stuff works, gets configured, gets controlled, etc.

Someone had to design this stuff?

---

