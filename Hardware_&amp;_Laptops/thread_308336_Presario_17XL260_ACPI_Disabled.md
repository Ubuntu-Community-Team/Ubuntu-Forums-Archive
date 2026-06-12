---
title: "Presario 17XL260 ACPI Disabled"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by MudCrab on 2006-11-27
I just installed Ubuntu 6.06 LTS on my Compaq Presario 17XL260 laptop. It seems to run okay except it does not display battery status and locks up when it gets to the "halt" line when I shut down. It will restart correctly, though.

I have done some searching on this forum, but haven't found a way to get the battery icon to show up. Apparently, the ACPI support is not being installed. I get the following message when the computer boots:

Presario kernel: [4294667.296000] ACPI: Vendor "PTLTD " System " DSDT " Revision 0x6040000 has a known ACPI BIOS problem.

... ACPI: Reason: Multiple problems. This is a non-rocoverable error.

... ACPI: Disabling ACPI support.

Is there a way to enable ACPI support or to make it where I can tell how much battery run-time remains? I can always guess, but if I miss it I assume the computer will just shut off and any open files will be lost.

Laptop: Compaq Presario 17XL260, 500MHz PIII, 320MB RAM, 20GB HD, DVD-ROM

---

### Post by MudCrab on 2006-11-28
Per posts on this forum I have tried adding the "apm power_off=1" to the /etc/modules file. This didn't seem to do anything.

I also tried adding the "acpi=force" to the startup line in /boot/grub/menu.lst
This did let the computer shut down, but there are a lot of ACPI errors on startup and the battery icon shows 0%. Because this doesn't show the correct information can it hurt the computer or the battery? Perhaps charge incorrectly?

Is it better to just shut off the computer manually or is there a fix for this?

---

