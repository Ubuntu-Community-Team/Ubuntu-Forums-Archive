---
title: "ACPI: expecting a [Reference] package element, found type 0"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by IsmAvatar on 2009-05-28
After upgrading from 8.10 (Intrepid) to 9.04 (Jaunty), I started receiving this line of text on boot up, after grub but before the graphical loading bar. It pauses on this text for about 5 seconds, so presumably this message is unnecessarily extending my loading time. The line is:
ACPI: expecting a [Reference] package element, found type 0

Of course I don't have a clue what it means. Presumably it has something to do with the Advanced Configuration and Power Interface (ACPI) driver.
Is there any way to fix it or make it go away? Or at least make it not sit there for 5 seconds...

---

### Post by Raskula on 2009-06-04
Many Many people have the same problem, including me. I think it's because of the new bootloader or the new linux kernel.

So I just won't upgrade until they fix this problem.

---

### Post by abnerion on 2009-06-21
I have the same problem.

I solved the problem by deactivating the ACPI from the BIOS but when the computer halts, the computer don't power off automaticly.

------
Using kernel 2.6.26.

---

### Post by ohnoezitasploded on 2009-09-24
Ditto here.  Running 9.04 with an Asus M2N-SLI Deluxe motherboard.

This problem seems like it's very common, amongst different distros and hardware configurations, here's hoping a fix is forthcoming.

---

