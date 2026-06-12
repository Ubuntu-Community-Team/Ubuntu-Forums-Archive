---
title: "Will HP C7280 All-in-one Work?"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by mattpg1 on 2007-11-30
I'm probably going to need to install Linux and Ubuntu 7.10 is on the top of my list.  I am also probably getting the HP C7280 All-In-One printer.

If you have this printer or one you think is similar working with Ubuntu, please tell me.  

Also, if you think you can give an educated answer...

Thanks

---

### Post by .nedberg on 2007-11-30
I don't have that model, but I have a HP all-in-one printer and it works just fine. Scan and everything. I can even read the ink levels from my computer.

I heard that HP printers work out-of-the-box with every Linux distribution because they (HP) are "Linux-friendly".

---

### Post by mattpg1 on 2007-11-30
Thanks

---

### Post by taysider on 2007-12-01
go to this link, at the bottom of the page is your printer
[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)

dave

---

### Post by mattpg1 on 2007-12-02
Even better.  Thanks

---

### Post by da Wookiee on 2007-12-04
Well, It DID work.

I had it working under ubuntu 7.10, installed like a dream, duplex and everything.

Then I got the bright idea to overwrite my installation with Kubuntu, now hp-setup won't detect the printer.  Even reinstalling Ubuntu with gnome didn't help.  I can't figure out what I'm doing different.  It prints from a Vista machine on the same network, so the network doesn't seem to be the problem.  I can get hp-setup to detect the printer if i put in the ip as a hostname, but then it says the printer is offline or busy all the time regardless of whether it is on or off.   

It wouldn't frustrate me as much if it hadn't worked perfectly in the beginning.  Hope your installation goes off flawlessly.  Post step by step for us and if it works I can follow your lead, and if it doesn't, one of the more experienced personnel here can guide us to where we want to be.

---

### Post by 11hjpphty76lkjj on 2007-12-04
Can you delete the printer queue, then run 

```
sudo tail -f /var/log/messages
```

re-setup the printer using hp-setup, try to print and then post any errors in the /var/log/messages.

A

---

### Post by da Wookiee on 2007-12-05
Well, I did as asked, but I'm not sure I can make head or tails from it.


```
Dec  5 09:37:37 Alphaone syslogd 1.4.1#21ubuntu3: restart.
Dec  5 09:44:45 Alphaone kernel: [ 1086.322185] usb 5-1: reset high speed USB device using ehci_hcd and address 2
Dec  5 09:54:28 Alphaone exiting on signal 15
Dec  5 09:55:44 Alphaone syslogd 1.4.1#21ubuntu3: restart.
Dec  5 09:55:44 Alphaone kernel: Inspecting /boot/System.map-2.6.22-14-generic
Dec  5 09:55:44 Alphaone kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Dec  5 09:55:44 Alphaone kernel: Symbols match kernel version 2.6.22.
Dec  5 09:55:44 Alphaone kernel: No module symbols loaded - kernel modules not enabled. 
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] BIOS-provided physical RAM map:
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 00000000fefffc00 - 00000000ff000000 (reserved)
Dec  5 09:55:44 Alphaone kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] 1151MB HIGHMEM available.
Dec  5 09:55:44 Alphaone kernel: [    0.000000] 896MB LOWMEM available.
Dec  5 09:55:44 Alphaone kernel: [    0.000000] found SMP MP-table at 000f3690
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Zone PFN ranges:
Dec  5 09:55:44 Alphaone kernel: [    0.000000]   DMA             0 ->     4096
Dec  5 09:55:44 Alphaone kernel: [    0.000000]   Normal       4096 ->   229376
Dec  5 09:55:44 Alphaone kernel: [    0.000000]   HighMem    229376 ->   524272
Dec  5 09:55:44 Alphaone kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec  5 09:55:44 Alphaone kernel: [    0.000000]     0:        0 ->   524272
Dec  5 09:55:44 Alphaone kernel: [    0.000000] DMI 2.2 present.
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7550 checksum 0
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: RSDP 000F7550, 0014 (r0 Nvidia)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: RSDT 7FFF3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: FACP 7FFF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: DSDT 7FFF3180, 5FB9 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: FACS 7FFF0000, 0040
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: MCFG 7FFF9240, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: APIC 7FFF9180, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Dec  5 09:55:44 Alphaone kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Processor #0 15:12 APIC version 16
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec  5 09:55:44 Alphaone kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Built 1 zonelists.  Total pages: 520177
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Kernel command line: root=UUID=72a8ad05-9e3a-4245-97fe-4e1d8aaf21fc ro quiet splash
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Initializing CPU#0
Dec  5 09:55:44 Alphaone kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec  5 09:55:44 Alphaone kernel: [    0.000000] Detected 2010.347 MHz processor.
Dec  5 09:55:44 Alphaone kernel: [   19.334773] Console: colour VGA+ 80x25
Dec  5 09:55:44 Alphaone kernel: [   19.335199] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec  5 09:55:44 Alphaone kernel: [   19.335636] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec  5 09:55:44 Alphaone kernel: [   19.399494] Memory: 2067456k/2097088k available (2015k kernel code, 28440k reserved, 916k data, 364k init, 1179584k highmem)
Dec  5 09:55:44 Alphaone kernel: [   19.399503] virtual kernel memory layout:
Dec  5 09:55:44 Alphaone kernel: [   19.399504]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Dec  5 09:55:44 Alphaone kernel: [   19.399506]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec  5 09:55:44 Alphaone kernel: [   19.399507]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Dec  5 09:55:44 Alphaone kernel: [   19.399508]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec  5 09:55:44 Alphaone kernel: [   19.399509]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Dec  5 09:55:44 Alphaone kernel: [   19.399510]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Dec  5 09:55:44 Alphaone kernel: [   19.399512]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Dec  5 09:55:44 Alphaone kernel: [   19.399514] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec  5 09:55:44 Alphaone kernel: [   19.399551] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Dec  5 09:55:44 Alphaone kernel: [   19.479513] Calibrating delay using timer specific routine.. 4023.19 BogoMIPS (lpj=8046380)
Dec  5 09:55:44 Alphaone kernel: [   19.479541] Security Framework v1.0.0 initialized
Dec  5 09:55:44 Alphaone kernel: [   19.479547] SELinux:  Disabled at boot.
Dec  5 09:55:44 Alphaone kernel: [   19.479559] Mount-cache hash table entries: 512
Dec  5 09:55:44 Alphaone kernel: [   19.479682] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec  5 09:55:44 Alphaone kernel: [   19.479684] CPU: L2 Cache: 512K (64 bytes/line)
Dec  5 09:55:44 Alphaone kernel: [   19.479697] Compat vDSO mapped to ffffe000.
Dec  5 09:55:44 Alphaone kernel: [   19.479708] Checking 'hlt' instruction... OK.
Dec  5 09:55:44 Alphaone kernel: [   19.495635] SMP alternatives: switching to UP code
Dec  5 09:55:44 Alphaone kernel: [   19.495843] Freeing SMP alternatives: 11k freed
Dec  5 09:55:44 Alphaone kernel: [   19.496088] Early unpacking initramfs... done
Dec  5 09:55:44 Alphaone kernel: [   19.794971] ACPI: Core revision 20070126
Dec  5 09:55:44 Alphaone kernel: [   19.795040] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Dec  5 09:55:44 Alphaone kernel: [   19.797973] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 02
Dec  5 09:55:44 Alphaone kernel: [   19.797989] Total of 1 processors activated (4023.19 BogoMIPS).
Dec  5 09:55:44 Alphaone kernel: [   19.798127] ENABLING IO-APIC IRQs
Dec  5 09:55:44 Alphaone kernel: [   19.798311] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Dec  5 09:55:44 Alphaone kernel: [   19.943242] Brought up 1 CPUs
Dec  5 09:55:44 Alphaone kernel: [   19.943341] Booting paravirtualized kernel on bare hardware
Dec  5 09:55:44 Alphaone kernel: [   19.943381] Time: 15:54:57  Date: 11/05/107
Dec  5 09:55:44 Alphaone kernel: [   19.943400] NET: Registered protocol family 16
Dec  5 09:55:44 Alphaone kernel: [   19.943467] EISA bus registered
Dec  5 09:55:44 Alphaone kernel: [   19.943475] ACPI: bus type pci registered
Dec  5 09:55:44 Alphaone kernel: [   19.948087] PCI: PCI BIOS revision 3.00 entry at 0xfa7e0, last bus=5
Dec  5 09:55:44 Alphaone kernel: [   19.948089] PCI: Using configuration type 1
Dec  5 09:55:44 Alphaone kernel: [   19.948091] Setting up standard PCI resources
Dec  5 09:55:44 Alphaone kernel: [   19.956474] ACPI: Interpreter enabled
Dec  5 09:55:44 Alphaone kernel: [   19.956476] ACPI: (supports S0 S1 S4 S5)
Dec  5 09:55:44 Alphaone kernel: [   19.956488] ACPI: Using IOAPIC for interrupt routing
Dec  5 09:55:44 Alphaone kernel: [   19.964412] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec  5 09:55:44 Alphaone kernel: [   19.964899] PCI: Transparent bridge - 0000:00:09.0
Dec  5 09:55:44 Alphaone kernel: [   20.021583] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Dec  5 09:55:44 Alphaone kernel: [   20.021739] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.021894] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 10 11 *12 14 15)
Dec  5 09:55:44 Alphaone kernel: [   20.022048] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Dec  5 09:55:44 Alphaone kernel: [   20.022201] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.022356] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Dec  5 09:55:44 Alphaone kernel: [   20.022509] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.022663] ACPI: PCI Interrupt Link [LMAC] (IRQs *3 4 5 7 9 10 11 12 14 15)
Dec  5 09:55:44 Alphaone kernel: [   20.022817] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Dec  5 09:55:44 Alphaone kernel: [   20.022975] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.023130] ACPI: PCI Interrupt Link [LSMB] (IRQs *3 4 5 7 9 10 11 12 14 15)
Dec  5 09:55:44 Alphaone kernel: [   20.023291] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 11 *12 14 15)
Dec  5 09:55:44 Alphaone kernel: [   20.023448] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.023609] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Dec  5 09:55:44 Alphaone kernel: [   20.023772] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Dec  5 09:55:44 Alphaone kernel: [   20.023934] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.024105] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Dec  5 09:55:44 Alphaone kernel: [   20.024270] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.024434] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Dec  5 09:55:44 Alphaone kernel: [   20.024597] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
Dec  5 09:55:44 Alphaone kernel: [   20.024707] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.024878] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Dec  5 09:55:44 Alphaone kernel: [   20.025047] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.025215] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Dec  5 09:55:44 Alphaone kernel: [   20.025384] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
Dec  5 09:55:44 Alphaone kernel: [   20.025553] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.025721] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Dec  5 09:55:44 Alphaone kernel: [   20.025890] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Dec  5 09:55:44 Alphaone kernel: [   20.026058] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.026233] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Dec  5 09:55:44 Alphaone kernel: [   20.026408] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Dec  5 09:55:44 Alphaone kernel: [   20.026583] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
Dec  5 09:55:44 Alphaone kernel: [   20.026672] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec  5 09:55:44 Alphaone kernel: [   20.026680] pnp: PnP ACPI init
Dec  5 09:55:44 Alphaone kernel: [   20.026687] ACPI: bus type pnp registered
Dec  5 09:55:44 Alphaone kernel: [   20.031004] pnp: PnP ACPI: found 13 devices
Dec  5 09:55:44 Alphaone kernel: [   20.031006] ACPI: ACPI bus type pnp unregistered
Dec  5 09:55:44 Alphaone kernel: [   20.031009] PnPBIOS: Disabled by ACPI PNP
Dec  5 09:55:44 Alphaone kernel: [   20.031049] PCI: Using ACPI for IRQ routing
Dec  5 09:55:44 Alphaone kernel: [   20.031052] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec  5 09:55:44 Alphaone kernel: [   20.097919] NET: Registered protocol family 8
Dec  5 09:55:44 Alphaone kernel: [   20.097921] NET: Registered protocol family 20
Dec  5 09:55:44 Alphaone kernel: [   20.097972] pnp: 00:01: ioport range 0x4000-0x407f has been reserved
Dec  5 09:55:44 Alphaone kernel: [   20.097975] pnp: 00:01: ioport range 0x4080-0x40ff has been reserved
Dec  5 09:55:44 Alphaone kernel: [   20.097977] pnp: 00:01: ioport range 0x4400-0x447f has been reserved
Dec  5 09:55:44 Alphaone kernel: [   20.097980] pnp: 00:01: ioport range 0x4480-0x44ff has been reserved
Dec  5 09:55:44 Alphaone kernel: [   20.097983] pnp: 00:01: ioport range 0x4800-0x487f has been reserved
Dec  5 09:55:44 Alphaone kernel: [   20.097985] pnp: 00:01: ioport range 0x4880-0x48ff has been reserved
Dec  5 09:55:44 Alphaone kernel: [   20.097994] pnp: 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
Dec  5 09:55:44 Alphaone kernel: [   20.097998] pnp: 00:0c: iomem range 0xcec00-0xcffff has been reserved
Dec  5 09:55:44 Alphaone kernel: [   20.098001] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
Dec  5 09:55:44 Alphaone kernel: [   20.098003] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
Dec  5 09:55:44 Alphaone kernel: [   20.098006] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Dec  5 09:55:44 Alphaone kernel: [   20.099109] Time: tsc clocksource has been installed.
Dec  5 09:55:44 Alphaone kernel: [   20.128194] PCI: Bridge: 0000:00:09.0
Dec  5 09:55:44 Alphaone kernel: [   20.128196]   IO window: d000-dfff
Dec  5 09:55:44 Alphaone kernel: [   20.128199]   MEM window: fe900000-fe9fffff
Dec  5 09:55:44 Alphaone kernel: [   20.128202]   PREFETCH window: fea00000-feafffff
Dec  5 09:55:44 Alphaone kernel: [   20.128205] PCI: Bridge: 0000:00:0b.0
Dec  5 09:55:44 Alphaone kernel: [   20.128207]   IO window: c000-cfff
Dec  5 09:55:44 Alphaone kernel: [   20.128209]   MEM window: fe800000-fe8fffff
Dec  5 09:55:44 Alphaone kernel: [   20.128212]   PREFETCH window: fe700000-fe7fffff
Dec  5 09:55:44 Alphaone kernel: [   20.128214] PCI: Bridge: 0000:00:0c.0
Dec  5 09:55:44 Alphaone kernel: [   20.128216]   IO window: b000-bfff
Dec  5 09:55:44 Alphaone kernel: [   20.128219]   MEM window: fe600000-fe6fffff
Dec  5 09:55:44 Alphaone kernel: [   20.128221]   PREFETCH window: fe500000-fe5fffff
Dec  5 09:55:44 Alphaone kernel: [   20.128224] PCI: Bridge: 0000:00:0d.0
Dec  5 09:55:44 Alphaone kernel: [   20.128226]   IO window: a000-afff
Dec  5 09:55:44 Alphaone kernel: [   20.128228]   MEM window: fe400000-fe4fffff
Dec  5 09:55:44 Alphaone kernel: [   20.128231]   PREFETCH window: fe300000-fe3fffff
Dec  5 09:55:44 Alphaone kernel: [   20.128238] PCI: Bridge: 0000:00:0e.0
Dec  5 09:55:44 Alphaone kernel: [   20.128240]   IO window: 9000-9fff
Dec  5 09:55:44 Alphaone kernel: [   20.128242]   MEM window: fc000000-fdffffff
Dec  5 09:55:44 Alphaone kernel: [   20.128245]   PREFETCH window: c8000000-d7ffffff
Dec  5 09:55:44 Alphaone kernel: [   20.128287] NET: Registered protocol family 2
Dec  5 09:55:44 Alphaone kernel: [   20.167106] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec  5 09:55:44 Alphaone kernel: [   20.167231] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Dec  5 09:55:44 Alphaone kernel: [   20.168525] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec  5 09:55:44 Alphaone kernel: [   20.168984] TCP: Hash tables configured (established 131072 bind 65536)
Dec  5 09:55:44 Alphaone kernel: [   20.168986] TCP reno registered
Dec  5 09:55:44 Alphaone kernel: [   20.179168] checking if image is initramfs... it is
Dec  5 09:55:44 Alphaone kernel: [   20.630761] Switched to high resolution mode on CPU 0
Dec  5 09:55:44 Alphaone kernel: [   20.763937] Freeing initrd memory: 7356k freed
Dec  5 09:55:44 Alphaone kernel: [   20.764256] audit: initializing netlink socket (disabled)
Dec  5 09:55:44 Alphaone kernel: [   20.764267] audit(1196870098.100:1): initialized
Dec  5 09:55:44 Alphaone kernel: [   20.764321] highmem bounce pool size: 64 pages
Dec  5 09:55:44 Alphaone kernel: [   20.765648] VFS: Disk quotas dquot_6.5.1
Dec  5 09:55:44 Alphaone kernel: [   20.765692] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec  5 09:55:44 Alphaone kernel: [   20.765762] io scheduler noop registered
Dec  5 09:55:44 Alphaone kernel: [   20.765764] io scheduler anticipatory registered
Dec  5 09:55:44 Alphaone kernel: [   20.765766] io scheduler deadline registered
Dec  5 09:55:44 Alphaone kernel: [   20.765778] io scheduler cfq registered (default)
Dec  5 09:55:44 Alphaone kernel: [   20.765804] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
Dec  5 09:55:44 Alphaone kernel: [   20.765811] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Dec  5 09:55:44 Alphaone kernel: [   20.765817] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
Dec  5 09:55:44 Alphaone kernel: [   20.765824] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Dec  5 09:55:44 Alphaone kernel: [   20.765829] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
Dec  5 09:55:44 Alphaone kernel: [   20.765836] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Dec  5 09:55:44 Alphaone kernel: [   20.765841] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
Dec  5 09:55:44 Alphaone kernel: [   20.765848] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
Dec  5 09:55:44 Alphaone kernel: [   20.765948] assign_interrupt_mode Found MSI capability
Dec  5 09:55:44 Alphaone kernel: [   20.766015] assign_interrupt_mode Found MSI capability
Dec  5 09:55:44 Alphaone kernel: [   20.766079] assign_interrupt_mode Found MSI capability
Dec  5 09:55:44 Alphaone kernel: [   20.766150] assign_interrupt_mode Found MSI capability
Dec  5 09:55:44 Alphaone kernel: [   20.766238] isapnp: Scanning for PnP cards...
Dec  5 09:55:44 Alphaone kernel: [   21.118618] isapnp: No Plug & Play device found
Dec  5 09:55:44 Alphaone kernel: [   21.138404] Real Time Clock Driver v1.12ac
Dec  5 09:55:44 Alphaone kernel: [   21.138488] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec  5 09:55:44 Alphaone kernel: [   21.138569] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  5 09:55:44 Alphaone kernel: [   21.139079] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  5 09:55:44 Alphaone kernel: [   21.139591] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec  5 09:55:44 Alphaone kernel: [   21.139722] input: Macintosh mouse button emulation as /class/input/input0
Dec  5 09:55:44 Alphaone kernel: [   21.139773] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Dec  5 09:55:44 Alphaone kernel: [   21.139775] PNP: PS/2 controller doesn't have AUX irq; using default 12
Dec  5 09:55:44 Alphaone kernel: [   21.390493] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  5 09:55:44 Alphaone kernel: [   21.390598] mice: PS/2 mouse device common for all mice
Dec  5 09:55:44 Alphaone kernel: [   21.390683] EISA: Probing bus 0 at eisa.0
Dec  5 09:55:44 Alphaone kernel: [   21.390696] Cannot allocate resource for EISA slot 4
Dec  5 09:55:44 Alphaone kernel: [   21.390706] EISA: Detected 0 cards.
Dec  5 09:55:44 Alphaone kernel: [   21.390783] TCP cubic registered
Dec  5 09:55:44 Alphaone kernel: [   21.390797] NET: Registered protocol family 1
Dec  5 09:55:44 Alphaone kernel: [   21.390817] Using IPI No-Shortcut mode
Dec  5 09:55:44 Alphaone kernel: [   21.390966]   Magic number: 3:892:941
Dec  5 09:55:44 Alphaone kernel: [   21.391024]   hash matches device ptyyc
Dec  5 09:55:44 Alphaone kernel: [   21.391332] Freeing unused kernel memory: 364k freed
Dec  5 09:55:44 Alphaone kernel: [   21.466230] input: AT Translated Set 2 keyboard as /class/input/input1
Dec  5 09:55:44 Alphaone kernel: [   22.592319] AppArmor: AppArmor initialized<5>audit(1196870099.600:2):  type=1505 info="AppArmor initialized" pid=1242
Dec  5 09:55:44 Alphaone kernel: [   22.600021] fuse init (API version 7.8)
Dec  5 09:55:44 Alphaone kernel: [   22.604345] Failure registering capabilities with primary security module.
Dec  5 09:55:44 Alphaone kernel: [   22.620323] ACPI: Fan [FAN] (on)
Dec  5 09:55:44 Alphaone kernel: [   22.624217] ACPI: Processor [CPU0] (supports 8 throttling states)
Dec  5 09:55:44 Alphaone kernel: [   22.625271] ACPI: Thermal Zone [THRM] (31 C)
Dec  5 09:55:44 Alphaone kernel: [   23.144733] usbcore: registered new interface driver usbfs
Dec  5 09:55:44 Alphaone kernel: [   23.144765] usbcore: registered new interface driver hub
Dec  5 09:55:44 Alphaone kernel: [   23.144782] usbcore: registered new device driver usb
Dec  5 09:55:44 Alphaone kernel: [   23.145671] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Dec  5 09:55:44 Alphaone kernel: [   23.145679] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
Dec  5 09:55:44 Alphaone kernel: [   23.145694] ohci_hcd 0000:00:02.0: OHCI Host Controller
Dec  5 09:55:44 Alphaone kernel: [   23.145851] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Dec  5 09:55:44 Alphaone kernel: [   23.145865] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfebff000
Dec  5 09:55:44 Alphaone kernel: [   23.176356] SCSI subsystem initialized
Dec  5 09:55:44 Alphaone kernel: [   23.210572] usb usb1: configuration #1 chosen from 1 choice
Dec  5 09:55:44 Alphaone kernel: [   23.210595] hub 1-0:1.0: USB hub found
Dec  5 09:55:44 Alphaone kernel: [   23.210605] hub 1-0:1.0: 10 ports detected
Dec  5 09:55:44 Alphaone kernel: [   23.312986] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Dec  5 09:55:44 Alphaone kernel: [   23.312995] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 17
Dec  5 09:55:44 Alphaone kernel: [   23.313008] ohci_hcd 0000:01:06.0: OHCI Host Controller
Dec  5 09:55:44 Alphaone kernel: [   23.313027] ohci_hcd 0000:01:06.0: new USB bus registered, assigned bus number 2
Dec  5 09:55:44 Alphaone kernel: [   23.313042] ohci_hcd 0000:01:06.0: irq 17, io mem 0xfe9ff000
Dec  5 09:55:44 Alphaone kernel: [   23.313305] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Dec  5 09:55:44 Alphaone kernel: [   23.313310] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 18
Dec  5 09:55:44 Alphaone kernel: [   23.313318] ehci_hcd 0000:00:02.1: EHCI Host Controller
Dec  5 09:55:44 Alphaone kernel: [   23.313333] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
Dec  5 09:55:44 Alphaone kernel: [   23.313356] ehci_hcd 0000:00:02.1: debug port 1
Dec  5 09:55:44 Alphaone kernel: [   23.313366] ehci_hcd 0000:00:02.1: irq 18, io mem 0xfebfe000
Dec  5 09:55:44 Alphaone kernel: [   23.313371] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec  5 09:55:44 Alphaone kernel: [   23.313426] usb usb3: configuration #1 chosen from 1 choice
Dec  5 09:55:44 Alphaone kernel: [   23.313448] hub 3-0:1.0: USB hub found
Dec  5 09:55:44 Alphaone kernel: [   23.313455] hub 3-0:1.0: 10 ports detected
Dec  5 09:55:44 Alphaone kernel: [   23.340457] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
Dec  5 09:55:44 Alphaone kernel: [   23.416707] usb usb2: configuration #1 chosen from 1 choice
Dec  5 09:55:44 Alphaone kernel: [   23.416729] hub 2-0:1.0: USB hub found
Dec  5 09:55:44 Alphaone kernel: [   23.416738] hub 2-0:1.0: 3 ports detected
Dec  5 09:55:44 Alphaone kernel: [   23.469205] Floppy drive(s): fd0 is 1.44M
Dec  5 09:55:44 Alphaone kernel: [   23.515125] FDC 0 is a post-1991 82077
Dec  5 09:55:44 Alphaone kernel: [   23.520809] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Dec  5 09:55:44 Alphaone kernel: [   23.520819] ACPI: PCI Interrupt 0000:01:06.1[B] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
Dec  5 09:55:44 Alphaone kernel: [   23.520832] ohci_hcd 0000:01:06.1: OHCI Host Controller
Dec  5 09:55:44 Alphaone kernel: [   23.520899] ohci_hcd 0000:01:06.1: new USB bus registered, assigned bus number 4
Dec  5 09:55:44 Alphaone kernel: [   23.520914] ohci_hcd 0000:01:06.1: irq 19, io mem 0xfe9fe000
Dec  5 09:55:44 Alphaone kernel: [   23.606270] usb usb4: configuration #1 chosen from 1 choice
Dec  5 09:55:44 Alphaone kernel: [   23.606293] hub 4-0:1.0: USB hub found
Dec  5 09:55:44 Alphaone kernel: [   23.606302] hub 4-0:1.0: 2 ports detected
Dec  5 09:55:44 Alphaone kernel: [   23.708617] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Dec  5 09:55:44 Alphaone kernel: [   23.708626] ACPI: PCI Interrupt 0000:01:06.2[C] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20
Dec  5 09:55:44 Alphaone kernel: [   23.708638] ehci_hcd 0000:01:06.2: EHCI Host Controller
Dec  5 09:55:44 Alphaone kernel: [   23.708658] ehci_hcd 0000:01:06.2: new USB bus registered, assigned bus number 5
Dec  5 09:55:44 Alphaone kernel: [   23.732311] ehci_hcd 0000:01:06.2: irq 20, io mem 0xfe9fd000
Dec  5 09:55:44 Alphaone kernel: [   23.732319] ehci_hcd 0000:01:06.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec  5 09:55:44 Alphaone kernel: [   23.732392] usb usb5: configuration #1 chosen from 1 choice
Dec  5 09:55:44 Alphaone kernel: [   23.732414] hub 5-0:1.0: USB hub found
Dec  5 09:55:44 Alphaone kernel: [   23.732421] hub 5-0:1.0: 5 ports detected
Dec  5 09:55:44 Alphaone kernel: [   23.840537] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec  5 09:55:44 Alphaone kernel: [   23.840542] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec  5 09:55:44 Alphaone kernel: [   23.843008] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
Dec  5 09:55:44 Alphaone kernel: [   23.843028] NFORCE-CK804: chipset revision 162
Dec  5 09:55:44 Alphaone kernel: [   23.843030] NFORCE-CK804: not 100%% native mode: will probe irqs later
Dec  5 09:55:44 Alphaone kernel: [   23.843035] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
Dec  5 09:55:44 Alphaone kernel: [   23.843044]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
Dec  5 09:55:44 Alphaone kernel: [   23.843053]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd:DMA
Dec  5 09:55:44 Alphaone kernel: [   24.060044] usb 3-7: new high speed USB device using ehci_hcd and address 3
Dec  5 09:55:44 Alphaone kernel: [   24.128062] hda: Maxtor 91360U4, ATA DISK drive
Dec  5 09:55:44 Alphaone kernel: [   24.193164] usb 3-7: configuration #1 chosen from 1 choice
Dec  5 09:55:44 Alphaone kernel: [   24.193382] hub 3-7:1.0: USB hub found
Dec  5 09:55:44 Alphaone kernel: [   24.193744] hub 3-7:1.0: 4 ports detected
Dec  5 09:55:44 Alphaone kernel: [   24.407847] hdb: WDC WD1200AB-00DBA0, ATA DISK drive
Dec  5 09:55:44 Alphaone kernel: [   24.466086] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Dec  5 09:55:44 Alphaone kernel: [   24.727525] usb 1-5: new low speed USB device using ohci_hcd and address 2
Dec  5 09:55:44 Alphaone kernel: [   24.938264] usb 1-5: configuration #1 chosen from 1 choice
Dec  5 09:55:44 Alphaone kernel: [   25.179181] usb 5-1: new high speed USB device using ehci_hcd and address 2
Dec  5 09:55:44 Alphaone kernel: [   25.223216] hdc: SONY DVD RW DRU-810A, ATAPI CD/DVD-ROM drive
Dec  5 09:55:44 Alphaone kernel: [   25.314358] usb 5-1: configuration #1 chosen from 1 choice
Dec  5 09:55:44 Alphaone kernel: [   25.316214] usbcore: registered new interface driver hiddev
Dec  5 09:55:44 Alphaone kernel: [   25.327047] input: HID 04d9:0499 as /class/input/input2
Dec  5 09:55:44 Alphaone kernel: [   25.327080] input: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:02.0-5
Dec  5 09:55:44 Alphaone kernel: [   25.327094] usbcore: registered new interface driver usbhid
Dec  5 09:55:44 Alphaone kernel: [   25.327097] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Dec  5 09:55:44 Alphaone kernel: [   25.328656] usbcore: registered new interface driver libusual
Dec  5 09:55:44 Alphaone kernel: [   25.331933] Initializing USB Mass Storage driver...
Dec  5 09:55:44 Alphaone kernel: [   25.332012] scsi0 : SCSI emulation for USB Mass Storage devices
Dec  5 09:55:44 Alphaone kernel: [   25.332058] usbcore: registered new interface driver usb-storage
Dec  5 09:55:44 Alphaone kernel: [   25.332061] USB Mass Storage support registered.
Dec  5 09:55:44 Alphaone kernel: [   25.895416] ide1 at 0x170-0x177,0x376 on irq 15
Dec  5 09:55:44 Alphaone kernel: [   25.897562] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
Dec  5 09:55:44 Alphaone kernel: [   25.897571] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
Dec  5 09:55:44 Alphaone kernel: [   25.897583] forcedeth: using HIGHDMA
Dec  5 09:55:44 Alphaone kernel: [   25.904169] hda: max request size: 128KiB
Dec  5 09:55:44 Alphaone kernel: [   25.915949] hda: 26588016 sectors (13613 MB) w/2048KiB Cache, CHS=26377/16/63, UDMA(66)
Dec  5 09:55:44 Alphaone kernel: [   25.915956] hda: cache flushes not supported
Dec  5 09:55:44 Alphaone kernel: [   25.915990]  hda: hda1 hda2
Dec  5 09:55:44 Alphaone kernel: [   25.924000] hdb: max request size: 512KiB
Dec  5 09:55:44 Alphaone kernel: [   25.925032] hdb: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
Dec  5 09:55:44 Alphaone kernel: [   25.926388] hdb: cache flushes supported
Dec  5 09:55:44 Alphaone kernel: [   25.926409]  hdb:hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec  5 09:55:44 Alphaone kernel: [   25.937050] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
Dec  5 09:55:44 Alphaone kernel: [   25.937053] ide: failed opcode was: unknown
Dec  5 09:55:44 Alphaone kernel: [   25.937386] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec  5 09:55:44 Alphaone kernel: [   25.937389] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
Dec  5 09:55:44 Alphaone kernel: [   25.937391] ide: failed opcode was: unknown
Dec  5 09:55:44 Alphaone kernel: [   25.938806] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec  5 09:55:44 Alphaone kernel: [   25.938809] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
Dec  5 09:55:44 Alphaone kernel: [   25.938812] ide: failed opcode was: unknown
Dec  5 09:55:44 Alphaone kernel: [   25.939075] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Dec  5 09:55:44 Alphaone kernel: [   25.939078] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
Dec  5 09:55:44 Alphaone kernel: [   25.939080] ide: failed opcode was: unknown
Dec  5 09:55:44 Alphaone kernel: [   25.939083] hda: DMA disabled
Dec  5 09:55:44 Alphaone kernel: [   25.986550] ide0: reset: success
Dec  5 09:55:44 Alphaone kernel: [   25.995151]  hdb1 < hdb5 >
Dec  5 09:55:44 Alphaone kernel: [   26.024971] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Dec  5 09:55:44 Alphaone kernel: [   26.024979] Uniform CD-ROM driver Revision: 3.20
Dec  5 09:55:44 Alphaone kernel: [   26.414455] eth0: forcedeth.c: subsystem: 01565:2501 bound to 0000:00:0a.0
Dec  5 09:55:44 Alphaone kernel: [   26.414570] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20
Dec  5 09:55:44 Alphaone kernel: [   26.467339] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fe9fc000-fe9fc7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Dec  5 09:55:44 Alphaone kernel: [   26.472676] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Dec  5 09:55:44 Alphaone kernel: [   26.472684] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 22
Dec  5 09:55:44 Alphaone kernel: [   26.472687] sata_nv 0000:00:07.0: Using ADMA mode
Dec  5 09:55:44 Alphaone kernel: [   26.472815] scsi1 : sata_nv
Dec  5 09:55:44 Alphaone kernel: [   26.472850] scsi2 : sata_nv
Dec  5 09:55:44 Alphaone kernel: [   26.472895] ata1: SATA max UDMA/133 cmd 0xf88c8480 ctl 0xf88c84a0 bmdma 0x0001f600 irq 22
Dec  5 09:55:44 Alphaone kernel: [   26.472899] ata2: SATA max UDMA/133 cmd 0xf88c8580 ctl 0xf88c85a0 bmdma 0x0001f608 irq 22
Dec  5 09:55:44 Alphaone kernel: [   26.617960] Attempting manual resume
Dec  5 09:55:44 Alphaone kernel: [   26.659869] EXT3-fs: INFO: recovery required on readonly filesystem.
Dec  5 09:55:44 Alphaone kernel: [   26.659873] EXT3-fs: write access will be enabled during recovery.
Dec  5 09:55:44 Alphaone kernel: [   26.781944] ata1: SATA link down (SStatus 0 SControl 300)
Dec  5 09:55:44 Alphaone kernel: [   27.093697] ata2: SATA link down (SStatus 0 SControl 300)
Dec  5 09:55:44 Alphaone kernel: [   27.094102] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Dec  5 09:55:44 Alphaone kernel: [   27.094106] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
Dec  5 09:55:44 Alphaone kernel: [   27.094111] sata_nv 0000:00:08.0: Using ADMA mode
Dec  5 09:55:44 Alphaone kernel: [   27.094272] scsi3 : sata_nv
Dec  5 09:55:44 Alphaone kernel: [   27.094329] scsi4 : sata_nv
Dec  5 09:55:44 Alphaone kernel: [   27.094375] ata3: SATA max UDMA/133 cmd 0xf8874480 ctl 0xf88744a0 bmdma 0x0001f100 irq 16
Dec  5 09:55:44 Alphaone kernel: [   27.094378] ata4: SATA max UDMA/133 cmd 0xf8874580 ctl 0xf88745a0 bmdma 0x0001f108 irq 16
Dec  5 09:55:44 Alphaone kernel: [   27.405498] ata3: SATA link down (SStatus 0 SControl 300)
Dec  5 09:55:44 Alphaone kernel: [   27.717258] ata4: SATA link down (SStatus 0 SControl 300)
Dec  5 09:55:44 Alphaone kernel: [   30.329955] scsi 0:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Dec  5 09:55:44 Alphaone kernel: [   30.330673] scsi 0:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Dec  5 09:55:44 Alphaone kernel: [   30.331427] scsi 0:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Dec  5 09:55:44 Alphaone kernel: [   30.332137] scsi 0:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Dec  5 09:55:44 Alphaone kernel: [   30.346731] sd 0:0:0:0: [sda] Attached SCSI removable disk
Dec  5 09:55:44 Alphaone kernel: [   30.348634] sd 0:0:0:1: [sdb] Attached SCSI removable disk
Dec  5 09:55:44 Alphaone kernel: [   30.350049] sd 0:0:0:2: [sdc] Attached SCSI removable disk
Dec  5 09:55:44 Alphaone kernel: [   30.351562] sd 0:0:0:3: [sdd] Attached SCSI removable disk
Dec  5 09:55:44 Alphaone kernel: [   30.359330] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec  5 09:55:44 Alphaone kernel: [   30.359348] sd 0:0:0:1: Attached scsi generic sg1 type 0
Dec  5 09:55:44 Alphaone kernel: [   30.359364] sd 0:0:0:2: Attached scsi generic sg2 type 0
Dec  5 09:55:44 Alphaone kernel: [   30.359379] sd 0:0:0:3: Attached scsi generic sg3 type 0
Dec  5 09:55:44 Alphaone kernel: [   48.151406] kjournald starting.  Commit interval 5 seconds
Dec  5 09:55:44 Alphaone kernel: [   48.151421] EXT3-fs: hda2: orphan cleanup on readonly fs
Dec  5 09:55:44 Alphaone kernel: [   48.659613] EXT3-fs: hda2: 2 orphan inodes deleted
Dec  5 09:55:44 Alphaone kernel: [   48.659615] EXT3-fs: recovery complete.
Dec  5 09:55:44 Alphaone kernel: [   48.669702] EXT3-fs: mounted filesystem with ordered data mode.
Dec  5 09:55:44 Alphaone kernel: [   61.988286] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
Dec  5 09:55:44 Alphaone kernel: [   61.988314] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
Dec  5 09:55:44 Alphaone kernel: [   62.597022] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec  5 09:55:44 Alphaone kernel: [   62.613692] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec  5 09:55:44 Alphaone kernel: [   63.403384] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
Dec  5 09:55:44 Alphaone kernel: [   63.403389] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 18
Dec  5 09:55:44 Alphaone kernel: [   63.427088] Linux agpgart interface v0.102 (c) Dave Jones
Dec  5 09:55:44 Alphaone kernel: [   63.556325] input: PC Speaker as /class/input/input3
Dec  5 09:55:44 Alphaone kernel: [   63.725368] intel8x0_measure_ac97_clock: measured 54840 usecs
Dec  5 09:55:44 Alphaone kernel: [   63.725372] intel8x0: clocking to 46866
Dec  5 09:55:44 Alphaone kernel: [   63.784025] parport_pc 00:09: reported by Plug and Play ACPI
Dec  5 09:55:44 Alphaone kernel: [   63.784067] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Dec  5 09:55:44 Alphaone kernel: [   64.288086] lp0: using parport0 (interrupt-driven).
Dec  5 09:55:44 Alphaone kernel: [   64.369596] Adding 3903752k swap on /dev/hda1.  Priority:-1 extents:1 across:3903752k
Dec  5 09:55:44 Alphaone kernel: [   64.645729] EXT3 FS on hda2, internal journal
Dec  5 09:55:44 Alphaone kernel: [   65.271513] kjournald starting.  Commit interval 5 seconds
Dec  5 09:55:44 Alphaone kernel: [   65.276259] EXT3 FS on hdb5, internal journal
Dec  5 09:55:44 Alphaone kernel: [   65.276263] EXT3-fs: mounted filesystem with ordered data mode.
Dec  5 09:55:44 Alphaone kernel: [   65.953213] No dock devices found.
Dec  5 09:55:44 Alphaone kernel: [   66.101452] input: Power Button (FF) as /class/input/input4
Dec  5 09:55:44 Alphaone kernel: [   66.105440] ACPI: Power Button (FF) [PWRF]
Dec  5 09:55:44 Alphaone kernel: [   66.139177] input: Power Button (CM) as /class/input/input5
Dec  5 09:55:44 Alphaone kernel: [   66.143098] ACPI: Power Button (CM) [PWRB]
Dec  5 09:55:44 Alphaone kernel: [   66.175693] input: Sleep Button (CM) as /class/input/input6
Dec  5 09:55:44 Alphaone kernel: [   66.179635] ACPI: Sleep Button (CM) [SLPB]
Dec  5 09:55:44 Alphaone kernel: [   66.417589] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
Dec  5 09:55:45 Alphaone kernel: [   68.148055] ppdev: user-space parallel port driver
Dec  5 09:55:46 Alphaone kernel: [   68.492863] audit(1196870145.869:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5228 profile="/usr/sbin/cupsd"
Dec  5 09:55:46 Alphaone kernel: [   68.738765] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Dec  5 09:55:46 Alphaone kernel: [   68.738770] apm: overridden by ACPI.
Dec  5 09:55:49 Alphaone kernel: [   71.273757] Failure registering capabilities with primary security module.
Dec  5 09:55:49 Alphaone dhcdbd: Started up.
Dec  5 09:55:49 Alphaone kernel: [   71.555915] Bluetooth: Core ver 2.11
Dec  5 09:55:49 Alphaone kernel: [   71.556187] NET: Registered protocol family 31
Dec  5 09:55:49 Alphaone kernel: [   71.556190] Bluetooth: HCI device and connection manager initialized
Dec  5 09:55:49 Alphaone kernel: [   71.556193] Bluetooth: HCI socket layer initialized
Dec  5 09:55:49 Alphaone kernel: [   71.575953] Bluetooth: L2CAP ver 2.8
Dec  5 09:55:49 Alphaone kernel: [   71.575957] Bluetooth: L2CAP socket layer initialized
Dec  5 09:55:49 Alphaone kernel: [   71.705611] Bluetooth: RFCOMM socket layer initialized
Dec  5 09:55:49 Alphaone kernel: [   71.705905] Bluetooth: RFCOMM TTY layer initialized
Dec  5 09:55:49 Alphaone kernel: [   71.705908] Bluetooth: RFCOMM ver 1.8
Dec  5 09:55:51 Alphaone dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec  5 09:55:53 Alphaone kernel: [   76.145785] NET: Registered protocol family 17
Dec  5 09:55:56 Alphaone dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Dec  5 09:55:56 Alphaone dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 
Dec  5 09:55:56 Alphaone dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Dec  5 09:55:56 Alphaone dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec  5 09:55:56 Alphaone dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec  5 09:55:57 Alphaone kernel: [   80.055920] NET: Registered protocol family 10
Dec  5 09:55:57 Alphaone kernel: [   80.056459] lo: Disabled Privacy Extensions

```

---

### Post by 11hjpphty76lkjj on 2007-12-05
Sorry could we try this one more time?

just run the tail -f /var/log/messages and then try to print.  it should be a lot shorter. :)

A

---

### Post by da Wookiee on 2007-12-05
When I run the tail I get this

```
Dec  5 19:37:41 Alphaone kernel: [ 3220.320116] atkbd.c: Use 'setkeycodes e025 <keycode>' to make it known.
Dec  5 19:37:55 Alphaone kernel: [ 3233.995111] atkbd.c: Unknown key pressed (translated set 2, code 0xa5 on isa0060/serio0).
Dec  5 19:37:55 Alphaone kernel: [ 3233.995116] atkbd.c: Use 'setkeycodes e025 <keycode>' to make it known.
Dec  5 19:37:55 Alphaone kernel: [ 3234.238300] atkbd.c: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
Dec  5 19:37:55 Alphaone kernel: [ 3234.238303] atkbd.c: Use 'setkeycodes e025 <keycode>' to make it known.
Dec  5 19:37:55 Alphaone kernel: [ 3234.342052] atkbd.c: Unknown key pressed (translated set 2, code 0xa5 on isa0060/serio0).
Dec  5 19:37:55 Alphaone kernel: [ 3234.342055] atkbd.c: Use 'setkeycodes e025 <keycode>' to make it known.
Dec  5 19:37:55 Alphaone kernel: [ 3234.484495] atkbd.c: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
Dec  5 19:37:55 Alphaone kernel: [ 3234.484498] atkbd.c: Use 'setkeycodes e025 <keycode>' to make it known.
Dec  5 19:45:29 Alphaone kernel: [ 3688.295057] usb 5-1: reset high speed USB device using ehci_hcd and address 2
```

And the terminal hangs, so I open another terminal and run hp-setup
```

error: No devices found.Please make sure your printer is properly connected and powered-on.

```

And that's what I get in the terminal after the gui terminates.

Here's the last few lines from /var/log/messages that have the proper timecode to be pertinent.



```
Dec  5 19:45:29 Alphaone kernel: [ 3688.295057] usb 5-1: reset high speed USB device using ehci_hcd and address 2
Dec  5 19:51:39 Alphaone kernel: [ 4058.018548] usb 5-1: reset high speed USB device using ehci_hcd and address 2

```

---

### Post by 11hjpphty76lkjj on 2007-12-06
Everything looks fine.  After reviewing the thread it seems with the reinstalling there may be something conflicting or corrupted. You may want to try removing all of the printing system and re-installing.

```
sudo apt-get remove hplip cupsys gs foomatic-hpijs
```then

```
sudo updatedb
```then

```
locate hplip
```if you still have stuff in the /usr/share/hplip you'll want to remove that directory:

[COLOR=Red]USE CAUTION[/COLOR]
```

sudo rm -rf /usr/share/hplip

```and then:

```
sudo apt-get install cupsys gs foomatic-hpijs
```and finally reinstalling hplip from source at [http://hplip.sf.net](http://hplip.sf.net)

Hope this helps!

A

---

### Post by da Wookiee on 2007-12-07
That seems to have worked.!!!!!!!!!!!!!!!!!!!!!!!!!1


:)


Just remember if you get a 

```
 Unable to send broadcast SLP packet: (1, 'Operation not permitted')
```

error, it probably means your personal firewall is installed and you need to disable it for a bit.


Thanks a lot for your help!!!

---

### Post by da Wookiee on 2007-12-14
Well it was working anyway.  The IP address for my printer got reset by the DHCP server, and it hasn't worked right since.  I changed the ip address port for the Vista computer, updated the firewall, and it's happy as a clam.

The best I can get from ubuntu is one sided, and then it hangs forever on the second side.  I tried printing the same file from OpenOffice on both systems, so I'm pretty sure it isn't the network itself.  Now I just have to fix the setting but I don't know for sure how.  I tried to purge and reinstall, but it's not working yet.

---

