---
title: "Slow system after upgrading RAM to 2GB"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by qnob on 2007-02-07
Hi!

I've installed Ubuntu Edgy Eft on a host with 2x512GB RAM. Later, I tried to upgrade the memory with 2 identicals RAM entities - so I got altogther 2GB RAM. The BIOS recognises the RAMs without any problems. Also, Ubuntus memory test - started from Grub - worked without failures and the System Monitor shows the full 2GB memory.

The system, however, is very slow now. Everything delayed. The boot sequence takes more than a couple of tea! Before it was about 30s.

When I remove the additional RAM, the system works fine again. Does anybody have an idea? 

Thanks.

System:
- Intel® Pentium® D processor 945 dual-core 3.40 GHz 4 MB (2 MB per core) L2 cache 800 MHz front side bus with Extended Memory 64-bit Technology
- RAM 4x PC5300 (512MB)
[http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/12454-64287-89301-321860-f56-3232029.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/12454-64287-89301-321860-f56-3232029.html)

Kernel: linux-generic (v. 2.6.17.10) Standard package from Ubuntu Repo.

dmesg:

```

[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease
) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007efb1d00 (usable)
[17179569.184000]  BIOS-e820: 000000007efb1d00 - 000000007f000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fed40000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed45000 - 0000000100000000 (reserved)
[17179569.184000] 1135MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f9bf0
[17179569.184000] On node 0 totalpages: 520113
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 290737 pages, LIFO batch:31
[17179569.184000] DMI 2.4 present.
[17179569.184000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000e7610
[17179569.184000] ACPI: RSDT (v001 HPQOEM SLIC-BPC 0x20060830  0x00000000) @ 0x7efc3d40
[17179569.184000] ACPI: FADT (v001 COMPAQ BROADH2O 0x00000001  0x00000000) @ 0x7efc3de8
[17179569.184000] ACPI: MADT (v001 COMPAQ BROADH2O 0x00000001  0x00000000) @ 0x7efc3e5c
[17179569.184000] ACPI: ASF! (v032 COMPAQ BROADH2O 0x00000001  0x00000000) @ 0x7efc3ec4
[17179569.184000] ACPI: MCFG (v001 COMPAQ BROADH2O 0x00000001  0x00000000) @ 0x7efc3f27
[17179569.184000] ACPI: TCPA (v001 COMPAQ BROADH2O 0x00000001  0x00000000) @ 0x7efc3f63
[17179569.184000] ACPI: SLIC (v001 HPQOEM SLIC-BPC 0x00000001  0x00000000) @ 0x7efc3f95
[17179569.184000] ACPI: DSDT (v001 COMPAQ DSDT_PRJ 0x00000001 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xf808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:6 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:6 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 80000000 (gap: 7f000000:75000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
...
 
```

---

### Post by Shay Stephens on 2007-02-07
Just guessing here, but bad ram?  Take it back for replacement?

---

### Post by qnob on 2007-02-08
Thanks Shay!

I tried it with other 2x1GB entities as well - same effect!

---

### Post by Shay Stephens on 2007-02-08
Weird.  But that was a good test.  I am out of my league ;-)

The only thing I can think of now, is trying an SMP kernel.  And I am just grasping at straws here.  I wish I knew more about linux troubleshooting.

---

### Post by Shay Stephens on 2007-02-08
One thing just occurred to me, the motherboard, there is the chance it might be having trouble.  I don't know if you have the ability to try the ram on another board or not.

---

### Post by qnob on 2007-02-09
I took the RAM from another, identical host with the same setup. Therefore, I believe that those entities are ok.

---

### Post by qnob on 2007-02-09
:guitar: I've found  a hint on [http://michael-prokop.at/blog/2007/01/09/hp-compaq-dc7700-and-linux/]("http://michael-prokop.at/blog/2007/01/09/hp-compaq-dc7700-and-linux/").

Thanks to Mik!

So, I've flashed the BIOS - a task that could be worth to make another post...but in short, I've extracted the .exe file on my windows host and copied file DOS Flash/7E1xxx.bin to a USB-stick and flashed the BIOS from the corresponding BIOS menu.

---

