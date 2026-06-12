---
title: "Installing Ubuntu on old machine (ca. 2000)"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by anf4 on 2009-02-17
Hi all, and thanks in advance for your help!

I have an old server on which I'd like to install Ubuntu.  This is my first time using it, and I'm doing this both for business (my new company uses Ubuntu for their development machines) and personal (looking to hopefully use the old box as a file server and not weighing it down with a Windows variant).

The server was something I built in college around the year 2000: it's a dual-processor Pentium 3 450MHz (which I think should be enough to run Ubuntu).  The motherboard is a Tyan Tiger 100 ([http://www.tyan.com/archive/products/html/tiger100.html](http://www.tyan.com/archive/products/html/tiger100.html)).

I can successfully boot up the CD.  The first time I attempted to install Ubuntu, I got the following error message:

[INDENT][FONT="Courier New"][   0.000000] ACPI: BIOS age (1999) fails cutoff(2000), acpi=force is required to enable ACPI[/FONT][/INDENT]

I tried adding the [FONT="Courier New"]acpi=force[/FONT] option to the installation, but still got the same error.  I then tried using the [FONT="Courier New"]acpi=off[/FONT] option.  I didn't get the error, but only a blank screen with a blinking cursor in the top left corner appeared.  I let it sit there for a good ten minutes before rebooting.

Does anyone have any tips on what might be going wrong here?  Or another boot option I could try?  Or even a configuration in my BIOS that might be incorrect?  For the record, I've already updated the to latest version of the BIOS (from 2001), and set the BIOS settings to what the installation guide recommended, but I may have missed something.  Any help would be greatly appreciated!

Regards,
Anthony Frasso

---

### Post by anf4 on 2009-02-19
Does anybody have any thoughts on what might be going wrong here?

Thanks,
Anthony Frasso

---

### Post by RJARRRPCGP on 2009-02-19
Looks like you have a buggy motherboard.

---

### Post by 00b00nt00 on 2009-02-21
Have you tried Ubuntu 8.04 instead of 8.10?

---

### Post by Mark Phelps on 2009-02-21
Don't think and older Ubuntu is going to help.  Have read about folks going back to Xubuntu 7.x and still getting the same error.  Since acpi=off doesn't work, the only thing you can try is going into the power management settings in the BIOS and seeing if there is any ACPI setting.

---

### Post by oldos2er on 2009-02-21
How much RAM does it have?

---

