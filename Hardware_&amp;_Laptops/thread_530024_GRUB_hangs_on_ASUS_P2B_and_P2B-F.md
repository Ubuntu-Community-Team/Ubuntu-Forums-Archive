---
title: "GRUB hangs on ASUS P2B and P2B-F"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by likes2skate on 2007-08-20
Hello world,

After installing 6.06 server, the screen says this on boot:

[INDENT]GRUB Loading stage 1.5.

GRUB loading, please wait...
[/INDENT]

That's it -- no error message, just a hung boot.

It says this when I boot on an ASUS P2B or P2B-F.  The same hard drive boots no problem on an ASUS P3B-F.

It fails to boot on an ASUS P2B or P2B-F both when I do the install using an ASUS P2B or P3B-F.   That is, I can install on the hard drive using either a P2B or P3B-F.  Whether I install using a P2B or P3B-F, ubuntu will boot on a P3B-F but not a P2B or P2B-F.

I updated the BIOS on the P2B to the most recent version.

I tried different CMOS settings for the hard drive (LBA and Normal), and did the install over.

I tried booting on a P3B-F, and editing /boot/grub/menu.lst there to put these on the kernel line:

[INDENT]ide=nodma apm=off acpi=off noapic nolapic noacpi
[/INDENT]

GRUB still hangs on a P2B or P2B-F.

The CPU is a P2 266 MHz.  There is plenty of memory (128 megs x 3).  

Is there hope for ubuntu on the P2B and P2B-F?

Thanks,

Rick

---

### Post by likes2skate on 2007-08-20
Oops!

Searching in a Debian forum, I found a post that said the solution was to set the drive to LBA.

Sure enough, that worked!

> I tried different CMOS settings for the hard drive (LBA and Normal) ...

I guess not carefully enough.

Yeah!  Its working!

Sorry to bother you.

---

