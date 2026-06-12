---
title: "[SOLVED] Bebugging my DSDT file"
date: 2008-06-13
forum: Hardware
---

### Post by davidryderuk on 2008-06-13
Hi,

I am trying to fix errors which are reported when i recompile my DSDT file, in the hope it will fix fan control on my laptop. The output i get when following instructions such as this one ([http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)) and the one found here ([http://ubuntuforums.org/showthread.php?t=482900](http://ubuntuforums.org/showthread.php?t=482900)) is shown below.

> Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

DSDT.dsl   177:     Method (\_WAK, 1, NotSerialized)
Warning  1079 -                 ^ Reserved method must return a value (_WAK)

DSDT.dsl  1844:                             CreateByteField (RSR2, \_SB.PCI0.PIB.SYSR._CRS._Y0B._DEC, BULG)
Error    4007 -                             Field offset is in bits, but a byte offset is required ^ 

ASL Input:  DSDT.dsl - 3686 lines, 125970 bytes, 1644 keywords
Compilation complete. 1 Errors, 1 Warnings, 0 Remarks, 536 Optimizations


The first warning goes away after editing the DSDT.dsl file following instructions found in the first link shown above and recompiling, however after inputting the following command

> dpkg-reconfigure linux-image-`uname -r` .

restarting the computer and repeating the procedure the warning is again reported upon recompiling the DSDT file, and the DSDT.dsl file that is outputted the second time is the original file not the edited one. I believe this is related to the command 

> iasl -tc dsdt.dsl

only outputting a .hex file and not a .aml file.

Can anyone tell me how i could make bug fixes in the DSDT.dsl file more permanent? Also if anyone knows how i would fix the second error that would also be helpful. Thanks for any assistance.

Edit: The aml file was produced after i fixed the second error (CreateByteField > CreateBiteField)

---

