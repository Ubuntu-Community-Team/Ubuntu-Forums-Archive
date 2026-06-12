---
title: "Various boot problems, Gutsy AMD64"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by Ghaagsheblah on 2008-02-08
Have spent some time now looking for solutions on various bootproblems without any result and am therefor giving it a try to post them in here...

My dist is Gutsy AMD64. 
Computer: Fujitsu Siemens laptop, Amilo Xi 1526

Problem 1:
[   35.401298] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0

Shows up in dmesg and during boot, found something on ubuntuforums regarding "failed to allocate mem resource" to reserve memory in menu.lst.

Have tried that by adding "reserve=0xd0000000,0x20000" to my boot options but without any success and the error message still appears.


Problem 2:
[   35.399663] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0

[   35.401370] PCI: Bridge: 0000:00:1c.0
[   35.401372]   IO window: disabled.
[   35.401378]   MEM window: fac00000-febfffff
[   35.401382]   PREFETCH window: disabled.
[   35.401388] PCI: Bridge: 0000:00:1c.2
[   35.401389]   IO window: disabled.
[   35.401395]   MEM window: b3000000-b30fffff
[   35.401399]   PREFETCH window: disabled.

When running lspci i get the following outputs:
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)

It seems that it has something to do with the microphone ports in my audio device. I have tried various boot options in menu.lst such as "pci=routeirq" and "pci=assign-busses" but the problem still remain. Since i never use a microphone is there any way to disable this during boot or does anyone have any other solution.

The two problems mentioned above does not seem to affect the computer but it slows the boot process with about 30-45 seconds.


Problem 3:
[   16.798055] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

I have no idea what the DSDT is used for and i cant find DSDT.aml on my computer. 

If anyone knows how to fix any of these problems it would be highly appreciated.

---

