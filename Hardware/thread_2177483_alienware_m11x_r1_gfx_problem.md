---
title: "alienware m11x r1 gfx problem"
date: 2013-09-28
forum: Hardware
---

### Post by matthewpepperl on 2013-09-28
hello all my problem is when running optirun it takes 5 or so minutes just to start the program.
once running it runs fine but i cant figure out why it taking so long it did not allways do this.
this is what i got from the sys log my os is xubuntu 12.04.

ps im new to the fourms.

Sep 28 21:16:26 ubuntu kernel: [ 4432.123908] bbswitch: enabling discrete graphics
Sep 28 21:16:26 ubuntu bumblebeed[5936]: Received Terminated signal.
Sep 28 21:16:27 ubuntu kernel: [ 4432.624423] bbswitch: Result of _DSM call for ON: 00000001
Sep 28 21:16:27 ubuntu kernel: [ 4432.624447] pci 0000:01:00.0: power state changed by ACPI to D0
Sep 28 21:16:27 ubuntu kernel: [ 4432.624454] pci 0000:01:00.0: power state changed by ACPI to D0
Sep 28 21:16:27 ubuntu kernel: [ 4432.624483] pci 0000:01:00.0: restoring config space at offset 0xf (was 0x110, writing 0x10b)
Sep 28 21:16:27 ubuntu kernel: [ 4432.624496] pci 0000:01:00.0: restoring config space at offset 0x9 (was 0x2c81, writing 0x2001)
Sep 28 21:16:27 ubuntu kernel: [ 4432.624510] pci 0000:01:00.0: restoring config space at offset 0x3 (was 0x800010, writing 0x800000)
Sep 28 21:16:27 ubuntu kernel: [ 4432.624518] pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100003)
Sep 28 21:16:27 ubuntu kernel: [ 4432.624541] pci 0000:01:00.0: power state changed by ACPI to D0
Sep 28 21:16:27 ubuntu kernel: [ 4432.624547] pci 0000:01:00.0: power state changed by ACPI to D0
Sep 28 21:16:27 ubuntu kernel: [ 4432.624558] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 28 21:16:27 ubuntu kernel: [ 4432.624566] pci 0000:01:00.0: setting latency timer to 64
Sep 28 21:16:27 ubuntu bumblebeed[6096]: /usr/sbin/bumblebeed 3.2.1 started
Sep 28 21:16:29 ubuntu kernel: [ 4435.530470] nvidia 0000:01:00.0: power state changed by ACPI to D0
Sep 28 21:16:29 ubuntu kernel: [ 4435.530478] nvidia 0000:01:00.0: power state changed by ACPI to D0
Sep 28 21:16:29 ubuntu kernel: [ 4435.530490] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 28 21:16:29 ubuntu kernel: [ 4435.530502] nvidia 0000:01:00.0: setting latency timer to 64
Sep 28 21:16:29 ubuntu kernel: [ 4435.530510] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=none,decodes=none:owns=none
Sep 28 21:16:29 ubuntu kernel: [ 4435.530816] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.88  Wed Mar 27 14:31:12 PDT 2013
Sep 28 21:16:29 ubuntu acpid: client 5949[0:1001] has disconnected
Sep 28 21:16:29 ubuntu acpid: client 5949[0:1001] has disconnected
Sep 28 21:16:29 ubuntu acpid: client connected from 6111[0:1001]
Sep 28 21:16:29 ubuntu acpid: 1 client rule loaded

so if you could help me i would be appreciative

---

