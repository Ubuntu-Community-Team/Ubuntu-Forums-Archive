---
title: "install server on LSI MegaRAID SAS 8204XLP controller?"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by AndyVe on 2008-01-08
Has anyone had any luck installing ubuntu on a drive controlled by this card?

Based on [Serial Attached SCSI (SAS) chipsets — Linux support status]("http://linuxmafia.com/faq/Hardware/sas.html") it seems that these cards should be use mptsas as their driver but that doesn't work when I try to install using it.  I tried mpt* and megaraid* as well without luck.

Thanks,
Andy

---

### Post by AndyVe on 2008-01-08
Just dug into the code that comes with the SLES install.

That driver is actually MEGASR.  Saw a note from a linux mailing forum about a jumper for some other 1068 based cards that lets you switch from Fusion to MegaSR modes.  The docs from LSI dont show this jumper though for the 8204XLP.

---

### Post by eL_vErDe on 2008-02-26
I made a package for it.

It works fine with Debian Etch kernel and may work with the Ubuntu kernel.
If it doesn't work, look at debian/rules and try with another binary objects (I used sles10's one for the etch kernel).

[http://mentors.debian.net/debian/pool/non-free/m/megasr/](http://mentors.debian.net/debian/pool/non-free/m/megasr/)

Regards, Adam.

---

