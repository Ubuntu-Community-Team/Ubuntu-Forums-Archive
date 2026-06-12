---
title: "Can't get Battery Monitor to work on a Toshiba Satellite Pro L20"
date: 2006-03-09
forum: Hardware &amp; Laptops
---

### Post by Feral Biochemist on 2006-03-09
Hi, I'm new to ubuntu and linux and I've been trying to get the battery monitor to work properly. 

I've been following the instructions at [https://wiki.ubuntu.com/ACPIBattery]("https://wiki.ubuntu.com/ACPIBattery")
but have run into a snag when trying to compile the dsdt.asl file using iasl:
```
john@ubuntu:~/acpi$ ./iasl -tc dsdt.asl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20060217 [Mar 10 2006]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

Non-ASCII character [0xF4] found in line 1, file offset 0x04
Non-ASCII character [0x83] found in line 8, file offset 0x68
Non-ASCII character [0x80] found in line 8, file offset 0x70
Non-ASCII character [0x83] found in line 8, file offset 0x75
Non-ASCII character [0x80] found in line 8, file offset 0x7D
Non-ASCII character [0x80] found in line 14, file offset 0xCA
Non-ASCII character [0x80] found in line 15, file offset 0xD1
Non-ASCII character [0x81] found in line 15, file offset 0xD4
Non-ASCII character [0x80] found in line 15, file offset 0xE1
Non-ASCII character [0x80] found in line 15, file offset 0xE8
1277 non-ASCII characters found in input source text, could be a binary file
Error    1060 - Invalid characters found in file dsdt.asl

```

I've been following the instructions exactly right up to this step ... any help would be greatly appreciated.

---

### Post by Feral Biochemist on 2006-03-09
Update: I can't open the .asl file in gedit, so maybe it's just crap. Does anyone know how to manually patch the existing dsdt file to get it working for the L20?

---

### Post by anurag_gupta on 2006-06-07
hi 


try out the following n paste the output of the compilation of the DSDT.

sudo -s -H
cat /proc/acpi/DSDT > dsdt.dat

now you will get your dsdt as dsdt.dat. now diassemble it and then compile it.
if it has errors then iasl would show. else it will generate DSDT.aml
which you need to put in the follwing place if u use breezy
/etc/mkinitramfs/
(note:- the file DSDT.aml should have the extension *.aml)
then go to a terminal
sudo dpkg-reconfigure linux-image-$ (uname -r)

note:- remember to create a backup of ur current
initrd.gz and vmlinuz as mentioned in the link uhave mentiond.
or else it will lead to kernel panic
then reboot  now ur battery status may be working.

---

