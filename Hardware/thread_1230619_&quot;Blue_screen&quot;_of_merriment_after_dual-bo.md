---
title: "&quot;Blue screen&quot; of merriment after dual-boot install of jaunty"
date: 2009-08-03
forum: Hardware
---

### Post by Tink on 2009-08-03
Hi,

Last night I installed kubuntu 9.04 on a friends
Dell Inspiron 6000 (after resizing the NTFS partition
from a RIP live CD). After the resize the machine still
happily booted XP home.

After the jaunty installation (and the grub-install?) it
only sh*ts itself, giving me a "blue screen", saying
that there's a problem with the boot volume.

XP is on partition /dev/sda2 (/dev/sda1 has a small  DELL 
utility partition with hardware diagnostics) ... I've 
played around with a variety of grub options for the 
windows partition, including hiding the utility partition,
but no joy.

Has anyone here encountered similar problems, and, more
importantly, successfully got windows to boot again?



Cheers,
Tink

---

### Post by quixote on 2009-08-04
Sounds like grub may have overwritten part of the Master Boot Record.  This is easy to fix if you have a Windows boot medium, a bootable CD, or even a floppy if your computer has such a Stone Age device.  This is from memory, so first search for "fixmbr" to make sure I have my facts right.

What I remember is this: boot into a recovery console.  Assuming that's A: and /dev/sda is C: according to Windows, at the A: prompt you'd type ```
A: fixmbr c:
```

---

