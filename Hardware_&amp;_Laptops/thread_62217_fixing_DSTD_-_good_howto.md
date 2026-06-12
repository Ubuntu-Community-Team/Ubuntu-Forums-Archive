---
title: "fixing DSTD - good howto"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by czeslaw on 2005-09-03
As it is my first post on this forum, let me say hello to all :)

I have spent few hours trying to fix Ubuntu with my Acer TravelMate 2313 NWLMi. Now I can say, that I finished my work with (almost) 100% success :)
The biggest problem was fixing DSTD table, because there was no good dsdt file for my laptop. I've found good faq, saying how to fix DSTD by yourself, basing on what the compiler says. I think, that this address haven't been posted to this forum: [http://www.cpqlinux.com/acpi-howto.html#fix_broken_dsdt](http://www.cpqlinux.com/acpi-howto.html#fix_broken_dsdt)

---

### Post by Confuse on 2005-09-04
[QUOTE=czeslaw]As it is my first post on this forum, let me say hello to all :)

I have spent few hours trying to fix Ubuntu with my Acer TravelMate 2313 NWLMi. Now I can say, that I finished my work with (almost) 100% success :)
The biggest problem was fixing DSTD table, because there was no good dsdt file for my laptop. I've found good faq, saying how to fix DSTD by yourself, basing on what the compiler says. I think, that this address haven't been posted to this forum: [http://www.cpqlinux.com/acpi-howto.html#fix_broken_dsdt](http://www.cpqlinux.com/acpi-howto.html#fix_broken_dsdt)[/QUOTE]

How did you go about implementing your new DSDT.aml? I tried using the initrd method without patching the kernel but that did not work on Breezy (it did work on Hoary though). So did you apply that acpi-dsdt patch to the kernel?

---

### Post by strandlooper on 2005-09-04
Guys

I really look up to you guys who managed to get clear with this DSDT and patch stuff. But be honest, it is expert oriented and not "user-friendly". However I switched to Breezy to get better hardware support for my bad boy (Acer Travelmate 8100). There is a step forward but there is still some work to do on my Notebook and I can't await the day when XP is history on my machine.

Now my topic:    **When Ubuntu kernel 2.6.13 will be part of Breezy repository?**


Cheers

---

### Post by czeslaw on 2005-09-04
Confuse: I have done it on the Hoary, I haven't tried Breezy, so I can't help you. I used the initrd method.

strandlooper: it was hard. Until I found the URL, that is posted above I was desperate, just wanted to give up and come back to Win XP. But applying the instructions that this guy posted makes all the operation just piece of cake :)

---

### Post by gree on 2005-09-05
for others who need to do this, (had to myself with Amilo 7600, or i cant even start X  after the installation)


HOWTO: Fix Common ACPI Problems (DSDT, ECDT, etc.)
[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

didnt read the link above, but thought this link might be handy for others too :)

---

