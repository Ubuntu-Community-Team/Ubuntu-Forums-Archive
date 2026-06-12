---
title: "Standby does not work with Lifebook E8010"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by Tomek on 2006-12-06
On my notebook Fujitsu-Siemens Lifebook E8010 Standby does not work properly.  I have installed Ubuntu 6.10 with all updates. I tried with Kernel 2.6.19 from Feisty (Unstable), too. When I activate the Standby-Mode the Notebook turns off, but the notebook does not beep twice, as it should. When I turn on the notebook again, the display is black and the fan is working. The notebook does not react on CTRL+ALT+DEL. There is no harddisk activity also. So I have to turn the notebook off completly and start the system. With Windows XP the Standby-Mode works all fine. 

The outputs of dmesg, lspci and lsmod are here:
[http://tueddeln.de/tomek/e8010/](http://tueddeln.de/tomek/e8010/)

The DSDT compiles cleanly:
```
root@wirbelwind:~# cat /proc/acpi/dsdt > dsdt.dat 
root@wirbelwind:~# iasl -d dsdt.dat  
 
Intel ACPI Component Architecture 
AML Disassembler version 20060608 [Jun 29 2006] 
Copyright (C) 2000 - 2006 Intel Corporation 
Supports ACPI Specification Revision 3.0a 
 
Loading Acpi table from file dsdt.dat 
Acpi table [DSDT] successfully installed and loaded 
Pass 1 parse of [DSDT] 
Pass 2 parse of [DSDT] 
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions) 
.......................................................................................................... 
.......................................................................................................... 
.................................................................................................... 
Parsing completed 
Disassembly completed, written to "dsdt.dsl" 
root@wirbelwind:~# iasl -tc dsdt.dsl  
 
Intel ACPI Component Architecture 
ASL Optimizing Compiler version 20060608 [Jun 29 2006] 
Copyright (C) 2000 - 2006 Intel Corporation 
Supports ACPI Specification Revision 3.0a 
 
ASL Input:  dsdt.dsl - 6788 lines, 259348 bytes, 3211 keywords 
AML Output: dsdt.aml - 23941 bytes 698 named objects 2513 executable opcodes 
 
Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 565 Optimizations 
root@wirbelwind:~#
```Hibernate (Suspend-To-Disk) works out of the box without any problems. 

I have also tried many kernel parameters, like these:
 pci=biosirq, acpi_os_name="Microsoft Windows XP", pci=routeirq, pci=assign-busses, acpi_sleep=s3_mode,s3_bios ...

I also tried the 2.6.18 kernel from Fedora Core 6, but all this does not help. Without X and without a framebuffer driver the notebook behaves the same.

Thanks in advance. :)

---

