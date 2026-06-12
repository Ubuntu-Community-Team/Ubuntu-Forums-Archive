---
title: "APIC error on CPU0: 40(40)"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by macubo on 2007-06-07
Hi all folks, I'm trying to fine-tune my 7.04 on a HP NX6125 laptop.
I got most of the devices to work fine, still haven't tried PCMCIA, expressCard, firewire, cardreader and fingerprint reader (some said firewire, cardreader and expresscard or pcmcia work out-of-the-box).

I noticed a lot of messages of " APIC error on CPU0: 40(40)" and the first: 40(00).
Here is the output of dmesg | grep ACPI:
```
manuele@manuele-laptop:~$ dmesg | grep APIC
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] Setting APIC routing to physical flat
[    9.629576] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    9.669616] Using local APIC timer interrupts.
[    9.715127] Detected 12.469 MHz APIC timer.
[    9.732360] ACPI: Using IOAPIC for interrupt routing
[  163.277569] APIC error on CPU0: 00(40)
[  218.439071] APIC error on CPU0: 40(40)
[  245.319581] APIC error on CPU0: 40(40)
[  281.715478] APIC error on CPU0: 40(40)
[  323.204918] APIC error on CPU0: 40(40)
[  437.914908] APIC error on CPU0: 40(40)
[  477.463928] APIC error on CPU0: 40(40)
[  737.497811] APIC error on CPU0: 40(40)
[  817.513968] APIC error on CPU0: 40(40)
[  874.862263] APIC error on CPU0: 40(40)
[  881.619307] APIC error on CPU0: 40(40)
[  958.398674] APIC error on CPU0: 40(40)
[  961.551407] APIC error on CPU0: 40(40)
[ 1024.874453] APIC error on CPU0: 40(40)
[ 1075.043994] APIC error on CPU0: 40(40)
[ 1104.340488] APIC error on CPU0: 40(40)
[ 1203.139049] APIC error on CPU0: 40(40)
[ 1274.607335] APIC error on CPU0: 40(40)
[ 1674.819783] APIC error on CPU0: 40(40)
[ 2285.518528] APIC error on CPU0: 40(40)
[ 2313.721243] APIC error on CPU0: 40(40)
[ 2453.392629] APIC error on CPU0: 40(40)
[ 2650.790414] APIC error on CPU0: 40(40)
[ 2765.390209] APIC error on CPU0: 40(40)
[ 3033.295834] APIC error on CPU0: 40(40)
[ 3249.412353] APIC error on CPU0: 40(40)
[ 3436.519288] APIC error on CPU0: 40(40)
[ 3556.588389] APIC error on CPU0: 40(40)
[ 3597.859253] APIC error on CPU0: 40(40)
[ 3700.901781] APIC error on CPU0: 40(40)
[ 3916.258027] APIC error on CPU0: 40(40)
[ 3935.327286] APIC error on CPU0: 40(40)
[ 4122.293022] APIC error on CPU0: 40(40)
[ 4265.118336] APIC error on CPU0: 40(40)
[ 4356.500107] APIC error on CPU0: 40(40)
[ 4384.996441] APIC error on CPU0: 40(40)
[ 4518.480386] APIC error on CPU0: 40(40)
[ 4601.114715] APIC error on CPU0: 40(40)

```

I boot normally **without** the noapic nolapic parameters, and kernel is:
```
manuele@manuele-laptop:~$ uname -r
2.6.20-16-generic

```

The [5534 bug]("http://bugzilla.kernel.org/show_bug.cgi?id=5534") has been recently fixed for this laptop et similia and fans now work fine.
The laptop seems to properly operate.. should I pay more attention to that error?

Thank you

---

### Post by DynamicMouse on 2008-06-13
I too have the same APIC error message, however it only appeared after upgrading to 8.04.

There doesn't seem to be any information about what causes this message, I am stumpped!

---

### Post by DynamicMouse on 2008-07-16
I forgot about this error, it went away presumably after I did a few updates using synaptic

---

