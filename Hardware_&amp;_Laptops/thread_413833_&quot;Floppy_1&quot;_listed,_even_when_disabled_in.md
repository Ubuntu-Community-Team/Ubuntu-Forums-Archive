---
title: "&quot;Floppy 1&quot; listed, even when disabled in BIOS"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by iain_m on 2007-04-19
Hi

I'm using 7.04. This is a niggling problem: Under 'Places -> Computer', a drive called 'floppy 1' is listed, even though my floppy drive controller is disabled in the BIOS.

I am, incidentally, using an Intel D865PERL motherboard.

When the floppy is enabled in BIOS, a 'floppy drive' appears accordingly in 'Computer'. This is *in addition to* the 'floppy 1'.

'Floppy drive' can be successfully mounted and its contents browsed when a floppy is in the drive.

I have tried to move 'floppy 1' to trash but I get this message:

*Error "Operation not permitted" while deleting "computer://...5201.drive".*

Any ideas? Thanks.

---

### Post by psusi on 2007-04-19
Can you open the Floppy 1 when you put a disk in the drive?  Are you sure that you disabled the second floppy in the bios?

---

### Post by iain_m on 2007-04-19
Hi,

To answer your questions in turn -

- No, Floppy 1 doesn't open even with a floppy in the drive. I get the message:[I]

Unable to mount the selected floppy drive.
mount: /dev/ is not a block device[/I]

- There is no second floppy option in the bios. Floppy 1 appears even with the floppy options completely disabled in the bios.

BTW I tried opening a terminal and typing sudo nautilus, but this didn't enable me to delete floppy 1.

**UPDATE: SOLVED** (for now - I think). From fstab I removed the line:

```
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

Now in 'Computer' I see 'Floppy Drive', but no 'Floppy 1'. I can successfully mount a floppy disk inserted in the drive by clicking 'Floppy Drive'. :)

---

