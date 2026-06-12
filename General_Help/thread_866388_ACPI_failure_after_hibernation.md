---
title: "ACPI failure after hibernation"
date: 2008-07-21
forum: General Help
---

### Post by Torsion on 2008-07-21
Hello, after enabling hibernation and upon powering up the computer this morning I noticed an ACPI failure / disabled message.  My other system seemed to have problems hibernating in Ubuntu as well, but always recovered from the errors and beeping after a few reboots.

I'm also running Windows XP in a dual boot and it won't go past a blue screen message about the ACPI.  So this makes me think it's something hardware or the bios is corrupted.  However, my other system had the same problems with hibernating in Ubuntu.  I only hope something hasn't been internally damaged.  Thank you.

---

### Post by Torsion on 2008-07-21
Here are the error messages.

```

[   13.889322] ACPI: Core revision 20070126
[   13.889363] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.895928] ACPI Error (hwacpi-0142): Hardware did not change modes [20070126]
[   13.895930] ACPI Error (evxfevnt-0086): Could not transition to ACPI mode [20070126]
[   13.895933] ACPI Warning (utxface-0139): AcpiEnable failed [20070126]
[   13.895935] ACPI: Unable to enable ACPI

```

I think Ubuntu messed up my bios. :(  I've tried disabling acpi in grub but it still comes up with this.  Everything seemed to be working well until I enabled hibernation.  I've since reinstalled and still no luck, because somehow my hardware has acpi disabled.

---

### Post by Torsion on 2008-07-23
Well these are obviously very busy forums.  However, for the sake of those seaching, my problem was solved by pulling the motherboard battery for 5 minutes to reset the CMOS.

But it WAS Ubuntu that made this happen!  And also had the same problems with my Dell...

---

