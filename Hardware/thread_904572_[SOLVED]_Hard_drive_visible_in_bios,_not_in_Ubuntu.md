---
title: "[SOLVED] Hard drive visible in bios, not in Ubuntu"
date: 2008-08-29
forum: Hardware
---

### Post by AusIV4 on 2008-08-29
I have a system that has been running off of a 200 GB SATA drive.

For a script I'm writing, I wanted to try some stuff on a smaller, unimportant hard drive. I've installed an old 40 GB IDE drive. It is recognized in BIOS (I have the option to boot off of it), but Linux gives no indication that it is present.

*fdisk -l* only tells me about the SATA drive.

*lshw -C disk* tells me about the CD drive and the SATA disk.

Is there a kernel module that might not be loaded since the install was done without any IDE drives connected?

Any help is appreciated.

---

### Post by AusIV4 on 2008-09-05
Turns out the jumper on the hard drive was set as "Master with slave" when it was just a master. I didn't think jumper settings mattered much any more, apparently I was wrong.

Marking as solved.

---

