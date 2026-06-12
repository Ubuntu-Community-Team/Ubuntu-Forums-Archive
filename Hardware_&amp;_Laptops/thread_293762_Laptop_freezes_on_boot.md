---
title: "Laptop freezes on boot"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2006-11-05
Hi all,

For some reason, my laptop freezes *sometimes* when I boot up.

Turning it off and back on a few times usually allows me to boot, but it is still annoying. I've got an HP dv6000z laptop with the AMD Sempron.

When I'm booting, the last message that I get is either:

```
[17179572.292000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0d.0
```

or

```
[17179572.288000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
```

Here is dmesg leading up those messages (when it boots up fully)

```
[17179571.496000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.576000] Calibrating delay using timer specific routine.. 3621.96 BogoMIPS (lpj=7243932)
[17179571.576000] Security Framework v1.0.0 initialized
[17179571.576000] SELinux:  Disabled at boot.
[17179571.576000] Mount-cache hash table entries: 512
[17179571.576000] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019
[17179571.576000] CPU: After vendor identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019
[17179571.576000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179571.576000] CPU: L2 Cache: 512K (64 bytes/line)
[17179571.576000] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 00000019
[17179571.576000] CPU: AMD Mobile AMD Sempron(tm) Processor 3500+ stepping 02
[17179571.576000] Checking 'hlt' instruction... OK.
[17179571.592000] SMP alternatives: switching to UP code
[17179571.592000] Freeing SMP alternatives: 0k freed
[17179571.592000] checking if image is initramfs... it is
[17179572.128000] Freeing initrd memory: 6465k freed
[17179572.128000] ACPI: Core revision 20060707
[17179572.132000] ACPI: Looking for DSDT ... not found!
[17179572.136000] ENABLING IO-APIC IRQs
[17179572.136000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179572.284000] NET: Registered protocol family 16
[17179572.284000] EISA bus registered
[17179572.284000] ACPI: bus type pci registered
[17179572.284000] PCI: Using MMCONFIG
[17179572.284000] PCI: No mmconfig possible on 0:18
[17179572.284000] PCI: No mmconfig possible on 7:5
[17179572.284000] Setting up standard PCI resources
[17179572.288000] ACPI: Interpreter enabled
[17179572.288000] ACPI: Using IOAPIC for interrupt routing
[17179572.288000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.288000] PCI: Probing PCI hardware (bus 00)
[17179572.288000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.292000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0d.0

```

---

### Post by erothoff on 2007-01-20
I have a HP DV6119 with a Turon64 x2 and I have the exact same problem with Ubuntu 64 but not in the Ubuntu i386 version. Any suggestions?

---

### Post by keflavich on 2007-02-07
I have the same problem on a Compaq Presario v6000 with a Turion64.  Also running 32 bit ubuntu.

---

### Post by erothoff on 2007-02-07
Hi,
  I found that adding the line: pnpbios=off on the startup usually solved this problem. In my startup I have both "noapic pnpbios=off" as noapic stops a freezing later on, and pnpbios=off stops the freezing on the PCI bridge. Good luck...

---

### Post by enigma_0Z on 2007-02-08
After much experimentation,

The new kernel from kernel.org also fixes the problem.

However, recompiling your kernel is not for the faint of heart.

---

### Post by keflavich on 2007-02-15
I grabbed  the new kernel today (6.17.11) and started getting the pnpbios errors on both the new and old kernel for the first time.  I'll try adding pnpbios=off, though, and see if it helps  any.  Thanks.

---

