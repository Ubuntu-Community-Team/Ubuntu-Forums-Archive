---
title: "Intel 945GM / GMA 950 / 3945ABG support"
date: 2006-09-07
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2006-09-07
Hello,

I've already started a few threads about my laptop. It's an Averatec 2460, Intel Core Duo CPU, Intel 945GM chipset with S-ATA harddisk, Intel GMA 950 graphics, Intel 3945ABG wireless & RealTek 8139 NIC.

The problem is that Ubuntu 6.06 and the pre-rleases of 6.10 won't install, the LiveCD/Alternate CD hangs during hardware detection. But I managed to get Gentoo running on this notebook. Graphics & onboard NIC is working fine, wireless works (but not with encryption turned on), I even have AIGLX+Compiz running. What I didn't get to work is suspend-to-ram and suspend-to-disk.

Now a friend suggested I should try Ubuntu 5.10 and indeed the Ubuntu 5.10 LiveCD works, it detects the onboard NIC, though not the wireless. X won't start, but when I select "vesa" as a driver  this works too. So now my plan is o install Ubuntu 5.10 on this machine, and right afterwards upgrade to Dapper - I hope this works. Before I try this, I'd like to know how and if my hardware is supported. I'd would be kind of you to tell me about your experience running Ubuntu 6.06 on my hardware. The most importanting thing is graphics (with the i810 driver in widescreen, 1280x800), the onboard network & sound (Intel HDA). Suspend-to-RAM & Suspend-to-Disk would be nice but it's not essential, wireless would also be nice but is not essential.

I'd be very thankful if some of you could tell me if and how good my hardare is working with Ubunut 5.10 and/or Ubuntu 6.06:

- Intel Core Duo T2300 1.66GHz

- Intel 945GM chipset

- Intel GMA 950 graphics in 1280x800 widescreen

- Intel HD audio

- RealTek 8139 onboard NIC

- Intel 3945ABG wireless

- S-ATA harddisk, CD/DVD burner

- USB

- Power management features

- CPU speedstepping

Thanks for your help, I really hope that I can finally get my loved Ubuntu running on my loved new notebook ;-)


Tom

---

### Post by iLoVe.cF- on 2006-09-07
Hum... gonna work after some trubleing.. the display reselution may be a issue.. but is a fix probaly sound.. dont know..

The hardware is good enough tho.. ;)

I use asus a3e 

Intel centrino 1.5 ghz
1.5 gb memory
intel 915 128 mb
80 gb
realtek 880 intel-hda

works fast but have video card issues right now :'(

---

### Post by Liquid2006 on 2006-09-10
I had issues with the sound running the 945GM but I suspect this was due to running it on an Acer (there was an Acer specific patch). Getting the latest Alsa and compiling it fixed this issue.

I compiled the Intel 3945 wireless driver from the latest version along with Network Manager and this enabled the ability to connect to WPA networks. [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

The graphics worked fine but I was limited in the resolution I could select until I installed the 915resolution package.

All in all most things worked fine but needed just a little tweaking.

Ive had no luck with suspend-to-ram though and I have read that the DSDT table needs to be rewritten but this is something Im not willing to do so will just wait for the next release and hope.

---

### Post by el3ktro on 2006-09-10
Hi well I managed to istall Breezy and then upgrade to Dapper now. The Dapper kernel wouldn't boot, so I booted with the old Breezy kernel into Dapper, and then re-compiled the original Dapper kernel with only one thing chnaged:

I selected "Use PIO instead of MMIO" for the 8139too module - this was it, and the Dapper kernel booted. I can't believe that one single option in one single module can prevent the whole OS from even installing or booting.

Well right now everythig works, including graphics, sound, wireless, network - except I have some issues with my CPU. It's an Intel Core Duo - and it constantly is at around 50% (both cores). I didn't yet figured out how to solve that, and it kind of scares me to have the CPU at 50% constantly, the mouse pointer sometimes lags.

Tom

---

### Post by Liquid2006 on 2006-09-11
> **el3ktro said:**
> 
It's an Intel Core Duo - and it constantly is at around 50% (both cores). I didn't yet figured out how to solve that, and it kind of scares me to have the CPU at 50% constantly, the mouse pointer sometimes lags.

Tom

I would be interested to see the results of ps -f and dmesg to see whats triggering the high cpu useage. Sounds very odd indeed.

---

### Post by mrojas73 on 2006-09-12
I have an Acer 5601 AWLMI, very similar to yours I think.  I have done the same as you to get it the resolition working correctly, for the sound and wireless.  I would like to get xgl running but I don't know if it is possilbe with the GMA950 card.  Anyways, I get some ACPI erros at boot time but I don't know what they mean, here is my dmesg which shows the error at the begining.
Thanks!


```

0x1f69ae94
[17179569.184000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69aefc
[17179569.184000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x1f69af34
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x1f69af70
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f69afd8
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x1f69352d
[17179569.184000] ACPI: DSDT (v001 INTEL  CALISTGA 0x06040000 MSFT 0x02000002) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: 2 duplicate APIC table ignored.
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1 already used, trying 2
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)[17179569.184000] Memory: 498536k/514624k available (2110k kernel code, 15500k reserved, 595k data, 332k init, 0k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xe0000000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1600.088 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 3204.14 BogoMIPS (lpj=6408296)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[17179569.268000] CPU: After vendor identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 2048K
[17179569.268000] CPU: Hyper-Threading is disabled
[17179569.268000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00000040 0000c189 00000000 00000000
[17179569.268000] mtrr: v2.0 (20020519)
[17179569.268000] Enabling fast FPU save and restore... done.
[17179569.268000] Enabling unmasked SIMD FPU exception support... done.
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] checking if image is initramfs... it is
[17179569.908000] Freeing initrd memory: 6809k freed
[17179569.940000] ACPI: Looking for DSDT ... not found!
[17179569.944000] CPU0: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[17179569.944000] SMP alternatives: switching to SMP code
[17179569.944000] Booting processor 1/1 eip 3000
[17179569.956000] Initializing CPU#1
[17179570.036000] Calibrating delay using timer specific routine.. 3200.44 BogoMIPS (lpj=6400884)
[17179570.036000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[17179570.036000] CPU: After vendor identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[17179570.036000] monitor/mwait feature present.
[17179570.036000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.036000] CPU: L2 cache: 2048K
[17179570.036000] CPU: Hyper-Threading is disabled
[17179570.036000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00000040 0000c189 00000000 00000000
[17179570.036000] CPU1: Intel Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[17179570.036000] Total of 2 processors activated (6404.59 BogoMIPS).
[17179570.036000] ENABLING IO-APIC IRQs
[17179570.036000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.188000] checking TSC synchronization across 2 CPUs: passed.
[17179570.192000] Brought up 2 CPUs
[17179570.192000] NET: Registered protocol family 16
[17179570.192000] EISA bus registered
[17179570.192000] ACPI: bus type pci registered
[17179570.216000] PCI: PCI BIOS revision 2.10 entry at 0xfd6f2, last bus=11
[17179570.216000] PCI: Using MMCONFIG
[17179570.216000] ACPI: Subsystem revision 20051216
[17179570.220000] ACPI: Interpreter enabled
[17179570.220000] ACPI: Using IOAPIC for interrupt routing
[17179570.220000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.220000] PCI: Probing PCI hardware (bus 00)
[17179570.220000] Boot video device is 0000:00:02.0
[17179570.220000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.224000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.224000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.228000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179570.228000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[17179570.228000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[17179570.228000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[17179570.232000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.232000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179570.232000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179570.232000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179570.232000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179570.232000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179570.232000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179570.232000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[17179570.232000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179570.232000] ACPI: Embedded Controller [EC0] (gpe 23) interrupt mode.
[17179570.268000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.268000] pnp: PnP ACPI init
[17179570.272000] pnp: PnP ACPI: found 9 devices
[17179570.272000] PnPBIOS: Disabled by ACPI PNP
[17179570.272000] PCI: Using ACPI for IRQ routing
[17179570.272000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.272000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.272000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.272000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.272000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.272000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.272000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.272000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.272000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.272000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[17179570.272000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.3
[17179570.272000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
[17179570.272000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.3
[17179570.308000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.308000] PCI: Bridge: 0000:00:1c.0
[17179570.308000]   IO window: disabled.
[17179570.308000]   MEM window: 32000000-320fffff
[17179570.308000]   PREFETCH window: disabled.
[17179570.308000] PCI: Bridge: 0000:00:1c.1
[17179570.308000]   IO window: disabled.
[17179570.308000]   MEM window: disabled.
[17179570.308000]   PREFETCH window: disabled.
[17179570.308000] PCI: Bridge: 0000:00:1c.2
[17179570.308000]   IO window: disabled.
[17179570.308000]   MEM window: disabled.
[17179570.308000]   PREFETCH window: disabled.
[17179570.308000] PCI: Bridge: 0000:00:1c.3
[17179570.308000]   IO window: disabled.
[17179570.308000]   MEM window: disabled.
[17179570.308000]   PREFETCH window: disabled.
[17179570.308000] PCI: Bus 11, cardbus bridge: 0000:0a:09.0
[17179570.308000]   IO window: 00002400-000024ff
[17179570.308000]   IO window: 00002800-000028ff
[17179570.308000]   PREFETCH window: 30000000-31ffffff
[17179570.308000]   MEM window: 34000000-35ffffff
[17179570.308000] PCI: Bridge: 0000:00:1e.0
[17179570.308000]   IO window: 2000-2fff
[17179570.308000]   MEM window: b0300000-b03fffff
[17179570.308000]   PREFETCH window: 30000000-31ffffff
[17179570.308000] PCI: Enabling device 0000:00:1c.0 (0000 -> 0002)
[17179570.308000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.308000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.308000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179570.308000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.308000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179570.308000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.308000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 193
[17179570.308000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179570.308000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.308000] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179570.308000] Simple Boot Flag at 0x3e set to 0x1
[17179570.308000] audit: initializing netlink socket (disabled)
[17179570.308000] audit(1158066147.304:1): initialized
[17179570.308000] VFS: Disk quotas dquot_6.5.1
[17179570.308000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.308000] Initializing Cryptographic API
[17179570.308000] io scheduler noop registered
[17179570.308000] io scheduler anticipatory registered
[17179570.308000] io scheduler deadline registered
[17179570.308000] io scheduler cfq registered
[17179570.308000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.308000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.308000] assign_interrupt_mode Found MSI capability
[17179570.308000] Allocate Port Service[pcie00]
[17179570.308000] Allocate Port Service[pcie02]
[17179570.308000] Allocate Port Service[pcie03]
[17179570.308000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179570.308000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179570.308000] assign_interrupt_mode Found MSI capability
[17179570.308000] Allocate Port Service[pcie00]
[17179570.308000] Allocate Port Service[pcie02]
[17179570.308000] Allocate Port Service[pcie03]
[17179570.308000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179570.308000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[17179570.308000] assign_interrupt_mode Found MSI capability
[17179570.308000] Allocate Port Service[pcie00]
[17179570.308000] Allocate Port Service[pcie02]
[17179570.308000] Allocate Port Service[pcie03]
[17179570.308000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 193
[17179570.308000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179570.308000] assign_interrupt_mode Found MSI capability
[17179570.308000] Allocate Port Service[pcie00]
[17179570.308000] Allocate Port Service[pcie02]
[17179570.308000] Allocate Port Service[pcie03]
[17179570.308000] isapnp: Scanning for PnP cards...
[17179570.664000] isapnp: No Plug & Play device found
[17179570.684000] Real Time Clock Driver v1.12
[17179570.684000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.684000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179570.684000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179570.688000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179570.688000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179570.688000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179570.688000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.688000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.688000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.688000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.688000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.688000] mice: PS/2 mouse device common for all mice
[17179570.688000] EISA: Probing bus 0 at eisa.0
[17179570.688000] Cannot allocate resource for EISA slot 1
[17179570.688000] Cannot allocate resource for EISA slot 2
[17179570.688000] EISA: Detected 0 cards.
[17179570.688000] NET: Registered protocol family 2
[17179570.740000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.740000] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[17179570.740000] TCP bind hash table entries: 16384 (order: 5, 196608 bytes)
[17179570.740000] TCP: Hash tables configured (established 16384 bind 16384)
[17179570.740000] TCP reno registered
[17179570.740000] TCP bic registered
[17179570.740000] NET: Registered protocol family 1
[17179570.740000] NET: Registered protocol family 8
[17179570.740000] NET: Registered protocol family 20
[17179570.740000] Starting balanced_irq
[17179570.740000] Using IPI No-Shortcut mode
[17179570.740000] ACPI wakeup devices:
[17179570.740000] HDEF PXS1 LANE PXS4 PXS5 PXS6 USB1 USB2 USB3 USB4 USB7 LANC
[17179570.740000] ACPI: (supports S0 S3 S4 S5)
[17179570.740000] Freeing unused kernel memory: 332k freed
[17179570.788000] vga16fb: initializing
[17179570.788000] vga16fb: mapped to 0xc00a0000
[17179570.860000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.904000] Console: switching to colour frame buffer device 80x25
[17179570.904000] fb0: VGA16 VGA frame buffer device
[17179571.944000] Capability LSM initialized
[17179572.000000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179572.000000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.004000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[17179572.004000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179572.008000] ACPI: Thermal Zone [THRM] (35 C)
[17179572.416000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179572.416000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 185
[17179572.416000] ICH7: chipset revision 2
[17179572.416000] ICH7: not 100% native mode: will probe irqs later
[17179572.416000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
[17179572.416000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:pio, hdd:pio
[17179572.416000] Probing IDE interface ide0...
[17179572.708000] hda: HTS721080G9AT00, ATA DISK drive
[17179573.492000] hdb: MATSHITADVD-RAM UJ-850S, ATAPI CD/DVD-ROM drive
[17179573.548000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.568000] Probing IDE interface ide1...
[17179574.140000] hda: max request size: 1024KiB
[17179574.140000] hda: 156301488 sectors (80026 MB) w/7539KiB Cache, CHS=16383/255/63, UDMA(33)
[17179574.140000] hda: cache flushes supported
[17179574.140000]  hda: hda1 hda2 < hda5 >
[17179574.208000] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.208000] Uniform CD-ROM driver Revision: 3.20
[17179574.444000] usbcore: registered new driver usbfs
[17179574.444000] usbcore: registered new driver hub
[17179574.448000] USB Universal Host Controller Interface driver v2.3
[17179574.448000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 58
[17179574.448000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.448000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.452000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.452000] uhci_hcd 0000:00:1d.0: irq 58, io base 0x00001820
[17179574.452000] hub 1-0:1.0: USB hub found
[17179574.452000] hub 1-0:1.0: 2 ports detected
[17179574.556000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179574.556000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.556000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179574.556000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179574.556000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x00001840
[17179574.556000] hub 2-0:1.0: USB hub found
[17179574.556000] hub 2-0:1.0: 2 ports detected
[17179574.660000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 185
[17179574.660000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179574.660000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179574.660000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179574.660000] uhci_hcd 0000:00:1d.2: irq 185, io base 0x00001860
[17179574.660000] hub 3-0:1.0: USB hub found
[17179574.660000] hub 3-0:1.0: 2 ports detected
[17179574.764000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 177
[17179574.764000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179574.764000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179574.764000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179574.764000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x00001880
[17179574.764000] hub 4-0:1.0: USB hub found
[17179574.764000] hub 4-0:1.0: 2 ports detected
[17179574.868000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 58
[17179574.868000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179574.868000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179574.868000] ehci_hcd 0000:00:1d.7: debug port 1
[17179574.868000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179574.868000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179574.868000] ehci_hcd 0000:00:1d.7: irq 58, io mem 0xb0004000
[17179574.872000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.872000] hub 5-0:1.0: USB hub found
[17179574.872000] hub 5-0:1.0: 8 ports detected
[17179574.988000] Probing IDE interface ide1...
[17179575.656000] Attempting manual resume
[17179575.716000] EXT3-fs: mounted filesystem with ordered data mode.
[17179575.716000] kjournald starting.  Commit interval 5 seconds
[17179584.476000] Linux agpgart interface v0.101 (c) Dave Jones
[17179584.480000] agpgart: Detected an Intel 945GM Chipset.
[17179584.480000] agpgart: Detected 7932K stolen memory.
[17179584.500000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179584.600000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179584.612000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179584.828000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17179584.844000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13[17179584.844000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179584.856000] ieee80211_crypt: registered algorithm 'NULL'
[17179584.860000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179584.860000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179584.968000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m
[17179584.968000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179584.968000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17179584.968000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179584.968000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179584.972000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179584.976000] hw_random: RNG not detected
[17179585.004000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 66
[17179585.004000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179585.100000] 8139too Fast Ethernet driver 0.9.27
[17179585.120000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179585.120000] sdhci: Copyright(c) Pierre Ossman
[17179585.408000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[17179585.464000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179585.488000] ts: Compaq touchscreen protocol output
[17179585.888000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[17179585.892000] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179585.892000] eth0: RealTek RTL8139 at 0xe0178000, 00:16:36:5e:3a:78, IRQ 169
[17179585.892000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179585.908000] ACPI: PCI Interrupt 0000:0a:09.3[A] -> GSI 20 (level, low) -> IRQ 201
[17179585.944000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179585.944000] ACPI: PCI Interrupt 0000:0a:09.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179585.944000] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0102]
[17179585.944000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179585.944000] Yenta: Routing CardBus interrupts to PCI
[17179585.944000] Yenta TI: socket 0000:0a:09.0, mfunc 0x01321b22, devctl 0x66
[17179585.956000] sdhci: ============== REGISTER DUMP ==============
[17179585.956000] sdhci: Sys addr: 0x00000000 | Version:  0x00008900
[17179585.956000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179585.956000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179585.956000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179585.956000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179585.956000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[17179585.956000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179585.956000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179585.956000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179585.956000] sdhci: Caps:     0x01e030b0 | Max curr: 0x00000034
[17179585.956000] sdhci: ===========================================
[17179586.008000] mmc0: SDHCI at 0xb0300400 irq 201 DMA
[17179586.152000] eth0: link down
[17179586.204000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 201
[17179586.204000] Socket status: 30000006
[17179586.204000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[17179586.204000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179586.204000] cs: IO port probe 0x2000-0x2fff: clean.
[17179586.204000] pcmcia: parent PCI bridge Memory window: 0xb0300000 - 0xb03fffff
[17179586.204000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179586.492000] ALSA /home/mrojas/Desktop/alsa-driver-1.0.13rc1/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:537: hda_intel: azx_get_response timeout, switching to polling mode...
[17179586.540000] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x370-0x377
[17179586.544000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179586.544000] cs: IO port probe 0x820-0x8ff: clean.
[17179586.544000] cs: IO port probe 0xc00-0xcf7: clean.
[17179586.544000] cs: IO port probe 0xa00-0xaff: clean.
[17179586.676000] lp: driver loaded but no devices found
[17179586.728000] Adding 1477940k swap on /dev/hda5.  Priority:-1 extents:1 across:1477940k
[17179586.780000] EXT3 FS on hda1, internal journal
[17179586.932000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179586.932000] md: bitmap version 4.39
[17179587.444000] NET: Registered protocol family 17
[17179587.460000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179587.792000] cdrom: open failed.
[17179592.100000] ACPI: AC Adapter [ACAD] (on-line)
[17179592.120000] ACPI: Battery Slot [BAT1] (battery present)
[17179592.216000] ACPI: Power Button (FF) [PWRF]
[17179592.216000] ACPI: Lid Switch [LID]
[17179592.216000] ACPI: Power Button (CM) [PWRB]
[17179592.216000] ACPI: Sleep Button (CM) [SLPB]
[17179592.296000] ibm_acpi: ec object not found
[17179592.332000] pcc_acpi: loading...
[17179592.372000] wmi_add device=df40e000
[17179592.372000] calling WQBA
[17179592.432000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)[17179595.844000] [drm] Initialized drm 1.0.1 20051102
[17179595.900000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179595.900000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179595.904000] [drm] Initialized i915 1.5.0 20060119 on minor 0:
[17179596.344000] ppdev: user-space parallel port driver
[17179596.808000] apm: BIOS not found.
[17179600.064000] Bluetooth: Core ver 2.8
[17179600.064000] NET: Registered protocol family 31
[17179600.064000] Bluetooth: HCI device and connection manager initialized
[17179600.064000] Bluetooth: HCI socket layer initialized
[17179600.108000] Bluetooth: L2CAP ver 2.8
[17179600.108000] Bluetooth: L2CAP socket layer initialized
[17179600.128000] Bluetooth: RFCOMM socket layer initialized
[17179600.128000] Bluetooth: RFCOMM TTY layer initialized
[17179600.128000] Bluetooth: RFCOMM ver 1.7
[17179699.184000] NET: Registered protocol family 10
[17179699.184000] lo: Disabled Privacy Extensions
[17179699.184000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179699.184000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179699.184000] IPv6 over IPv4 tunneling driver
[17179712.360000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179712.420000] ieee80211_crypt: registered algorithm 'TKIP'
[17179730.892000] eth1: no IPv6 routers present

```

---

