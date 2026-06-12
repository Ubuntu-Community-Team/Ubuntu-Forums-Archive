---
title: "CPU Fan control - problem solved (amilo pro 2030)"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by acojlo on 2006-06-30
My hardware is Fujitsu Siemens Amilo Pro 2030 laptop so the guide is for the hardware, but possibly can be applicable to other.

This guide is solution to following problem: Under Kubuntu 6.06 Dapper Drake cpu's fan is allways on by full speed.

Let's first summarize what I did: Repairing the DSDT. The repair enable ways of controling the cpu fan, but it does not make active fan control. Control can be made manualy or automaticly at boot time.

Here are the steps

1. Install iasl package by Adept (Package manager)
2. Copy dsdt to file:

	cat /proc/acpi/dsdt > dsdt.dat

3. Make dsdt.dat readable by human eye:
	iasl -d dsdt.dat

4. Edit your dsdt.dsl (the new file (.dsl) is created by previous command). This option can vary. But, for my laptop (amilo pro 2030) I had to do this:

Original DSDT taken down from my BIOS:

Method functions are empty:

Device (FAN)
                {
                    Name (_HID, EisaId ("PNP0C0B"))
                    Name (_PSC, 0x00)
                    Method (_PS0, 0, NotSerialized)
                    {
                    }

                    Method (_PS3, 0, NotSerialized)
                    {
                    }
                }


GO-GO SOLUTION:

Method (_PS0, 0, NotSerialized)
                    {
                       \_TZ.PFAN._ON ()
                       SFAN(0x03)
                    } 
         
                    Method (_PS1, 0, NotSerialized)
                    {
                        SFAN (0x01)
                    }
         
                    Method (_PS2, 0, NotSerialized)
                    {
                        SFAN (0x02)
                    }

                    Method (_PS3, 0, NotSerialized)
                    {
                        \_TZ.PFAN._OFF ()
                    }

5. Compile dsdt:

	iasl -tc dsdt.dsl

this makes DSDT.asl

6. sudo cp DSDT.aml /etc/mkinitramfs/ 
7. sudo dpkg-reconfigure linux-image-`uname -r`

8. So far I have established ways for fan control to be possible. After finishing previous step - restart system

9. echo 3 > /proc/acpi/fan/FAN/state (you must do this as root and this is manual way of controling the fan)

10. How about to automaticaly control fan, without manualy entering step 9? This way:

11. Create text file with this lines (save it after as fan_control):

#! /bin/sh
#
# omogucavanje kontrole cpu ventilatora

echo 3 > /proc/acpi/fan/FAN/state

exit 0

12. chmod 755 fan_control
13. sudo cp fan_control /etc/init.d/
14. sudo update-rc.d kontrola_cpu_fan start 51 S .

Done.

---

### Post by Injall on 2008-02-06
Hi,

My english is not good, my first language is french...

I've exactly this problem but i've an AMILO Pi 1536 and i've 8 errors:

> injall@injall-laptop:~$ sudo iasl -tc dsdt.dsl
[sudo] password for injall:

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  1822: GO-GO SOLUTION:
Error    4094 -  ^ syntax error, unexpected PARSEOP_NAMESEG

dsdt.dsl  1822: GO-GO SOLUTION:
Error    4094 -   ^ Invalid character (0x2D), expecting ASL keyword or name

dsdt.dsl  1822: GO-GO SOLUTION:
Error    4094 -               ^ Invalid character (0x3A), expecting ASL keyword or name

dsdt.dsl  1826: \_TZ.PFAN._ON ()
Error    4062 -             ^ Object does not exist (\_TZ.PFAN._ON)

dsdt.dsl  1827: SFAN(0x03)
Error    4062 -    ^ Object does not exist (SFAN)

dsdt.dsl  1832: SFAN (0x01)
Error    4062 -    ^ Object does not exist (SFAN)

dsdt.dsl  1837: SFAN (0x02)
Error    4062 -    ^ Object does not exist (SFAN)

dsdt.dsl  1842: \_TZ.PFAN._OFF ()
Error    4062 -              ^ Object does not exist (\_TZ.PFAN._OFF)

ASL Input:  dsdt.dsl - 5602 lines, 189440 bytes, 2102 keywords
Compilation complete. 8 Errors, 0 Warnings, 0 Remarks, 5 Optimizations
injall@injall-laptop:~$ 


How can i repear that ?

---

