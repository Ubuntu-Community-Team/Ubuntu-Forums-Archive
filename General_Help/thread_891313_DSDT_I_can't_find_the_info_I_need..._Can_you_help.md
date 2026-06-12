---
title: "DSDT I can't find the info I need... Can you help?"
date: 2008-08-15
forum: General Help
---

### Post by HunterThomson on 2008-08-15
Ello,

The Lenovo Ideapad's have a problem with the backlight... It looks like it is a problem with the DSDT. So, I was going to recompile the DSDT to see if I get any errors.... However, when I try to disassemble it I run into problems that I don't know how to fix and I can't find any info in the WIKI's.

I try this...

```
cp /proc/acpi/dsdt DSDT
```

```
acpixtract DSDT acpidump > DSDT.dat
```

```
iasl -d DSDT.dat
```

When I try to disasemble it with iasl I get this error...

```
Intel ACPI Component Architecture
AML Disassembler version 20061109 [Apr 27 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file DSDT.dat
Could not read the table header
Could not get table from the file

```

---

### Post by HunterThomson on 2008-08-16
Bump

---

### Post by HunterThomson on 2008-08-16
Bump bump.....

---

### Post by HunterThomson on 2008-08-16
I don't have a TABLE.dat file.....

```
 sudo acpidump > acpidump.out
Password: 
Wrong checksum for ATKG
Wrong checksum for ATKG!
```

```
 ls
APIC.dat  DSDT.dat   FACP2.dat  HPET.dat  RSDP.dat  SSDT.dat
ATKG.dat  ECDT.dat   FACS.dat   MCFG.dat  RSDT.dat  XSDT.dat
BOOT.dat  FACP1.dat  GSCI.dat   OEMB.dat  SLIC.dat

```
```


Intel ACPI Component Architecture
AML Disassembler version 20061109 [Apr 27 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file DSDT.dat
Could not read the table header
Could not get table from the file

```

---

### Post by HunterThomson on 2008-08-17
OK... I was stupid... Well the documetation I was reading was unclear...
Anyway, I have now dissasembled and reasembled the DSDT.dat file with ASL... And guess what.... The Micosoft compiler is junk and mised some errors.... The Open Sorce intel compiler I used found and error and 12 wornings... I am going to play with it I'lll be back to tell you how it turns out....

```
DSDT.dsl 13624:                 Name (_T_0, Zero)
Error    4081 -     Use of reserved word ^  (_T_0)

ASL Input:  DSDT.dsl - 13995 lines, 402087 bytes, 6667 keywords
Compilation complete. 1 Errors, 12 Warnings, 0 Remarks, 36 Optimizations

```


"It seems unfortunate if we do this work and get our
partners to do the work and the result is that Linux works great without
having to do the work" (Bill Gates on Making ACPI Not Work with Linux,
[http://www.osnews.com/story.php/17689/Bill-Gates-on-Makin](http://www.osnews.com/story.php/17689/Bill-Gates-on-Makin)...)

---

