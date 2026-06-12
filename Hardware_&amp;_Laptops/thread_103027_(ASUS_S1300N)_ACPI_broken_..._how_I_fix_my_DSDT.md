---
title: "(ASUS S1300N) ACPI broken ... how I fix my DSDT?"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by bennibuntu on 2005-12-13
Hello

I already posted this problem in ubuntusers.de, but no answer yet. so I hope, I'll get help from you.

I tryed to install Breezy on my Laptop, an Asus S1300N. But without the bootprompt 'acpi=off' the installation fails. that is not acceptable, beacause my sound is now out off funktion.

Now I think my DSDT-table isn't well compiled. Thats what the intel compiler says:

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20051117 [Nov 30 2005]
Copyright (C) 2000 - 2005 Intel Corporation
Supports ACPI Specification Revision 3.0

dsdt.dsl 2075: Store (ACAP (), \ACPF)
Warning 2090 - ^ Called method may not always return a value

dsdt.dsl 2171: If (ACAP ())
Warning 2090 - ^ Called method may not always return a value

dsdt.dsl 2216: Method (ACAP, 0, Serialized)
Warning 2085 - ^ Not all control paths return a value (ACAP)

dsdt.dsl 2243: Method (BATP, 1, Serialized)
Warning 2085 - ^ Not all control paths return a value (BATP)

dsdt.dsl 2824: Return (\_SB.PCI0.SBRG.EC0.ACAP ())
Warning 2090 - Called method may not always return a value ^

dsdt.dsl 2839: If (ACAP ())
Warning 2090 - ^ Called method may not always return a value

dsdt.dsl 2918: If (\_SB.PCI0.SBRG.EC0.BATP (0x00))
Warning 2090 - Called method may not always return a value ^

dsdt.dsl 2964: If (LNot (\_SB.PCI0.SBRG.EC0.BATP (0x00)))
Warning 2090 - Called method may not always return a value ^

dsdt.dsl 3008: If (LNot (\_SB.PCI0.SBRG.EC0.BATP (0x00)))
Warning 2090 - Called method may not always return a value ^

dsdt.dsl 3018: If (\_SB.PCI0.SBRG.EC0.ACAP ())
Warning 2090 - Called method may not always return a value ^

dsdt.dsl 3095: If (LNot (BATP (0x00)))
Warning 2090 - ^ Called method may not always return a value

dsdt.dsl 3127: If (BATP (0x00))
Warning 2090 - ^ Called method may not always return a value

dsdt.dsl 3136: If (BATP (0x00))
Warning 2090 - ^ Called method may not always return a value

dsdt.dsl 4114: If (\_SB.PCI0.SBRG.EC0.ACAP ())
Warning 2090 - Called method may not always return a value ^
```

May any of you give me help to fixe it. I have no idea how to do it myself.

by the way, my bios is up-to-date. 0206 and there isn't a dsdt-patch available on [http://acpi.sourceforge.net/dsdt/view.php]("http://acpi.sourceforge.net/dsdt/view.php")

another hint: a test with SUSE (kernel 2.6.13-15) works. no acpi-problems.

thanks a lot
benni

---

