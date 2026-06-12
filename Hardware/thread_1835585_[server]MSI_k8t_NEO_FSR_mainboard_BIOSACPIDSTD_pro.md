---
title: "[server]MSI k8t NEO FSR mainboard BIOS/ACPI/DSTD problems"
date: 2011-08-29
forum: Hardware
---

### Post by flel on 2011-08-29
Hi!

My name is Floris and I am new to these forums. I've been looking around for a bit to research some problems but to no avail so far. As of recently I have joined myself to write about these problems and hopefully come to a solution to help me and hopefully others as well.

```
jopie@jopieserver:~$ uname -a
Linux jopieserver 2.6.32-33-server #70-Ubuntu SMP Thu Jul 7 22:28:30 UTC 2011 x86_64 GNU/Linux
```

So onto my problems:
1. Cool 'n Quiet/CPU Freq Scaling/ACPI/Buggy DSTD tables
As I am building a home media server I would like to scale my CPU as conservative as possible to conserve power and reduce noise. However, enabling the option in the BIOS hangs ubuntu at startup (inmediately after GRUB). Adding acpi=off in grub will make ubuntu load but this doesn't solve the problem. I chcked the DSTD tables for errors according to [this]("http://ubuntuforums.org/showthread.php?t=1036051") guide. The result: ```
jopie@jopieserver:~$ iasl -tc -va dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

ASL Input:  dsdt.dsl - 4118 lines, 132851 bytes, 1349 keywords
Compilation complete. 12 Errors, 2 Warnings, 0 Remarks, 475 Optimizations
```

2. BIOS hangs with 1.0 TB external USB drive attached to the port. Disabeling legacy USB support or using a HUB doesn't solve the problem.

3. My BIOS won't Flash
I hoped upgrading the BIOS would help solve both issues. However, I can't get it to flash!
I've tried all the options in this [guide]("http://ubuntuforums.org/showthread.php?t=318789") as well as tried other bootable DOS CD options. The AMIFLASH tool provided by MSI on their [website]("http://www.msi.com/product/mb/K8T-Neo-FSR--FIS2R.html#/?div=BIOS") won't flash the ROMS supplied. Running the flash program with the ROM supplied as argument in the FreeDOS environement simply echo's the help screen.

I really don't know whats going on here, and my frustration is slowly building up now lol. Too many hours spent trying and trying and no luck anywhere. Hope someone can help me out!

Thanks,
Floris

---

