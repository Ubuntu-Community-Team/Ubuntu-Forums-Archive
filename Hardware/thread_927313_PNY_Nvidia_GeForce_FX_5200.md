---
title: "PNY Nvidia GeForce FX 5200"
date: 2008-09-22
forum: Hardware
---

### Post by Lt. Sullust on 2008-09-22
Hello all,

I've recently added the listed graphics card to my computer.  After trying to enable it (and failing) through various methods on these forums.  

I've decided that it might be easier to create install a second ubuntu partition while attached to the PCI card so that Ubuntu sees that as the default.

Unfortunately, I seem to have hit a snag there as well.  When I used the text install, I get a bunch of 'Buffer I/O error on device fd0, logical block 0' errors.  If I wait long enough it will proceed to the graphical/text interface; however, this presents more problems.

Whenever I press a key it enters that value twice.  For example, if I press 'a', 'aa' is printed to the screen.  This makes navigating the menus difficult since the arrow keys are all doubled as well.  Secondly, it then complains about not being able to locate the cd-rom drive.  I find this odd since that's what I'm installing from.  

Any help?

EDIT: I should also mention that there is no floppy drive on this computer.

---

### Post by Lt. Sullust on 2008-09-22
I did a bit more reading on the forums and went into the BIOS and made sure that the Floppy Drive was disabled.

I also added all_generic_ide on the ubuntu text installer.  Here's the resulting output:

ACPI: Unable to start the ACPI Interpreter
ata_piix 000:00:1f.2: invalid MAP value 0
ata3.00: failed to set xfermode (err_mask=0x40)
ata3.00 revalidation failed (errno=-5)
ata3.00 revalidation failed (errno=-5)
ata3.01 failed to set xfermode (err_mask_0x40)
ata3.01 failed to set xfermode (err_mask_0x40)
ata3.01 failed to set xfermode (err_mask_0x40)

After this it gets to the first graphical/text screen of the installer; however, the display is several thin vertical lines...

---

### Post by SyL on 2008-11-25
Hi,

Did you manage to get anything running?

---

