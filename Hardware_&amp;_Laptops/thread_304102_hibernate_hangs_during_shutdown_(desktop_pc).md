---
title: "hibernate hangs during shutdown (desktop pc)"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by zardoz on 2006-11-21
Hy!

I have both Ubuntu and Kubuntu installed on my system (on different partitions). Both lockup during hibernate.
Kubuntu completely silent ... I select hibernate, the screen gets dark, the monitor goes in standby, the pc stays on forever without reacting to anything.
In Ubuntu when I select hibernate, I get several errors and then it also hangs.
Here are the error messages:
pnp: failed to activate device 00:09
ata1: failed to set xfer mode (err_mask=0x4)
Buffer I/O error on device sda4, logical block 2544109
^ this comes several time with different logical blocks
Aborting journal on device sda4
ext3_abort called
EXT3-fs error (device sda4)
ext3_journal_start_sb: Detected abortet journal
Remounting Filesystem read-only
and then again those Buffer I/O errors.

(I had to write those error messages down, cause I couldnt find that in any logfile under /var/log/ ... where are those logged?)

Here my system:
Mainboard: Gigabyte GA-965P-DS4 (Intel P965 Chipset)
CPU: Intel Core 2 Duo
Graphics: GeForce 7600 GT
Samsung HDD and DVD-Burner both on SATA
HDD in AHCI Mode

Under Windows XP hibernate works fine on that machine.
Hope someone can help me, cause I used to do a lot hibernating on my last pc.

Best regards,
zardoz

---

### Post by zardoz on 2006-11-21
ah, something I forgot to write ...
Kubuntu has those glx Nvidia drivers installed ... Ubuntu doesn't.
That prehaps explains the different lockup behavior.
But as stated above, also ubuntu without those drivers hangs up.

---

### Post by zardoz on 2006-11-21
bump

---

### Post by zardoz on 2006-11-22
anyone? perhaps some advices?

---

### Post by zgornel on 2006-11-22
Do you have a swap partition ? what's the output of *dmesg* ?

---

### Post by zardoz on 2006-11-22
Ok, I did a complete new install of Kubuntu on another partition. Here again is how it behaves on hibernate.
I select hibernate ... the screen gets black for about 10 seconds ... 
then all those error messages as stated in my first post are printed .. then nothing happens anymore.
But I can still change to other consoles ... when I change to the X console (Alt+Ctrl+F7) a login dialog appears (like the one, when you lock your screen). When I then insert my login data, I get the error message: "Cannot unlock the session because the authentification system failed to work; You must kill kdesktop_lock (pid 7284) manually."
Then I can change to another text login console (for example Alt+Ctrl+F1), but when I enter my username, I get the following error message: "EXT3-fs error (device sda4): ext3_get_inode_loc: unable to read inode block - inode = 359068, block = 720901"
The only thing to reboot is doing a hard reset.

My swap partition is ok:
swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda2                               partition       979956  0       -1

Here is the output of dmesg directly after reboot via hard reset (strange that nothing refers there, that I tried to hibernate):

```

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003eee0000 (usable)
[17179569.184000]  BIOS-e820: 000000003eee0000 - 000000003eee3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003eee3000 - 000000003eef0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003eef0000 - 000000003ef00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 110MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5910
[17179569.184000] On node 0 totalpages: 257760
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 28384 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f72e0
[17179569.184000] ACPI: RSDT (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x3eee3040
[17179569.184000] ACPI: FADT (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x3eee30c0
[17179569.184000] ACPI: MCFG (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x3eee7c80
[17179569.184000] ACPI: MADT (v001 GBT    GBTUACPI 0x42302e31 GBTU 0x01010101) @ 0x3eee7b80
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20040311) @ 0x3eee7d00
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20040311) @ 0x3eee8190
[17179569.184000] ACPI: DSDT (v001 GBT    GBTUACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:15 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 6:15 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3ef00000:b1100000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda4 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1866.980 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.132000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.132000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.148000] Memory: 1012416k/1031040k available (1910k kernel code, 17888k reserved, 1070k data, 308k init, 113536k highmem)
[17179570.148000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.228000] Calibrating delay using timer specific routine.. 3737.59 BogoMIPS (lpj=7475183)
[17179570.228000] Security Framework v1.0.0 initialized
[17179570.228000] SELinux:  Disabled at boot.
[17179570.228000] Mount-cache hash table entries: 512
[17179570.228000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179570.228000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179570.228000] monitor/mwait feature present.
[17179570.228000] using mwait in idle threads.
[17179570.228000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.228000] CPU: L2 cache: 2048K
[17179570.228000] CPU: Hyper-Threading is disabled
[17179570.228000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000140 0000e3bd 00000000 00000001
[17179570.228000] Checking 'hlt' instruction... OK.
[17179570.244000] SMP alternatives: switching to UP code
[17179570.244000] checking if image is initramfs... it is
[17179570.676000] Freeing initrd memory: 5213k freed
[17179570.676000] ACPI: Core revision 20060707
[17179570.680000] ACPI: Looking for DSDT ... not found!
[17179570.680000] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[17179570.680000] SMP alternatives: switching to SMP code
[17179570.680000] Booting processor 1/1 eip 3000
[17179570.692000] Initializing CPU#1
[17179570.772000] Calibrating delay using timer specific routine.. 3733.64 BogoMIPS (lpj=7467296)
[17179570.772000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179570.772000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179570.772000] monitor/mwait feature present.
[17179570.772000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.772000] CPU: L2 cache: 2048K
[17179570.772000] CPU: Hyper-Threading is disabled
[17179570.772000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000140 0000e3bd 00000000 00000001
[17179570.772000] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[17179570.772000] Total of 2 processors activated (7471.23 BogoMIPS).
[17179570.772000] ENABLING IO-APIC IRQs
[17179570.772000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.916000] checking TSC synchronization across 2 CPUs: passed.
[17179570.920000] Brought up 2 CPUs
[17179570.968000] migration_cost=4000
[17179570.968000] NET: Registered protocol family 16
[17179570.968000] EISA bus registered
[17179570.968000] ACPI: bus type pci registered
[17179570.968000] PCI: Using MMCONFIG
[17179570.968000] Setting up standard PCI resources
[17179570.968000] mtrr: your CPUs had inconsistent variable MTRR settings
[17179570.968000] mtrr: probably your BIOS does not setup all CPUs.
[17179570.968000] mtrr: corrected configuration.
[17179570.976000] ACPI: Interpreter enabled
[17179570.976000] ACPI: Using IOAPIC for interrupt routing
[17179570.976000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.976000] PCI: Probing PCI hardware (bus 00)
[17179570.976000] Boot video device is 0000:01:00.0
[17179570.980000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.980000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.988000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[17179570.988000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[17179570.988000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[17179570.992000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.992000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179570.992000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
[17179570.992000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179570.992000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
[17179570.992000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[17179570.996000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179570.996000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179570.996000] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[17179570.996000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.996000] pnp: PnP ACPI init
[17179570.996000] pnp: PnP ACPI: found 14 devices
[17179570.996000] PnPBIOS: Disabled by ACPI PNP
[17179570.996000] PCI: Using ACPI for IRQ routing
[17179570.996000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.996000] pnp: 00:0a: ioport range 0x400-0x4bf could not be reserved
[17179571.000000] PCI: Bridge: 0000:00:01.0
[17179571.000000]   IO window: a000-afff
[17179571.000000]   MEM window: f4000000-f6ffffff
[17179571.000000]   PREFETCH window: e0000000-efffffff
[17179571.000000] PCI: Bridge: 0000:00:1c.0
[17179571.000000]   IO window: 8000-8fff
[17179571.000000]   MEM window: disabled.
[17179571.000000]   PREFETCH window: disabled.
[17179571.000000] PCI: Bridge: 0000:00:1c.4
[17179571.000000]   IO window: b000-bfff
[17179571.000000]   MEM window: f7000000-f8ffffff
[17179571.000000]   PREFETCH window: 40000000-400fffff
[17179571.000000] PCI: Bridge: 0000:00:1c.5
[17179571.000000]   IO window: 9000-9fff
[17179571.000000]   MEM window: disabled.
[17179571.000000]   PREFETCH window: disabled.
[17179571.000000] PCI: Bridge: 0000:00:1e.0
[17179571.000000]   IO window: disabled.
[17179571.000000]   MEM window: f9000000-f90fffff
[17179571.000000]   PREFETCH window: disabled.
[17179571.000000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.000000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.000000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.000000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.000000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.000000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[17179571.000000] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 177
[17179571.000000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[17179571.000000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.000000] NET: Registered protocol family 2
[17179571.040000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.040000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179571.040000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179571.040000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.040000] TCP reno registered
[17179571.040000] audit: initializing netlink socket (disabled)
[17179571.040000] audit(1164232416.040:1): initialized
[17179571.040000] highmem bounce pool size: 64 pages
[17179571.040000] VFS: Disk quotas dquot_6.5.1
[17179571.040000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.040000] Initializing Cryptographic API
[17179571.040000] io scheduler noop registered
[17179571.040000] io scheduler anticipatory registered
[17179571.040000] io scheduler deadline registered
[17179571.040000] io scheduler cfq registered (default)
[17179571.040000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.040000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.040000] assign_interrupt_mode Found MSI capability
[17179571.040000] Allocate Port Service[0000:00:01.0:pcie00]
[17179571.040000] Allocate Port Service[0000:00:01.0:pcie03]
[17179571.040000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.040000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.040000] assign_interrupt_mode Found MSI capability
[17179571.040000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179571.040000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179571.040000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179571.040000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.040000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[17179571.040000] assign_interrupt_mode Found MSI capability
[17179571.040000] Allocate Port Service[0000:00:1c.4:pcie00]
[17179571.040000] Allocate Port Service[0000:00:1c.4:pcie02]
[17179571.040000] Allocate Port Service[0000:00:1c.4:pcie03]
[17179571.040000] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 177
[17179571.040000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[17179571.040000] assign_interrupt_mode Found MSI capability
[17179571.040000] Allocate Port Service[0000:00:1c.5:pcie00]
[17179571.040000] Allocate Port Service[0000:00:1c.5:pcie02]
[17179571.040000] Allocate Port Service[0000:00:1c.5:pcie03]
[17179571.040000] isapnp: Scanning for PnP cards...
[17179571.392000] isapnp: No Plug & Play device found
[17179571.412000] Real Time Clock Driver v1.12ac
[17179571.412000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.412000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.412000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.412000] mice: PS/2 mouse device common for all mice
[17179571.412000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.412000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.412000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.412000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179571.412000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.416000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.416000] EISA: Probing bus 0 at eisa.0
[17179571.416000] Cannot allocate resource for EISA slot 8
[17179571.416000] EISA: Detected 0 cards.
[17179571.416000] TCP bic registered
[17179571.416000] NET: Registered protocol family 1
[17179571.416000] NET: Registered protocol family 8
[17179571.416000] NET: Registered protocol family 20
[17179571.416000] Starting balanced_irq
[17179571.416000] Using IPI No-Shortcut mode
[17179571.416000] ACPI: (supports S0 S1 S4 S5)
[17179571.416000] Freeing unused kernel memory: 308k freed
[17179571.432000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.476000] Capability LSM initialized
[17179572.504000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179572.504000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[17179572.504000] ACPI: Processor [CPU1] (supports 2 throttling states)
[17179572.504000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179572.504000] ACPI: Getting cpuindex for acpiid 0x2
[17179572.504000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179572.504000] ACPI: Getting cpuindex for acpiid 0x3
[17179572.804000] SCSI subsystem initialized
[17179572.808000] libata version 1.20 loaded.
[17179572.808000] ahci 0000:00:1f.2: version 1.2
[17179572.808000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 225
[17179580.284000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179580.284000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[17179580.284000] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part 
[17179580.284000] ata1: SATA max UDMA/133 cmd 0xF8828100 ctl 0x0 bmdma 0x0 irq 233
[17179580.284000] ata2: SATA max UDMA/133 cmd 0xF8828180 ctl 0x0 bmdma 0x0 irq 233
[17179580.284000] ata3: SATA max UDMA/133 cmd 0xF8828200 ctl 0x0 bmdma 0x0 irq 233
[17179580.284000] ata4: SATA max UDMA/133 cmd 0xF8828280 ctl 0x0 bmdma 0x0 irq 233
[17179580.284000] ata5: SATA max UDMA/133 cmd 0xF8828300 ctl 0x0 bmdma 0x0 irq 233
[17179580.284000] ata6: SATA max UDMA/133 cmd 0xF8828380 ctl 0x0 bmdma 0x0 irq 233
[17179580.660000] ata1: SATA link up 3.0 Gbps (SStatus 123)
[17179580.660000] ata1: dev 0 cfg 49:2f00 82:746b 83:7f01 84:4023 85:7469 86:be01 87:4023 88:40ff
[17179580.660000] ata1: dev 0 ATA-7, max UDMA7, 488395055 sectors: LBA48
[17179580.700000] ata1: dev 0 configured for UDMA/133
[17179580.700000] scsi0 : ahci
[17179581.076000] ata2: SATA link up 1.5 Gbps (SStatus 113)
[17179581.236000] ata2: dev 0 cfg 49:0f00 82:0000 83:4000 84:4000 85:0000 86:0000 87:4000 88:0407
[17179581.236000] ata2: dev 0 ATAPI, max UDMA/33
[17179581.396000] ata2: dev 0 configured for UDMA/33
[17179581.396000] scsi1 : ahci
[17179582.312000] ata3: SATA link down (SStatus 0)
[17179582.312000] scsi2 : ahci
[17179583.232000] ata4: SATA link down (SStatus 0)
[17179583.232000] scsi3 : ahci
[17179584.148000] ata5: SATA link down (SStatus 0)
[17179584.148000] scsi4 : ahci
[17179585.068000] ata6: SATA link down (SStatus 0)
[17179585.068000] scsi5 : ahci
[17179585.068000]   Vendor: ATA       Model: SAMSUNG SP2504C   Rev: VT10
[17179585.068000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179585.068000]   Vendor: TSSTcorp  Model: CD/DVDW SH-S183A  Rev: SB00
[17179585.068000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179585.076000] SCSI device sda: 488395055 512-byte hdwr sectors (250058 MB)
[17179585.076000] sda: Write Protect is off
[17179585.076000] sda: Mode Sense: 00 3a 00 00
[17179585.076000] SCSI device sda: drive cache: write back
[17179585.076000] SCSI device sda: 488395055 512-byte hdwr sectors (250058 MB)
[17179585.076000] sda: Write Protect is off
[17179585.076000] sda: Mode Sense: 00 3a 00 00
[17179585.076000] SCSI device sda: drive cache: write back
[17179585.076000]  sda: sda1 sda2 sda3 sda4
[17179585.100000] sd 0:0:0:0: Attached scsi disk sda
[17179585.416000] Probing IDE interface ide0...
[17179585.436000] usbcore: registered new driver usbfs
[17179585.436000] usbcore: registered new driver hub
[17179585.436000] USB Universal Host Controller Interface driver v3.0
[17179585.436000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179585.436000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[17179585.436000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[17179585.436000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[17179585.436000] uhci_hcd 0000:00:1a.0: irq 169, io base 0x0000c400
[17179585.436000] usb usb1: configuration #1 chosen from 1 choice
[17179585.436000] hub 1-0:1.0: USB hub found
[17179585.436000] hub 1-0:1.0: 2 ports detected
[17179585.464000] ieee1394: Initialized config rom entry `ip1394'
[17179585.544000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 50
[17179585.544000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[17179585.544000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[17179585.544000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[17179585.544000] uhci_hcd 0000:00:1a.1: irq 50, io base 0x0000c000
[17179585.544000] usb usb2: configuration #1 chosen from 1 choice
[17179585.544000] hub 2-0:1.0: USB hub found
[17179585.544000] hub 2-0:1.0: 2 ports detected
[17179585.648000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 58
[17179585.648000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179585.648000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179585.648000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[17179585.648000] uhci_hcd 0000:00:1d.0: irq 58, io base 0x0000c800
[17179585.648000] usb usb3: configuration #1 chosen from 1 choice
[17179585.648000] hub 3-0:1.0: USB hub found
[17179585.648000] hub 3-0:1.0: 2 ports detected
[17179585.752000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 225
[17179585.752000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179585.752000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179585.752000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[17179585.752000] uhci_hcd 0000:00:1d.1: irq 225, io base 0x0000cc00
[17179585.752000] usb usb4: configuration #1 chosen from 1 choice
[17179585.752000] hub 4-0:1.0: USB hub found
[17179585.752000] hub 4-0:1.0: 2 ports detected
[17179585.784000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179585.856000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 66
[17179585.856000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179585.856000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179585.856000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[17179585.856000] uhci_hcd 0000:00:1d.2: irq 66, io base 0x0000d000
[17179585.856000] usb usb5: configuration #1 chosen from 1 choice
[17179585.856000] hub 5-0:1.0: USB hub found
[17179585.856000] hub 5-0:1.0: 2 ports detected
[17179585.960000] usb 1-1: configuration #1 chosen from 1 choice
[17179585.964000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 66
[17179585.964000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[17179585.964000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[17179585.964000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[17179585.964000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[17179585.964000] ehci_hcd 0000:00:1a.7: irq 66, io mem 0xf9104000
[17179585.968000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179585.968000] usb usb6: configuration #1 chosen from 1 choice
[17179585.968000] hub 6-0:1.0: USB hub found
[17179585.968000] hub 6-0:1.0: 4 ports detected
[17179585.980000] Probing IDE interface ide1...
[17179586.072000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 58
[17179586.072000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179586.072000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179586.072000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[17179586.072000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179586.072000] ehci_hcd 0000:00:1d.7: irq 58, io mem 0xf9105000
[17179586.076000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179586.076000] usb usb7: configuration #1 chosen from 1 choice
[17179586.076000] hub 7-0:1.0: USB hub found
[17179586.076000] hub 7-0:1.0: 6 ports detected
[17179586.120000] usb 1-1: USB disconnect, address 2
[17179586.248000] ACPI: PCI Interrupt 0000:05:06.0[A] -> GSI 18 (level, low) -> IRQ 66
[17179586.296000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[66]  MMIO=[f9004000-f90047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179586.616000] usbcore: registered new driver libusual
[17179586.668000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179586.668000] EXT3-fs: write access will be enabled during recovery.
[17179586.856000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17179587.028000] usb 1-1: configuration #1 chosen from 1 choice
[17179587.036000] Initializing USB Mass Storage driver...
[17179587.272000] usb 1-2: new low speed USB device using uhci_hcd and address 4
[17179587.452000] usb 1-2: configuration #1 chosen from 1 choice
[17179587.456000] scsi6 : SCSI emulation for USB Mass Storage devices
[17179587.456000] usb-storage: device found at 3
[17179587.456000] usb-storage: waiting for device to settle before scanning
[17179587.456000] usbcore: registered new driver usb-storage
[17179587.456000] USB Mass Storage support registered.
[17179587.460000] usbcore: registered new driver hiddev
[17179587.476000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
[17179587.476000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.0-2
[17179587.476000] usbcore: registered new driver usbhid
[17179587.476000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179587.572000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0016e60000b94ffd]
[17179589.984000] kjournald starting.  Commit interval 5 seconds
[17179589.984000] EXT3-fs: sda4: orphan cleanup on readonly fs
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403537
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403546
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403545
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403544
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403540
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403569
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403567
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403568
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403566
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403563
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403560
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403542
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403578
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403577
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403576
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403574
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403573
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403572
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403571
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403565
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403564
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403562
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403561
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403559
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403543
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403549
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403550
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 1403558
[17179589.984000] ext3_orphan_cleanup: deleting unreferenced inode 310410
[17179589.984000] EXT3-fs: sda4: 29 orphan inodes deleted
[17179589.984000] EXT3-fs: recovery complete.
[17179589.992000] EXT3-fs: mounted filesystem with ordered data mode.
[17179592.460000] usb-storage: device scan complete
[17179592.468000]   Vendor: Brother   Model: DCP-115C          Rev: 1.00
[17179592.468000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179592.532000] sd 6:0:0:0: Attached scsi removable disk sdb
[17179596.772000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179596.776000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179596.828000] hw_random hardware driver 1.0.0 loaded
[17179596.832000] input: PC Speaker as /class/input/input2
[17179596.864000] Linux agpgart interface v0.101 (c) Dave Jones
[17179596.888000] agpgart: Detected an Intel 965G Chipset.
[17179596.900000] agpgart: AGP aperture is 256M @ 0x0
[17179597.064000] Floppy drive(s): fd0 is 1.44M
[17179597.080000] parport: PnPBIOS parport detected.
[17179597.080000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179597.084000] FDC 0 is a post-1991 82077
[17179597.096000] Linux video capture interface: v1.00
[17179597.328000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179597.328000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179597.328000] sky2 v1.6.1 addr 0xf8000000 irq 169 Yukon-EC (0xb6) rev 2
[17179597.328000] sky2 eth0: addr 00:16:e6:84:88:4c
[17179597.544000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x018C
[17179597.544000] usbcore: registered new driver usblp
[17179597.544000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179597.568000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 82
[17179597.568000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179597.604000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179597.604000]  1:0:0:0: Attached scsi generic sg1 type 5
[17179597.604000] sd 6:0:0:0: Attached scsi generic sg2 type 0
[17179597.676000] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[17179597.676000] Uniform CD-ROM driver Revision: 3.20
[17179597.676000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179597.688000] ts: Compaq touchscreen protocol output
[17179597.712000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179597.956000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[17179598.200000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 90
[17179598.200000] saa7134[0]: found at 0000:05:00.0, rev: 1, irq: 90, latency: 32, mmio: 0xf9005000
[17179598.200000] saa7134[0]: subsystem: 153b:1142, board: Terratec Cinergy 400 TV [card=8,autodetected]
[17179598.200000] saa7134[0]: board init: gpio is 50000
[17179598.200000] input: saa7134 IR (Terratec Cinergy 40 as /class/input/input3
[17179598.208000] sky2 eth0: enabling interface
[17179598.344000] saa7134[0]: i2c eeprom 00: 3b 15 42 11 ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.344000] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.344000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.344000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.344000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.344000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.344000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.344000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.388000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179598.388000] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[17179598.388000] tuner 0-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[17179598.392000] saa7134[0]: registered device video0 [v4l2]
[17179598.392000] saa7134[0]: registered device vbi0
[17179598.400000] saa7134 ALSA driver for DMA sound loaded
[17179598.400000] saa7134[0]/alsa: saa7134[0] at 0xf9005000 irq 90 registered as card -1
[17179598.580000] lp0: using parport0 (interrupt-driven).
[17179598.600000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179598.600000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179598.624000] Adding 979956k swap on /dev/disk/by-uuid/adfce31a-69ae-4903-8067-8b0579c24821.  Priority:-1 extents:1 across:979956k
[17179598.712000] EXT3 FS on sda4, internal journal
[17179598.888000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179598.948000] NTFS volume version 3.1.
[17179598.948000] kjournald starting.  Commit interval 5 seconds
[17179598.960000] EXT3 FS on sda3, internal journal
[17179598.960000] EXT3-fs: mounted filesystem with ordered data mode.
[17179599.532000] ACPI: Power Button (FF) [PWRF]
[17179599.532000] ACPI: Power Button (CM) [PWRB]
[17179599.616000] ibm_acpi: ec object not found
[17179599.656000] pcc_acpi: loading...
[17179599.912000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[17179599.936000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179599.936000] acpi-cpufreq: CPU1 - ACPI performance management activated.
[17179600.500000] NET: Registered protocol family 10
[17179600.500000] lo: Disabled Privacy Extensions
[17179600.500000] IPv6 over IPv4 tunneling driver
[17179600.988000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179600.988000] apm: disabled - APM is not SMP safe.
[17179605.236000] Bluetooth: Core ver 2.8
[17179605.236000] NET: Registered protocol family 31
[17179605.236000] Bluetooth: HCI device and connection manager initialized
[17179605.236000] Bluetooth: HCI socket layer initialized
[17179605.444000] Bluetooth: L2CAP ver 2.8
[17179605.444000] Bluetooth: L2CAP socket layer initialized
[17179605.460000] Bluetooth: RFCOMM socket layer initialized
[17179605.460000] Bluetooth: RFCOMM TTY layer initialized
[17179605.460000] Bluetooth: RFCOMM ver 1.7
[17179610.952000] eth0: no IPv6 routers present

```

---

### Post by zardoz on 2006-11-23
bump

---

### Post by zardoz on 2006-11-24
bump

---

### Post by zgornel on 2006-11-24
Try the hibernate script. (*$sudo apt-get install hibernate* and then *$sudo hibernate*)

---

### Post by zardoz on 2006-11-25
Also didn't work with hibernate package.

But I located the problem. It's cause I use AHCI mode for Serial ATA. When I switch to Ide mode (in BIOS), hibernate works. Thats why every error message above has to do sthg with the filesystem.
Now the question is ... is it a general bug with AHCI mode + hibernate, or does it only affect this chipset.

---

### Post by zgornel on 2006-11-26
It is probably because the chipset is new. I think i965 uses the new ICH7 southbridge and support for it was added in 2.6.18 kern.

---

