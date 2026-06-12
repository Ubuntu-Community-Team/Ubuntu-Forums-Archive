---
title: "ACPI and Radeon Issues during boot"
date: 2018-09-02
forum: Hardware
---

### Post by angourakis2 on 2018-09-02
Hello guys and girls,

I just installed Ubuntu 18.04 64-bit, and everything is, apparently, running fine (although sometimes I can see some micro-freezes, especially on videos).

However, during boot time, I can see some errors and captured them with dmesg:

> 
[    0.053176] ACPI Exception: Could not find/resolve named package element: AMD3 (20170831/dspkginit-381)
[    0.053176] ACPI Exception: Could not find/resolve named package element: AMD2 (20170831/dspkginit-381)
[    0.053176] ACPI Exception: Could not find/resolve named package element: AMD3 (20170831/dspkginit-381)
[    2.239792] ACPI Error: [\_SB_.PCI0.GFX0.DD02._BCL] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[    2.239805] ACPI Error: Method parse/execution failed \_SB.PCI0.RP05.PEGP.DD02._BCL, AE_NOT_FOUND (20170831/psparse-550)

[   15.913803] [drm:r600_ring_test [radeon]] *ERROR* radeon: ring 0 test failed (scratch(0x850C)=0xCAFEDEAD)
[   15.913828] [drm:si_resume [radeon]] *ERROR* si startup failed on resume
[  490.709731] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
[  490.709754] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing 762A (len 237, WS 0, PS 4) @ 0x7638
[  490.709772] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing 6FC2 (len 74, WS 0, PS 8) @ 0x6FF7
[  492.148992] [drm:r600_ring_test [radeon]] *ERROR* radeon: ring 0 test failed (scratch(0x850C)=0xCAFEDEAD)
[  492.149015] [drm:si_resume [radeon]] *ERROR* si startup failed on resume
[  547.194101] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
[  547.194126] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing 762A (len 237, WS 0, PS 4) @ 0x7638
[  547.194145] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing 6FC2 (len 74, WS 0, PS 8) @ 0x6FF7
[  548.614248] [drm:r600_ring_test [radeon]] *ERROR* radeon: ring 0 test failed (scratch(0x850C)=0xCAFEDEAD)
[  548.614275] [drm:si_resume [radeon]] *ERROR* si startup failed on resume


From my searches on Google, it seems related to BIOS (I'm already running the latest one, F71) and/or Kernel (4.15.0-29-generic).
My computer is an HP Pavilion 15-n274ca Touchsmart (Intel Core i5-4200U, 12GB RAM, 240GB SSD Samsung 840 Evo , dGPU Radeon HD8600M).

What can I do to solve them? I'm running with the drivers that came with Ubuntu.

Thank you!


EDIT: Just updated kernel version to 4.18.5-041805-generic and the errors with my video card are (almost) gone. These are the errors now:

> 
[    2.306876] ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.GFX0.DD02._BCL], AE_NOT_FOUND (20180531/psargs-330)
[    2.306898] ACPI Error: Method parse/execution failed \_SB.PCI0.RP05.PEGP.DD02._BCL, AE_NOT_FOUND (20180531/psparse-516)
[   16.795959] [drm:r600_ring_test [radeon]] *ERROR* radeon: ring 0 test failed (scratch(0x850C)=0xCAFEDEAD)
[   16.795987] [drm:si_resume [radeon]] *ERROR* si startup failed on resume


Also, I assume that since I updated my kernel manually, it will not update automatically anymore unless Ubuntu uses a higher version, right? From my understanding, I should only update the Kernel when I have hardware bugs that are fixed on newer versions, is that right?

Thank you!

---

