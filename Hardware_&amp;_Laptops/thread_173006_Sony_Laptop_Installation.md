---
title: "Sony Laptop Installation"
date: 2006-05-09
forum: Hardware &amp; Laptops
---

### Post by jaxplace on 2006-05-09
I am having difficulty in installing the 5.10 version on a Sony PCG-FX120 laptop.  The process stops responding after the line:
ACPI: Subsystem revision 20050729

I have deleted all partitions and am attempting to run on an unallocated partition.

Any Ideas?

---

### Post by souki on 2006-05-09
maybe try booting with 'acpi=off' option

---

### Post by dilmah on 2006-07-28
> **souki said:**
> maybe try booting with 'acpi=off' option
Sweet! You just fixed my installation woes with a Sony PCG-FX770K (an old 650MHz Pentium III laptop).

Previously the screen just blanked out after the ACPI line, but I could hear the CD loading stuff behind the scenes and when I pressed CTRL+ALT+DEL it even shut down properly and ejected the CD.

With ACPI off though, I can see it all.... looking awesome so far! *crosses fingers*

---

