---
title: "SMP on Ubuntu : How to verify a core in the CPU is not broken"
date: 2009-09-09
forum: Hardware
---

### Post by zong1 on 2009-09-09
I have an Intel Dual Core T2600 @ 2.16 Ghz running on my notebook.

Linux ranx 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux


The Linux ***lshw*** lists two cores (cpu0 cpu1)
  *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2600  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: N/A
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          clock: 166MHz

*-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 18EHz
          capabilities: vmx ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical

Running top and pressing 1 or I only ever lists cpu0 or cpu(s), but never cpu1. 

Installing WindowsXP SP3, only the Uniprocessor ACPI HAL is installed by default.  Forcing the the Multiprocessor ACPI HAL works, but WinXP only ever shows **one** CPU. Device Manager -> Processor will display the two cores, but Task Manager will only show one.

I know that Ubuntu ships with SMP enabled by default.  I had the same problem with Ubuntu 8.04 hence the upgrade.  Two cores were used in Ubuntu 7 with SMP enabled.

So, what gives?  Is one of cores broken - perhaps overheated and burnt out? How could I verify this?

---

