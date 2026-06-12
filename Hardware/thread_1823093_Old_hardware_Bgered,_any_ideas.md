---
title: "Old hardware B**gered, any ideas?"
date: 2011-08-11
forum: Hardware
---

### Post by MG&amp;TL on 2011-08-11
My old 32-bit, 256Mb RAM, Pentium 4, Dell Dimension computer decided not to boot in an interesting way this morning, it reaches GRUB after the BIOS screen, but then booting it yields a pulsing prompt (doesn't do anything, already checked) and a pulsing CAPS and SCROLL lock on the keyboard. It then hangs there. :(

Already checked the obvious connections, motherboard, power, that kind of thing. It boots from live cd or floppy, and I have done several re-installs with different OS, and they all have the same result after removal of live cd. Hardware problem then. Any ideas? Already recovered files using a rescue floppy.
It's my test computer. ( I can't have Linux on anything else, so I'll be restricted to Virtualbox if it doesn't work)

I do appreciate the meaning of 'end of life' though, so if it's truly done for, tell me and I'll salvage componements.

Has anyone had this problem? 

Yours hopefully, MG&TL.

---

### Post by .... on 2011-08-11
Flashing keyboard lights usually (always?) indicates a kernel panic. If a liveCD works, then it sounds like something disk-related, be it the the controller or the disk itself (I'm assuming you verified the liveCD's). If possible move the disk to a different PATA or SATA port and/or run SMART diagnostic check on it.
EDIT: Running memtest wouldn't hurt either.

---

### Post by MG&amp;TL on 2011-08-11
I've heard the phrase before, but wtf's a 'kernel panic'? It sounds bad...

I will move hard drives etc around in the morning (I'm in Europe) But everybody's in bed, so I can't really take the side off my desktop. :D

Thanks for the help. I thought it was a total goner (i.e. broken connection) A kernel panic sounds vaguely organised...

EDIT: I have an IDE hard drive, not a SATA one.

---

### Post by jerrrys on 2011-08-11
[http://en.wikipedia.org/wiki/Kernel_panic](http://en.wikipedia.org/wiki/Kernel_panic)

---

### Post by MG&amp;TL on 2011-08-11
People come up with brilliant names...A 'kernel oops' .....-A squirrel has just dropped his nut! Oops! Oh noes, now he can't find it-KERNEL PANIC! :D

Anyways, thanks for the link. Will look for heat and connection probs in the morning. Would getting a newer BIOS be easier to debug?

---

### Post by MG&amp;TL on 2011-08-12
Memtest seems to be fine...

No obvious loose connections or overheating.

To help, I'm looking for the kernel dump image, where can I find this? I have a rescue floppy from where I can mount the filesystem.

---

### Post by MG&amp;TL on 2011-08-12
Thanks for support guys, turned out the hard drive was dead in some way. New hard drive fixed it.

---

