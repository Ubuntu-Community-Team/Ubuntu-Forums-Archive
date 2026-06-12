---
title: "Shutting Down Issue with Medion MIM2230 Laptop"
date: 2009-03-07
forum: Hardware
---

### Post by thunderpants on 2009-03-07
Hi, I have a Medion MIM2230 Laptop that I have loaded with TinyXp/ Ubuntu 8.10.All works fine until you go to shut the machine down in Ubuntu, it does its closing bit but stops on the black screen with the Ubuntu logo.The orange bar goes black and then it does no more.
I then have to hold the power button down for about 10 seconds or so before it turns off. Has anybody experienced the same, or know of a cure? Previously I had G OS 3.1 loaded on it with no XP, With exactly the same conclusion. It works as it should with XP so I'm presuming this must be a slight incompatibility with Linux based Os.
Any ideas or help would be much appreciated.

Thanks!

---

### Post by 00b00nt00 on 2009-05-03
Same here. Don't try to suspend the computer or it will crash!

It's a quirk. You can disable ACPI (which controls power management) in the GRUB booter, but you will lose some of the hot keys.

---

### Post by moose2 on 2009-05-17
Do I have the same problem ([http://ubuntuforums.org/showthread.php?t=1161868](http://ubuntuforums.org/showthread.php?t=1161868))? How can I disable ACPI and for what is ACPI good?

---

### Post by 00b00nt00 on 2009-05-19
Disabling ACPI means that the computer will use APM. Wikipedia will explain these terms. Basically, APM is older than ACPI.

ACPI controls power managment and possibly some of the hot keys. If you disable ACPI, you will not be able to suspend your computer, and you will need to push the power button to switch it off.

I disabled ACPI before I installed Jaunty by selecting F6 in the Ubuntu options screen (on the CD) and setting acpi=off and noapic. I then installed from the CD in the usual way.

---

### Post by moose2 on 2009-05-23
@00b00nt00: thank you very much

Did anyone try an acpi-fix? I'll translate the [german howto]("http://wiki.ubuntuusers.de/acpi-fix"):
[LIST=1]
[*]install ''iasl''
[*]read with "sudo cat /proc/acpi/dsdt > dsdt.dat"
[*]disassemble with "iasl -d dsdt.dat"
[*]compile with: "iasl -sa dsdt.dsl" (at this step errors/warnings will be reported)
[*]fix the errors in dsdt.dsl until "iasl -sa dsdt.dsl" doesn't report any errors
[*]sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
[*]sudo update-initramfs -u 
[*]restart
[*]now acpi should work
[/LIST]

can anyone fix the errors in [my dsdt.dsl]("http://martin-thoma.de/ubuntu/dsdt.dsl")?
My errors were:
> moose@pc07:~$ iasl -sa dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl   383:             Name (_HID, "*pnp0c14")
'''Error    4001 -                                  ^ String must be entirely alphanumeric (*pnp0c14)'''

dsdt.dsl   412:             Method (_WED, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (_WED)

dsdt.dsl   412:             Method (_WED, 1, NotSerialized)
Warning  1080 -                        ^ Reserved method must return a value (_WED)

dsdt.dsl   667:                         Name (_T_0, 0x00)
Remark   5110 -    Use of compiler reserved name ^  (_T_0)

dsdt.dsl   781:                             Name (_T_1, 0x00)
Remark   5110 -        Use of compiler reserved name ^  (_T_1)

dsdt.dsl   825:                                 Name (_T_2, 0x00)
Remark   5110 -            Use of compiler reserved name ^  (_T_2)

dsdt.dsl   876:                                     Name (_T_3, 0x00)
Remark   5110 -                Use of compiler reserved name ^  (_T_3)

dsdt.dsl   913:                                         Name (_T_4, 0x00)
Remark   5110 -                    Use of compiler reserved name ^  (_T_4)

dsdt.dsl   955:                                         Name (_T_5, 0x00)
Remark   5110 -                    Use of compiler reserved name ^  (_T_5)

dsdt.dsl  6500:                     Method (HKDS, 1, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (HKDS)

ASL Input:  dsdt.dsl - 8073 lines, 285795 bytes, 3171 keywords
Compilation complete. 1 Errors, 3 Warnings, 6 Remarks, 925 Optimizations

---

