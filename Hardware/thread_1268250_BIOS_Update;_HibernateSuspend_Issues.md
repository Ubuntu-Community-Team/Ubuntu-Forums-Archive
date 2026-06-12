---
title: "BIOS Update; Hibernate/Suspend Issues"
date: 2009-09-16
forum: Hardware
---

### Post by wrwarwick on 2009-09-16
I just recently purchased an HP DV4-1428DX from Best Buy and have mostly finished the Ubuntu install and configuration. Everything is working besides the hibernate and suspend functions.

I read on another site that a BIOS update may fix the issue. The update from HP's site is an .exe file, which obviously will not run natively on Linux.

Is there any way to run this from ubuntu (I have deleted the windows partition)? Is it safe to run the .exe with WINE? Will the update work correctly from within a VM (I really doubt that would work)?

Any other tips or suggestions on what might be causing the ACPI issues and how to fix them? 

Thanks for all the help.

---

### Post by sergiom99 on 2009-09-16
I had a problem when booting on battery [1] which was easily solved by compiling a custom DSDT file for my hardware. This great how-to by 67GTA [2] will help you do this.

[1] [http://ubuntuforums.org/showthread.php?t=1137421](http://ubuntuforums.org/showthread.php?t=1137421)
[2] [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by wrwarwick on 2009-09-17
I have seemed to isolate the issue. Supsend seems to work correctly. Hibernate works if I disabled compiz and emerald. I have an ATI card running with fglrx.

I have seen some mention of this online...is there any known fix for the error?

---

### Post by wrwarwick on 2009-09-17
Bump.

---

### Post by taamir on 2009-11-03
Bump
i got the same problem

---

