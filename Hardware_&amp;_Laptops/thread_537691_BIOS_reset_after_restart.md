---
title: "BIOS reset after restart"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by the_twin on 2007-08-29
I have installed Feisty on a HP Pavillion 7940 desktop (dual boot with XP). Generally everything works rather nicely. However if I restart Ubuntu the on-board sound in the BIOS settings is disabled so there is no sound (Via AC97) requiring a BIOS reset. This doesn't happen if I shut the machine down completely and then switch back on, nor if I restart from XP and boot into Ubuntu.

Any clues to the cause of this behaviour?

---

### Post by az on 2007-08-29
> **the_twin said:**
> I have installed Feisty on a HP Pavillion 7940 desktop (dual boot with XP). Generally everything works rather nicely. However if I restart Ubuntu the on-board sound in the BIOS settings is disabled so there is no sound (Via AC97) requiring a BIOS reset. This doesn't happen if I shut the machine down completely and then switch back on, nor if I restart from XP and boot into Ubuntu.

Any clues to the cause of this behaviour?

Can you update the bios?  If you cannot, please file a bug report.  Perhaps this is an ACPI thing?  Are you using APM or ACPI (I don'T know how old your computer is)

Here is a similar  (but different) bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91400](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91400)

"Please check if there is a BIOS update for your system. It's technically not possible for the kernel to directly corrupt the BIOS. It does make calls into the BIOS to perform certain operations (like hibernate), but does not modify the BIOS directly.

Most likely this is a buggy BIOS."

---

### Post by the_twin on 2007-08-29
Thanks for the response.

There doesn't appear to be a BIOS update, at least according to HP website. I think the power management is ACPI, although the documentation I have is pretty light on such details. The machine dates from 2000-2001. It was grinding to a standstill under the weight of Windows and Ubuntu has given it a new lease of life.

There may well be an issue with ACPI. When I first installed Ubuntu the computer would not shut down properly from the desktop, but would power down the hard drive and then hang with the shut down splash screen still visible on the monitor until the power button was pushed which switched it off completely. I cured this behaviour by adding "acpi=force" to the grub menu.lst after finding a relevant thread in the forums. Hibernate does not work properly - the system shuts down and then will not restart normally.

What sort of detail (system logs etc) should I include in a bug report? Apart from the on board sound issue, the BIOS appears unaltered and the computer will boot into Ubuntu or XP, but with no sound device detectable.

---

