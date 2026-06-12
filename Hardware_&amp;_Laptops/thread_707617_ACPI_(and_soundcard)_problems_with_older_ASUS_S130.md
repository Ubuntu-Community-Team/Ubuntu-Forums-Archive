---
title: "ACPI (and soundcard) problems with older ASUS S1300N laptop"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by lukanova on 2008-02-25
hi all

i was thinking to ask this finally here as the last resort before i try compiling the kernel (still kinda tedious job, despite the 8years with linux).

i have an older asus s1300n laptop here that i'm migrating from debian to ubuntu. on debian i got the ACPI and sound working (sound needs acpi to work) by compiling my own kernel which had APM disabled. also custom DSDT (0205 i think) was compiled in. i was hoping that i would be able to use generic kernel from ubuntu with this buggy ACPI implementation on the laptop somehow resolved. after many hours of trying to use DSDT in initramfs image and trying various options on the command line, the only thing that doesn't freeze the boot at something like (the numbers are a bit different)

```
PCI: Using Configuration Type 1
ACPI: EC: GPE=0x16, ports = 0x66 , 0x66
```

is to pass acpi=off to the kernel at bootup (or grub). which disabled acpi and therefore sound. the soundcard does appear in lspci and intel8x0 was working in the old setup with debian and custom

the kernel is the current one - 
a# uname -a
Linux kiklop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
it's a  linux-image-2.6.22-14-generic 

i now also updated the bios to 0206, and i'm not sure if custom DSDT 0205 from acpi.sf.net is now suitable to be used.

also, is there a way to disable APM in the generic ubuntu kernel?

maybe somebody has a clue or pointer. would appreciate.

---

