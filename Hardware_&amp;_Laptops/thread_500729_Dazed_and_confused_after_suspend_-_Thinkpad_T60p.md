---
title: "Dazed and confused after suspend - Thinkpad T60p"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by bernt.ribbum on 2007-07-14
Hi gurus!

I'm getting these messages after resuming from a suspend on my Lenovo T60p (running 7.04 Feisty Fawn):

***
Message from syslogd@**** at Sat Jul 14 08:49:14 2007 ...
**** kernel: [68477.548000] Uhhuh. NMI received for unknown reason b0 on CPU 0.

Message from syslogd@**** at Sat Jul 14 08:49:14 2007 ...
**** kernel: [68477.548000] You have some hardware problem, likely on the PCI bus.

Message from syslogd@**** at Sat Jul 14 08:49:14 2007 ...
**** kernel: [68477.548000] Dazed and confused, but trying to continue
***

Anybody who have seen a similar thing? Everything seems to work as it should (although I've had the sound system being mute a few times). As far as I can tell this seems to be quite harmless, but I'd like to know what causes it. 

Anyone?

- Bernt

---

### Post by jbinto on 2007-07-16
I saw this for the first time and only time this morning. I've successfully suspended this Thinkpad T60 (Intel graphics) many times on Feisty and I've never seen anything like this. I am still booted into this 'dazed and confused' state and it's interesting to say the least.

Sequence of events:

1. Laptop is on the entire weekend, but I sleep it every night. 
2. This morning, I sleep the laptop to go to school.
3. I start the laptop at school, running Windows XP inside VMWare works perfectly for 2.5 hours (battery usually lasts 5 hours), as it always has.
4. Suddenly, my wireless network dies and scanning doesn't work. I have lots of trouble with my ar5418 Atheros card and have to use an svn madwifi, so I assume this is a not-so-serious driver issue. Continue without wireless network for next hour.
5. While working away without wireless, my Windows XP guest session shows some weird symptoms. No blue screen of death, but what I assume is memory corruption all over the place, programs terminating for no good reason, with "access violation" errors. In WinXP event viewer, I see these failures, but nothing like it since the VM has been created.
6. Warm-reboot VM (Start->Shut Down->Restart), same symptoms. 
7. Decide to pack it in, when I notice a message from syslog on all of my terminals:

```

Message from syslogd@blackbox at Mon Jul 16 11:45:05 2007 ...
blackbox kernel: [221515.800000] Uhhuh. NMI received for unknown reason b0 on CPU 0.

Message from syslogd@blackbox at Mon Jul 16 11:45:05 2007 ...
blackbox kernel: [221515.800000] You have some hardware problem, likely on the PCI bus.

Message from syslogd@blackbox at Mon Jul 16 11:45:05 2007 ...
blackbox kernel: [221515.800000] Dazed and confused, but trying to continue

```

I do a dmesg, and am flooded with:

```

[224588.688000] wifi0: rx FIFO overrun; resetting
[224591.060000] wifi0: rx FIFO overrun; resetting
[224593.612000] wifi0: rx FIFO overrun; resetting
[224595.728000] wifi0: rx FIFO overrun; resetting
[224598.384000] wifi0: rx FIFO overrun; resetting
[224600.320000] wifi0: rx FIFO overrun; resetting
[224601.848000] wifi0: rx FIFO overrun; resetting
[224603.812000] wifi0: rx FIFO overrun; resetting
[224606.468000] wifi0: rx FIFO overrun; resetting

```

Piping it through less, I get the same info:

```

[221515.800000] Uhhuh. NMI received for unknown reason b0 on CPU 0.
[221515.800000] You have some hardware problem, likely on the PCI bus.
[221515.800000] Dazed and confused, but trying to continue
[221516.820000] wifi0: rx FIFO overrun; resetting
[221517.620000] wifi0: rx FIFO overrun; resetting
[221518.648000] wifi0: rx FIFO overrun; resetting

```

The wifi died at the same time the "dazed and confused" happened.

Hundreds of the overrun lines, and one more interesting tidbit, which may be unrelated because I don't read 'dmesg' on this box very often, so I don't know if this happens always:

```

[224060.416000] ata1.00: exception Emask 0x2 SAct 0x7ffffff3 SErr 0x0 action 0x2 frozen
[224060.416000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x7ffffff3 FIS=005040a1:00000008)
[224060.416000] ata1.00: cmd 61/08:00:6e:65:6a/00:00:0c:00:00/40 tag 0 cdb 0x0 data 4096 out
[224060.416000]          res 50/00:08:36:cc:6a/00:00:0c:00:00/40 Emask 0x2 (HSM violation)
[224060.416000] ata1.00: cmd 61/08:08:36:cc:6a/00:00:0c:00:00/40 tag 1 cdb 0x0 data 4096 out
[224060.416000]          res 50/00:08:36:cc:6a/00:00:0c:00:00/40 Emask 0x2 (HSM violation)
[224060.416000] ata1.00: cmd 61/08:20:ee:eb:46/00:00:0c:00:00/40 tag 4 cdb 0x0 data 4096 out
[224060.416000]          res 50/00:08:36:cc:6a/00:00:0c:00:00/40 Emask 0x2 (HSM violation)
[224060.416000] ata1.00: cmd 61/08:28:ae:fd:46/00:00:0c:00:00/40 tag 5 cdb 0x0 data 4096 out
[224060.416000]          res 50/00:08:36:cc:6a/00:00:0c:00:00/40 Emask 0x2 (HSM violation)
[224060.416000] ata1.00: cmd 61/08:30:c6:9d:47/00:00:0c:00:00/40 tag 6 cdb 0x0 data 4096 out

```

..followed by a couple dozen more HSM violations.

I meant to shut down the laptop, but suspended it out of habit. When arriving home I turned it on and to my surprise NetworkManager connected to my home wireless network. Apparently the suspend/resume process unloaded the modules and that was enough to fix wireless. I'm scared to try the VM again in this state so I will reboot now. I don't expect to get this ever again considering how stable this laptop has been even while running VMWare, but we'll see. 

To the OP:

Do you experience this often, and are there any symptoms? I should note that *to the best of my knowledge* everything in Linux worked fine except the wireless card, and I would probably have never noticed if the VM didn't start misbehaving.

I will do some research on this issue and post my findings back. In the meantime, anyone know if this is on Launchpad as a bug?

---

### Post by bernt.ribbum on 2007-07-17
My laptop is ALWAYS dazed and confused after a suspend. Otherwise I have found no other symptoms. I'll have a closer look at the log files and see if I can find anything worth noting.

-  Bernt

---

### Post by bernt.ribbum on 2007-07-17
A quick dmesg scan reveals nothing that I can point at as a troublemaker... Everything looks like it is resumed properly.

These messages (from cold boot) are maybe interesting though:

[   25.472000] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   25.472000] vboxdrv: Successfully done.

I'm some times running XP in VirtualBox, and it works surprisingly well - I don't know what the watchdog is supposed to be doing, but at least it is NMI related..!

- Bernt

---

### Post by bernt.ribbum on 2007-07-17
Hmmm... Disabling VirtualBox did nothing.

I can attach the dmesg output if you like - just tell me :-)

- Bernt

---

### Post by What is in a name? on 2007-07-29
Hi there.

I'm running Ubuntu on dual-boot with Windows XP on my Samsung NP-R50 laptop, Intel Centrino 1,73Ghz, 512 MB (well, right now my Ubuntu says I have 502 MB, go figure), 48 GB of harddisk, ATI Mobility Radeon X300. I've been observing the same problem you mentioned since yesterday. The last events before my PC complained about being "dazed and confused" were some tweaks to my xorg.conf and the installation of Beryl, Kiba-dock and AWN (these last two from third-party repos), for I was trying to see which one worked best. Right now I'm with AWN, but what's important is that the Update Manager started to mention there were some updates to Compiz which I was not able to do, at least not integrally. After a partial update which did not come to its end, Synaptic reported I could not install nor remove any program further on, which was solved after I typed "sudo apt-get install -f" in a terminal. Synaptic was not corrupted anymore, but the newer updates of Compiz got installed too. Anyway, I did not worry about it. Later on I had to do a force reboot after a crash (Beryl, you know), and on the reboot I had that message you reported. I only got to understand what was written after several crashes, because the message disappeared in a fraction of seconds and I only could read parts of it each time.

Right now I did some more tinkerings and, though I did not save my dmesg from one of the previous problematic boots, I'm attaching the dmesg of the current session, which booted with no errors, and my current xorg.conf too.

I still don't think this is a real hardware issue. In my opinion (which is useless in actually solving the problem, but anyway I don't have enough knowledge to do so entirely on my own), the answer might be or on the xorg.conf configuration, or on a corrupted file, or on some conflict between libraries (BTW, I uninstalled the newer Compiz and reinstalled the version that comes with Feisty, after deactivating the third-party repos, but that did not solve the issue right away). This annoys me, since it is almost like a hit or a miss. I can also confirm it did not present that error message after the first today's boot, better said, after the PC was off for some hours. The error repeated itself again later and now it does not appear anymore after I made some changes in my current configuration. Thus the attachments.

P.S.: I just had a crash while I was writing this post. and after that my PC rebooted again (with Ctrl+Alt+Sys+[...]B) and the error message appeared again. So, I ran dmesg again and I'm attaching it too. Then I had another crash, which I could only solve with a forced reboot, and this time it didn't present any problem. And since the forums have limits even for the size of .TXT files, here it goes:

Clean boot DMESG:

> [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000008000 end: 00000000000d8000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fda0000 end: 000000001fea0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fea0000 size: 0000000000011000 end: 000000001feb1000 type: 3
[    0.000000] copy_e820_map() start: 000000001feb1000 size: 000000000004f000 end: 000000001ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010006000 end: 00000000f0006000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0008000 size: 0000000000004000 end: 00000000f000c000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000070000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fea0000 (usable)
[    0.000000]  BIOS-e820: 000000001fea0000 - 000000001feb1000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feb1000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130720) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130720
[    0.000000]   HighMem    130720 ->   130720
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130720
[    0.000000] On node 0 totalpages: 130720
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125635 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7860
[    0.000000] ACPI: RSDT (v001 PTLTD  Ohlone00 0x06040000  LTP 0x00000000) @ 0x1feabecf
[    0.000000] ACPI: FADT (v001 SEC    MAGIC    0x06040000 PTL  0x0000005f) @ 0x1feb0e88
[    0.000000] ACPI: MADT (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1feb0efc
[    0.000000] ACPI: HPET (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1feb0f64
[    0.000000] ACPI: MCFG (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1feb0f9c
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1feb0fd8
[    0.000000] ACPI: SSDT (v001 SataRe SataAhci 0x00001000 INTL 0x20030224) @ 0x1feac6f5
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x1feac1ca
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x1feabfe0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x1feabf17
[    0.000000] ACPI: DSDT (v001    SEC    MAGIC 0x06040000 INTL 0x20030224) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Detected 1729.111 MHz processor.
[    5.697352] Built 1 zonelists.  Total pages: 129699
[    5.697356] Kernel command line: root=UUID=ffeee1af-68e1-44ad-8ec5-80d725c2b0c1 ro quiet splash
[    5.697513] mapped APIC to ffffd000 (fee00000)
[    5.697515] mapped IOAPIC to ffffc000 (fec00000)
[    5.697519] Enabling fast FPU save and restore... done.
[    5.697521] Enabling unmasked SIMD FPU exception support... done.
[    5.697529] Initializing CPU#0
[    5.697599] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    5.698736] Console: colour VGA+ 80x25
[    5.698904] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    5.699102] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    5.712270] Memory: 507320k/522880k available (1992k kernel code, 14964k reserved, 900k data, 328k init, 0k highmem)
[    5.712280] virtual kernel memory layout:
[    5.712281]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    5.712282]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    5.712283]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    5.712284]     lowmem  : 0xc0000000 - 0xdfea0000   ( 510 MB)
[    5.712286]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    5.712287]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    5.712288]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    5.712292] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    5.712436] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    5.712441] hpet0: 3 64-bit timers, 14318180 Hz
[    5.713447] Using HPET for base-timer
[    5.792406] Calibrating delay using timer specific routine.. 3461.50 BogoMIPS (lpj=6923006)
[    5.792445] Security Framework v1.0.0 initialized
[    5.792452] SELinux:  Disabled at boot.
[    5.792466] Mount-cache hash table entries: 512
[    5.792593] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[    5.792604] CPU: L1 I cache: 32K, L1 D cache: 32K
[    5.792606] CPU: L2 cache: 2048K
[    5.792609] CPU: After all inits, caps: afe9fbff 00000000 00000000 00002040 00000180 00000000 00000000
[    5.792618] Compat vDSO mapped to ffffe000.
[    5.792621] Remapping vsyscall page to ffffe000
[    5.792632] Checking 'hlt' instruction... OK.
[    5.808484] SMP alternatives: switching to UP code
[    5.808645] Freeing SMP alternatives: 11k freed
[    5.808809] Early unpacking initramfs... done
[    6.132295] ACPI: Core revision 20060707
[    6.132643] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    6.136151] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    6.136173] Total of 1 processors activated (3461.50 BogoMIPS).
[    6.136380] ENABLING IO-APIC IRQs
[    6.136573] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    6.284231] Brought up 1 CPUs
[    6.284453] Booting paravirtualized kernel on bare hardware
[    6.284528] Time: 13:46:25  Date: 06/29/107
[    6.284553] NET: Registered protocol family 16
[    6.284625] EISA bus registered
[    6.284629] ACPI: bus type pci registered
[    6.284966] PCI: PCI BIOS revision 2.10 entry at 0xfd91e, last bus=6
[    6.284968] PCI: Using configuration type 1
[    6.284970] Setting up standard PCI resources
[    6.296045] ACPI: Interpreter enabled
[    6.296047] ACPI: Using IOAPIC for interrupt routing
[    6.297781] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    6.297789] PCI: Probing PCI hardware (bus 00)
[    6.299570] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    6.299575] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    6.299764] Boot video device is 0000:01:00.0
[    6.300410] PCI: Transparent bridge - 0000:00:1e.0
[    6.300469] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#06) (try 'pci=assign-busses')
[    6.300472] Please report the result to linux-kernel to fix this permanently
[    6.300513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    6.306376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    6.307127] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    6.307747] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    6.308543] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 6 *10 11)
[    6.308755] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 6 10 *11)
[    6.308966] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 10 *11)
[    6.309174] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 *10 11)
[    6.309382] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 6 *10 11)
[    6.309589] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 6 10 11) *0, disabled.
[    6.309804] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 6 10 *11)
[    6.310012] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 6 10 11)
[    6.311098] ACPI: Power Resource [CFAN] (on)
[    6.311189] Linux Plug and Play Support v0.97 (c) Adam Belay
[    6.311196] pnp: PnP ACPI init
[    6.313094] pnp: PnP ACPI: found 10 devices
[    6.313098] PnPBIOS: Disabled by ACPI PNP
[    6.313131] PCI: Using ACPI for IRQ routing
[    6.313134] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    6.332487] NET: Registered protocol family 8
[    6.332489] NET: Registered protocol family 20
[    6.332831] PCI: Bridge: 0000:00:01.0
[    6.332834]   IO window: 3000-3fff
[    6.332838]   MEM window: c0100000-c01fffff
[    6.332841]   PREFETCH window: d0000000-d7ffffff
[    6.332844] PCI: Bridge: 0000:00:1c.0
[    6.332847]   IO window: 4000-4fff
[    6.332853]   MEM window: c4000000-c7ffffff
[    6.332857]   PREFETCH window: d8000000-dbffffff
[    6.332869] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[    6.332871]   IO window: 00005000-000050ff
[    6.332875]   IO window: 00005400-000054ff
[    6.332880]   PREFETCH window: 30000000-33ffffff
[    6.332885]   MEM window: 34000000-37ffffff
[    6.332889] PCI: Bridge: 0000:00:1e.0
[    6.332892]   IO window: 5000-5fff
[    6.332898]   MEM window: c8000000-c80fffff
[    6.332903]   PREFETCH window: 30000000-33ffffff
[    6.332918] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    6.332923] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    6.332943] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    6.332949] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    6.332962] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    6.333014] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[    6.333038] NET: Registered protocol family 2
[    6.364211] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    6.364277] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    6.364370] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    6.364418] TCP: Hash tables configured (established 16384 bind 8192)
[    6.364420] TCP reno registered
[    6.376252] checking if image is initramfs... it is
[    7.008585] Freeing initrd memory: 6768k freed
[    7.008803] Simple Boot Flag at 0x36 set to 0x1
[    7.009025] audit: initializing netlink socket (disabled)
[    7.009039] audit(1185716785.380:1): initialized
[    7.009159] VFS: Disk quotas dquot_6.5.1
[    7.009178] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    7.009224] io scheduler noop registered
[    7.009227] io scheduler anticipatory registered
[    7.009229] io scheduler deadline registered
[    7.009239] io scheduler cfq registered (default)
[    7.009504] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    7.009532] assign_interrupt_mode Found MSI capability
[    7.009535] Allocate Port Service[0000:00:01.0:pcie00]
[    7.009606] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    7.009657] assign_interrupt_mode Found MSI capability
[    7.009660] Allocate Port Service[0000:00:1c.0:pcie00]
[    7.009688] Allocate Port Service[0000:00:1c.0:pcie02]
[    7.009847] isapnp: Scanning for PnP cards...
[    7.363764] isapnp: No Plug & Play device found
[    7.386245] Real Time Clock Driver v1.12ac
[    7.386456] hpet_resources: 0xfed00000 is busy
[    7.386471] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    7.387109] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 18
[    7.387117] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[    7.387191] mice: PS/2 mouse device common for all mice
[    7.387688] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    7.387968] input: Macintosh mouse button emulation as /class/input/input0
[    7.388000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    7.388004] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    7.388226] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    7.391091] i8042.c: Detected active multiplexing controller, rev 1.1.
[    7.392508] serio: i8042 KBD port at 0x60,0x64 irq 1
[    7.392511] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    7.392514] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    7.392516] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    7.392519] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    7.392628] EISA: Probing bus 0 at eisa.0
[    7.392636] Cannot allocate resource for EISA slot 1
[    7.392639] Cannot allocate resource for EISA slot 2
[    7.392641] Cannot allocate resource for EISA slot 3
[    7.392643] Cannot allocate resource for EISA slot 4
[    7.392646] Cannot allocate resource for EISA slot 5
[    7.392659] EISA: Detected 0 cards.
[    7.422743] TCP cubic registered
[    7.422752] NET: Registered protocol family 1
[    7.422772] Using IPI No-Shortcut mode
[    7.422829] ACPI: (supports S0 S3 S4 S5)
[    7.422875]   Magic number: 15:798:787
[    7.422877]   hash matches drivers/base/power/resume.c:46
[    7.422964]   hash matches device ptyq9
[    7.423149] Freeing unused kernel memory: 328k freed
[    7.423730] Time: tsc clocksource has been installed.
[    7.437010] input: AT Translated Set 2 keyboard as /class/input/input1
[    8.620097] Capability LSM initialized
[    8.647446] ACPI: Fan [FAN1] (on)
[    8.650903] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    8.650908] ACPI: Processor [CPU0] (supports 2 throttling states)
[    8.652126] ACPI: Thermal Zone [THRM] (52 C)
[    8.945415] usbcore: registered new interface driver usbfs
[    8.945437] usbcore: registered new interface driver hub
[    8.945455] usbcore: registered new device driver usb
[    8.946219] USB Universal Host Controller Interface driver v3.0
[    8.946267] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    8.946277] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    8.946281] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    8.946429] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    8.946460] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001800
[    8.946551] usb usb1: configuration #1 chosen from 1 choice
[    8.946572] hub 1-0:1.0: USB hub found
[    8.946576] hub 1-0:1.0: 2 ports detected
[    9.029058] SCSI subsystem initialized
[    9.034020] libata version 2.20 loaded.
[    9.047214] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    9.047226] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    9.047231] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    9.047251] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    9.047285] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001820
[    9.047369] usb usb2: configuration #1 chosen from 1 choice
[    9.047391] hub 2-0:1.0: USB hub found
[    9.047396] hub 2-0:1.0: 2 ports detected
[    9.073655] ieee1394: Initialized config rom entry `ip1394'
[    9.151154] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[    9.151167] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    9.151172] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    9.151192] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    9.151224] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001840
[    9.151306] usb usb3: configuration #1 chosen from 1 choice
[    9.151330] hub 3-0:1.0: USB hub found
[    9.151335] hub 3-0:1.0: 2 ports detected
[    9.255098] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    9.255110] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    9.255115] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    9.255135] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    9.255167] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    9.255255] usb usb4: configuration #1 chosen from 1 choice
[    9.255277] hub 4-0:1.0: USB hub found
[    9.255282] hub 4-0:1.0: 2 ports detected
[    3.452000] Time: hpet clocksource has been installed.
[    3.548000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.548000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.548000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.548000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.548000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.548000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.548000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xc0000000
[    3.552000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.552000] usb usb5: configuration #1 chosen from 1 choice
[    3.552000] hub 5-0:1.0: USB hub found
[    3.552000] hub 5-0:1.0: 8 ports detected
[    3.656000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.656000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[    3.656000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.656000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118c0 irq 14
[    3.656000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118c8 irq 15
[    3.656000] scsi0 : ata_piix
[    3.984000] ata1.00: ata_hpa_resize 1: sectors = 102022014, hpa_sectors = 117210240
[    3.984000] ata1.00: Host Protected Area detected.
[    3.984000]      current size : 102022014 sectors (52235 MB)
[    3.984000]      native  size : 117210240 sectors (60011 MB)
[    3.984000] ata1.00: SET of native returned 0, expected 117210240
[    3.984000] ata1.00: ATA-6: HTS541060G9AT00, MB3OA60A, max UDMA/100
[    3.984000] ata1.00: 102022014 sectors, multi 16: LBA48 
[    3.984000] ata1.01: ATAPI, max UDMA/33
[    3.992000] ata1.00: ata_hpa_resize 1: sectors = 102022014, hpa_sectors = 117210240
[    3.992000] ata1.00: Host Protected Area detected.
[    3.992000]      current size : 102022014 sectors (52235 MB)
[    3.992000]      native  size : 117210240 sectors (60011 MB)
[    3.992000] ata1.00: SET of native returned 0, expected 117210240
[    3.992000] ata1.00: configured for UDMA/100
[    4.156000] ata1.01: configured for UDMA/33
[    4.156000] scsi1 : ata_piix
[    4.156000] ata2: port disabled. ignoring.
[    4.156000] scsi 0:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3O PQ: 0 ANSI: 5
[    4.156000] scsi 0:0:1:0: CD-ROM            TEAC     DV-W28EA         S.0A PQ: 0 ANSI: 5
[    4.160000] b44.c:v1.01 (Jun 16, 2006)
[    4.160000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 22 (level, low) -> IRQ 22
[    4.164000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:00:f0:7c:b0:c8
[    4.164000] ACPI: PCI Interrupt 0000:06:09.1[B] -> GSI 17 (level, low) -> IRQ 17
[    4.216000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[c8001000-c80017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.252000] SCSI device sda: 102022014 512-byte hdwr sectors (52235 MB)
[    4.264000] sda: Write Protect is off
[    4.264000] sda: Mode Sense: 00 3a 00 00
[    4.284000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.284000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.284000] Uniform CD-ROM driver Revision: 3.20
[    4.284000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    4.288000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.288000] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    4.292000] SCSI device sda: 102022014 512-byte hdwr sectors (52235 MB)
[    4.292000] sda: Write Protect is off
[    4.292000] sda: Mode Sense: 00 3a 00 00
[    4.316000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.316000]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    4.388000] sd 0:0:0:0: Attached scsi disk sda
[    4.692000] Attempting manual resume
[    4.692000] swsusp: Resume From Partition 8:5
[    4.692000] PM: Checking swsusp image.
[    4.692000] PM: Resume from disk failed.
[    4.724000] kjournald starting.  Commit interval 5 seconds
[    4.724000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.496000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000f041200d7c1e]
[   16.264000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.268000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.288000] intel_rng: FWH not detected
[   16.328000] iTCO_vendor_support: vendor-support=0
[   16.328000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   16.328000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   16.328000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.732000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.804000] NET: Registered protocol family 17
[   16.808000] agpgart: Detected an Intel 915GM Chipset.
[   16.824000] agpgart: AGP aperture is 256M @ 0x0
[   17.012000] sdhci: Secure Digital Host Controller Interface driver
[   17.012000] sdhci: Copyright(c) Pierre Ossman
[   17.012000] sdhci: SDHCI controller found at 0000:06:09.2 [1180:0822] (rev 17)
[   17.012000] ACPI: PCI Interrupt 0000:06:09.2[C] -> GSI 18 (level, low) -> IRQ 21
[   17.012000] mmc0: SDHCI at 0xc8001800 irq 21 DMA
[   17.040000] Yenta: CardBus bridge found at 0000:06:09.0 [144d:b035]
[   17.168000] Yenta: ISA IRQ mask 0x04b8, PCI irq 16
[   17.168000] Socket status: 30000006
[   17.168000] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[   17.168000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   17.168000] cs: IO port probe 0x5000-0x5fff: clean.
[   17.168000] pcmcia: parent PCI bridge Memory window: 0xc8000000 - 0xc80fffff
[   17.168000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   17.212000] ieee80211_crypt: registered algorithm 'NULL'
[   17.220000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.220000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.252000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   17.252000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.252000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 18
[   17.252000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.532000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   17.964000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
[   17.964000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   18.024000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0x2580b1, caps: 0xa04713/0x200000
[   18.060000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   18.092000] cs: IO port probe 0x100-0x3af: clean.
[   18.096000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.096000] cs: IO port probe 0x820-0x8ff: clean.
[   18.096000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.096000] cs: IO port probe 0xa00-0xaff: clean.
[   18.128000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   18.128000] b44: eth0: Flow control is off for TX and off for RX.
[   18.784000] intel8x0_measure_ac97_clock: measured 55529 usecs
[   18.784000] intel8x0: clocking to 48000
[   18.892000] fuse init (API version 7.8)
[   18.944000] lp: driver loaded but no devices found
[   18.984000] Adding 1028120k swap on /dev/disk/by-uuid/52f3275b-5e16-45bc-acec-2497ccfd28e3.  Priority:-1 extents:1 across:1028120k
[   19.204000] EXT3 FS on sda3, internal journal
[   24.284000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   24.400000] NTFS volume version 3.1.
[   28.716000] input: Power Button (FF) as /class/input/input3
[   28.720000] ACPI: Power Button (FF) [PWRF]
[   28.752000] input: Lid Switch as /class/input/input4
[   28.756000] ACPI: Lid Switch [LID0]
[   28.788000] input: Power Button (CM) as /class/input/input5
[   28.792000] ACPI: Power Button (CM) [PWRB]
[   28.828000] input: Sleep Button (CM) as /class/input/input6
[   28.832000] ACPI: Sleep Button (CM) [SLPB]
[   28.844000] ACPI: AC Adapter [ADP1] (on-line)
[   28.952000] ACPI: Battery Slot [BAT1] (battery present)
[   29.036000] Using specific hotkey driver
[   29.072000] ibm_acpi: ec object not found
[   29.096000] No dock devices found.
[   29.128000] ACPI: Video Device [ATIM] (multi-head: yes  rom: no  post: no)
[   29.128000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   29.164000] pcc_acpi: loading...
[   31.380000] [drm] Initialized drm 1.1.0 20060810
[   31.392000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.392000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   32.628000] ppdev: user-space parallel port driver
[   32.716000] [drm] Setting GART location based on new memory map
[   32.720000] [drm] Loading R300 Microcode
[   32.720000] [drm] writeback test succeeded in 1 usecs
[   33.460000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.460000] apm: overridden by ACPI.
[   33.624000] Bluetooth: Core ver 2.11
[   33.624000] NET: Registered protocol family 31
[   33.624000] Bluetooth: HCI device and connection manager initialized
[   33.624000] Bluetooth: HCI socket layer initialized
[   33.668000] Bluetooth: L2CAP ver 2.8
[   33.668000] Bluetooth: L2CAP socket layer initialized
[   33.860000] Bluetooth: RFCOMM socket layer initialized
[   33.860000] Bluetooth: RFCOMM TTY layer initialized
[   33.860000] Bluetooth: RFCOMM ver 1.8


Error boot DMESG:

> [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000008000 end: 00000000000d8000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fda0000 end: 000000001fea0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fea0000 size: 0000000000011000 end: 000000001feb1000 type: 3
[    0.000000] copy_e820_map() start: 000000001feb1000 size: 000000000004f000 end: 000000001ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000001ff00000 size: 0000000000100000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010006000 end: 00000000f0006000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0008000 size: 0000000000004000 end: 00000000f000c000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000070000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fea0000 (usable)
[    0.000000]  BIOS-e820: 000000001fea0000 - 000000001feb1000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feb1000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130720) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130720
[    0.000000]   HighMem    130720 ->   130720
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130720
[    0.000000] On node 0 totalpages: 130720
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125635 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7860
[    0.000000] ACPI: RSDT (v001 PTLTD  Ohlone00 0x06040000  LTP 0x00000000) @ 0x1feabecf
[    0.000000] ACPI: FADT (v001 SEC    MAGIC    0x06040000 PTL  0x0000005f) @ 0x1feb0e88
[    0.000000] ACPI: MADT (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1feb0efc
[    0.000000] ACPI: HPET (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1feb0f64
[    0.000000] ACPI: MCFG (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1feb0f9c
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1feb0fd8
[    0.000000] ACPI: SSDT (v001 SataRe SataAhci 0x00001000 INTL 0x20030224) @ 0x1feac6f5
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x1feac1ca
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x1feabfe0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x1feabf17
[    0.000000] ACPI: DSDT (v001    SEC    MAGIC 0x06040000 INTL 0x20030224) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Detected 1729.036 MHz processor.
[   10.247002] Built 1 zonelists.  Total pages: 129699
[   10.247007] Kernel command line: root=UUID=ffeee1af-68e1-44ad-8ec5-80d725c2b0c1 ro quiet splash
[   10.247163] mapped APIC to ffffd000 (fee00000)
[   10.247165] mapped IOAPIC to ffffc000 (fec00000)
[   10.247169] Enabling fast FPU save and restore... done.
[   10.247171] Enabling unmasked SIMD FPU exception support... done.
[   10.247179] Initializing CPU#0
[   10.247248] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   10.248387] Console: colour VGA+ 80x25
[   10.248553] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.248750] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.261904] Memory: 507320k/522880k available (1992k kernel code, 14964k reserved, 900k data, 328k init, 0k highmem)
[   10.261913] virtual kernel memory layout:
[   10.261914]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   10.261916]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.261917]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   10.261918]     lowmem  : 0xc0000000 - 0xdfea0000   ( 510 MB)
[   10.261919]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   10.261921]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   10.261922]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   10.261925] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.262070] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   10.262076] hpet0: 3 64-bit timers, 14318180 Hz
[   10.263081] Using HPET for base-timer
[   10.342041] Calibrating delay using timer specific routine.. 3461.45 BogoMIPS (lpj=6922910)
[   10.342078] Security Framework v1.0.0 initialized
[   10.342086] SELinux:  Disabled at boot.
[   10.342100] Mount-cache hash table entries: 512
[   10.342228] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[   10.342239] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.342241] CPU: L2 cache: 2048K
[   10.342244] CPU: After all inits, caps: afe9fbff 00000000 00000000 00002040 00000180 00000000 00000000
[   10.342253] Compat vDSO mapped to ffffe000.
[   10.342257] Remapping vsyscall page to ffffe000
[   10.342267] Checking 'hlt' instruction... OK.
[   10.358120] SMP alternatives: switching to UP code
[   10.358280] Freeing SMP alternatives: 11k freed
[   10.358445] Early unpacking initramfs... done
[   10.682544] ACPI: Core revision 20060707
[   10.682889] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   10.686207] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[   10.686230] Total of 1 processors activated (3461.45 BogoMIPS).
[   10.686419] ENABLING IO-APIC IRQs
[   10.686613] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.833866] Brought up 1 CPUs
[   10.834088] Booting paravirtualized kernel on bare hardware
[   10.834162] Time: 17:16:13  Date: 06/29/107
[   10.834187] NET: Registered protocol family 16
[   10.834258] EISA bus registered
[   10.834262] ACPI: bus type pci registered
[   10.834599] PCI: PCI BIOS revision 2.10 entry at 0xfd91e, last bus=6
[   10.834601] PCI: Using configuration type 1
[   10.834603] Setting up standard PCI resources
[   10.845679] ACPI: Interpreter enabled
[   10.845681] ACPI: Using IOAPIC for interrupt routing
[   10.847419] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.847427] PCI: Probing PCI hardware (bus 00)
[   10.849204] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   10.849209] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   10.849398] Boot video device is 0000:01:00.0
[   10.850045] PCI: Transparent bridge - 0000:00:1e.0
[   10.850104] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#06) (try 'pci=assign-busses')
[   10.850107] Please report the result to linux-kernel to fix this permanently
[   10.850149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.855549] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   10.856301] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   10.856920] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   10.857711] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 6 *10 11)
[   10.857943] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 6 10 *11)
[   10.858154] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 10 *11)
[   10.858363] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 *10 11)
[   10.858572] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 6 *10 11)
[   10.858779] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 6 10 11) *0, disabled.
[   10.858993] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 6 10 *11)
[   10.859202] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 6 10 11)
[   10.860313] ACPI: Power Resource [CFAN] (on)
[   10.860404] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.860412] pnp: PnP ACPI init
[   10.862307] pnp: PnP ACPI: found 10 devices
[   10.862311] PnPBIOS: Disabled by ACPI PNP
[   10.862345] PCI: Using ACPI for IRQ routing
[   10.862348] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.881705] NET: Registered protocol family 8
[   10.881708] NET: Registered protocol family 20
[   10.882057] PCI: Bridge: 0000:00:01.0
[   10.882060]   IO window: 3000-3fff
[   10.882064]   MEM window: c0100000-c01fffff
[   10.882067]   PREFETCH window: d0000000-d7ffffff
[   10.882070] PCI: Bridge: 0000:00:1c.0
[   10.882073]   IO window: 4000-4fff
[   10.882079]   MEM window: c4000000-c7ffffff
[   10.882083]   PREFETCH window: d8000000-dbffffff
[   10.882095] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[   10.882097]   IO window: 00005000-000050ff
[   10.882102]   IO window: 00005400-000054ff
[   10.882107]   PREFETCH window: 30000000-33ffffff
[   10.882112]   MEM window: 34000000-37ffffff
[   10.882116] PCI: Bridge: 0000:00:1e.0
[   10.882119]   IO window: 5000-5fff
[   10.882125]   MEM window: c8000000-c80fffff
[   10.882129]   PREFETCH window: 30000000-33ffffff
[   10.882144] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   10.882150] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   10.882170] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   10.882176] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.882189] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.882243] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   10.882266] NET: Registered protocol family 2
[   10.909849] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   10.909914] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   10.910008] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   10.910055] TCP: Hash tables configured (established 16384 bind 8192)
[   10.910058] TCP reno registered
[   10.921891] checking if image is initramfs... it is
[   11.554630] Freeing initrd memory: 6768k freed
[   11.554849] Simple Boot Flag at 0x36 set to 0x1
[   11.555070] audit: initializing netlink socket (disabled)
[   11.555084] audit(1185729373.376:1): initialized
[   11.555204] VFS: Disk quotas dquot_6.5.1
[   11.555223] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.555270] io scheduler noop registered
[   11.555272] io scheduler anticipatory registered
[   11.555275] io scheduler deadline registered
[   11.555284] io scheduler cfq registered (default)
[   11.555548] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.555576] assign_interrupt_mode Found MSI capability
[   11.555580] Allocate Port Service[0000:00:01.0:pcie00]
[   11.555646] Uhhuh. NMI received for unknown reason a1 on CPU 0.
[   11.555693] You have some hardware problem, likely on the PCI bus.
[   11.555735] Dazed and confused, but trying to continue
[   11.555792] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.555843] assign_interrupt_mode Found MSI capability
[   11.555846] Allocate Port Service[0000:00:1c.0:pcie00]
[   11.555874] Allocate Port Service[0000:00:1c.0:pcie02]
[   11.556035] isapnp: Scanning for PnP cards...
[   11.909975] isapnp: No Plug & Play device found
[   11.932379] Real Time Clock Driver v1.12ac
[   11.932591] hpet_resources: 0xfed00000 is busy
[   11.932605] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.933251] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 18
[   11.933259] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   11.933330] mice: PS/2 mouse device common for all mice
[   11.933859] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.934050] input: Macintosh mouse button emulation as /class/input/input0
[   11.934083] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   11.934087] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   11.934312] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.937302] i8042.c: Detected active multiplexing controller, rev 1.1.
[   11.938878] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.938882] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   11.938884] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   11.938887] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   11.938889] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   11.939004] EISA: Probing bus 0 at eisa.0
[   11.939011] Cannot allocate resource for EISA slot 1
[   11.939014] Cannot allocate resource for EISA slot 2
[   11.939016] Cannot allocate resource for EISA slot 3
[   11.939018] Cannot allocate resource for EISA slot 4
[   11.939021] Cannot allocate resource for EISA slot 5
[   11.939034] EISA: Detected 0 cards.
[   11.969119] TCP cubic registered
[   11.969128] NET: Registered protocol family 1
[   11.969148] Using IPI No-Shortcut mode
[   11.969205] ACPI: (supports S0 S3 S4 S5)
[   11.969252]   Magic number: 15:707:290
[   11.969266]   hash matches device ttyz4
[   11.969353]   hash matches device tty23
[   11.969359] Time: tsc clocksource has been installed.
[   11.969531] Freeing unused kernel memory: 328k freed
[   11.983341] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.169826] Capability LSM initialized
[   13.197142] ACPI: Fan [FAN1] (on)
[   13.200592] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.200597] ACPI: Processor [CPU0] (supports 2 throttling states)
[   13.201838] ACPI: Thermal Zone [THRM] (60 C)
[   13.498817] usbcore: registered new interface driver usbfs
[   13.498839] usbcore: registered new interface driver hub
[   13.498857] usbcore: registered new device driver usb
[   13.499631] USB Universal Host Controller Interface driver v3.0
[   13.499677] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   13.499688] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.499692] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.499848] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.499877] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001800
[   13.499967] usb usb1: configuration #1 chosen from 1 choice
[   13.499988] hub 1-0:1.0: USB hub found
[   13.499993] hub 1-0:1.0: 2 ports detected
[   13.566477] SCSI subsystem initialized
[   13.588823] libata version 2.20 loaded.
[   13.600836] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   13.600849] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.600853] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.600878] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.600911] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001820
[   13.600991] usb usb2: configuration #1 chosen from 1 choice
[   13.601013] hub 2-0:1.0: USB hub found
[   13.601019] hub 2-0:1.0: 2 ports detected
[   13.704765] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   13.704777] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.704782] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.704806] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.704838] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001840
[   13.704916] usb usb3: configuration #1 chosen from 1 choice
[   13.704942] hub 3-0:1.0: USB hub found
[   13.704946] hub 3-0:1.0: 2 ports detected
[   13.712777] ieee1394: Initialized config rom entry `ip1394'
[    3.448000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.448000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.448000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.448000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.448000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    3.448000] usb usb4: configuration #1 chosen from 1 choice
[    3.448000] hub 4-0:1.0: USB hub found
[    3.448000] hub 4-0:1.0: 2 ports detected
[    3.452000] Time: hpet clocksource has been installed.
[    3.552000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.552000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.552000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.552000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.552000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.552000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.552000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xc0000000
[    3.556000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.556000] usb usb5: configuration #1 chosen from 1 choice
[    3.556000] hub 5-0:1.0: USB hub found
[    3.556000] hub 5-0:1.0: 8 ports detected
[    3.660000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.660000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[    3.660000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.660000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118c0 irq 14
[    3.660000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118c8 irq 15
[    3.660000] scsi0 : ata_piix
[    3.988000] ata1.00: ata_hpa_resize 1: sectors = 102022014, hpa_sectors = 117210240
[    3.988000] ata1.00: Host Protected Area detected.
[    3.988000]      current size : 102022014 sectors (52235 MB)
[    3.988000]      native  size : 117210240 sectors (60011 MB)
[    3.988000] ata1.00: SET of native returned 0, expected 117210240
[    3.988000] ata1.00: ATA-6: HTS541060G9AT00, MB3OA60A, max UDMA/100
[    3.988000] ata1.00: 102022014 sectors, multi 16: LBA48 
[    3.988000] ata1.01: ATAPI, max UDMA/33
[    3.996000] ata1.00: ata_hpa_resize 1: sectors = 102022014, hpa_sectors = 117210240
[    3.996000] ata1.00: Host Protected Area detected.
[    3.996000]      current size : 102022014 sectors (52235 MB)
[    3.996000]      native  size : 117210240 sectors (60011 MB)
[    3.996000] ata1.00: SET of native returned 0, expected 117210240
[    3.996000] ata1.00: configured for UDMA/100
[    4.160000] ata1.01: configured for UDMA/33
[    4.160000] scsi1 : ata_piix
[    4.160000] ata2: port disabled. ignoring.
[    4.160000] scsi 0:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3O PQ: 0 ANSI: 5
[    4.160000] scsi 0:0:1:0: CD-ROM            TEAC     DV-W28EA         S.0A PQ: 0 ANSI: 5
[    4.164000] b44.c:v1.01 (Jun 16, 2006)
[    4.164000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 22 (level, low) -> IRQ 22
[    4.168000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:00:f0:7c:b0:c8
[    4.168000] ACPI: PCI Interrupt 0000:06:09.1[B] -> GSI 17 (level, low) -> IRQ 17
[    4.220000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[c8001000-c80017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.240000] SCSI device sda: 102022014 512-byte hdwr sectors (52235 MB)
[    4.240000] sda: Write Protect is off
[    4.240000] sda: Mode Sense: 00 3a 00 00
[    4.240000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.240000] SCSI device sda: 102022014 512-byte hdwr sectors (52235 MB)
[    4.240000] sda: Write Protect is off
[    4.240000] sda: Mode Sense: 00 3a 00 00
[    4.240000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.240000]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    4.280000] sd 0:0:0:0: Attached scsi disk sda
[    4.280000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.280000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.352000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.352000] Uniform CD-ROM driver Revision: 3.20
[    4.352000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    4.780000] Attempting manual resume
[    4.780000] swsusp: Resume From Partition 8:5
[    4.780000] PM: Checking swsusp image.
[    4.780000] PM: Resume from disk failed.
[    4.804000] kjournald starting.  Commit interval 5 seconds
[    4.804000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.500000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000f041200d7c1e]
[   16.244000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.248000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.596000] intel_rng: FWH not detected
[   16.640000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.644000] NET: Registered protocol family 17
[   16.660000] agpgart: Detected an Intel 915GM Chipset.
[   16.676000] agpgart: AGP aperture is 256M @ 0x0
[   16.900000] iTCO_vendor_support: vendor-support=0
[   16.900000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   16.900000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   16.900000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.916000] ieee80211_crypt: registered algorithm 'NULL'
[   16.916000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.916000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.928000] sdhci: Secure Digital Host Controller Interface driver
[   16.928000] sdhci: Copyright(c) Pierre Ossman
[   16.928000] sdhci: SDHCI controller found at 0000:06:09.2 [1180:0822] (rev 17)
[   16.928000] ACPI: PCI Interrupt 0000:06:09.2[C] -> GSI 18 (level, low) -> IRQ 21
[   16.928000] mmc0: SDHCI at 0xc8001800 irq 21 DMA
[   16.984000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   16.984000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.984000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 18
[   16.984000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.740000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   17.740000] Yenta: CardBus bridge found at 0000:06:09.0 [144d:b035]
[   17.812000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0x2580b1, caps: 0xa04713/0x200000
[   17.848000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   17.868000] Yenta: ISA IRQ mask 0x04b8, PCI irq 16
[   17.868000] Socket status: 30000006
[   17.868000] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[   17.868000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   17.868000] cs: IO port probe 0x5000-0x5fff: clean.
[   17.868000] pcmcia: parent PCI bridge Memory window: 0xc8000000 - 0xc80fffff
[   17.868000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   17.872000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
[   17.872000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   18.180000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   18.180000] b44: eth0: Flow control is off for TX and off for RX.
[   18.184000] cs: IO port probe 0x100-0x3af: clean.
[   18.184000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.184000] cs: IO port probe 0x820-0x8ff: clean.
[   18.184000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.188000] cs: IO port probe 0xa00-0xaff: clean.
[   18.692000] intel8x0_measure_ac97_clock: measured 55532 usecs
[   18.692000] intel8x0: clocking to 48000
[   18.816000] fuse init (API version 7.8)
[   18.868000] lp: driver loaded but no devices found
[   18.908000] Adding 1028120k swap on /dev/disk/by-uuid/52f3275b-5e16-45bc-acec-2497ccfd28e3.  Priority:-1 extents:1 across:1028120k
[   19.136000] EXT3 FS on sda3, internal journal
[   24.492000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   24.568000] NTFS volume version 3.1.
[   28.764000] input: Power Button (FF) as /class/input/input3
[   28.768000] ACPI: Power Button (FF) [PWRF]
[   28.800000] input: Lid Switch as /class/input/input4
[   28.804000] ACPI: Lid Switch [LID0]
[   28.840000] input: Power Button (CM) as /class/input/input5
[   28.840000] ACPI: Power Button (CM) [PWRB]
[   28.876000] input: Sleep Button (CM) as /class/input/input6
[   28.876000] ACPI: Sleep Button (CM) [SLPB]
[   28.888000] ACPI: AC Adapter [ADP1] (on-line)
[   29.008000] ACPI: Battery Slot [BAT1] (battery present)
[   29.112000] Using specific hotkey driver
[   29.148000] ibm_acpi: ec object not found
[   29.172000] No dock devices found.
[   29.200000] ACPI: Video Device [ATIM] (multi-head: yes  rom: no  post: no)
[   29.200000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   29.248000] pcc_acpi: loading...
[   31.252000] [drm] Initialized drm 1.1.0 20060810
[   31.264000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.264000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   32.536000] ppdev: user-space parallel port driver
[   32.544000] [drm] Setting GART location based on new memory map
[   32.548000] [drm] Loading R300 Microcode
[   32.548000] [drm] writeback test succeeded in 1 usecs
[   33.332000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.332000] apm: overridden by ACPI.
[   33.412000] Bluetooth: Core ver 2.11
[   33.412000] NET: Registered protocol family 31
[   33.412000] Bluetooth: HCI device and connection manager initialized
[   33.412000] Bluetooth: HCI socket layer initialized
[   33.432000] Bluetooth: L2CAP ver 2.8
[   33.432000] Bluetooth: L2CAP socket layer initialized
[   33.632000] Bluetooth: RFCOMM socket layer initialized
[   33.632000] Bluetooth: RFCOMM TTY layer initialized
[   33.632000] Bluetooth: RFCOMM ver 1.8


My current xorg.conf:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc M22 [Radeon Mobility M300]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"DisableGLXRootClipping"	"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"XAANoOffscreenPixmaps"
	Option		"TripleBuffer"		"true"
	Option		"ColorTiling"		"on"
	Option		"AllowGLXWithComposite"	"true"
	Option		"EnablePageFlip"	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M22 [Radeon Mobility M300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	Option		"AIGLX"		"true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section	"Extensions"
	Option	"Composite"	"Enable"
EndSection

Thanks for the attention. Let us hope this issue gets solved soon.

Launchpad link for the bug: [https://answers.launchpad.net/ubuntu/+question/5847](https://answers.launchpad.net/ubuntu/+question/5847)

---

### Post by punkrokk on 2007-08-08
Any word on this?

---

### Post by What is in a name? on 2007-08-13
I guess not... Unfortunately... I was hoping some of the experts would have a hint of what is going on... But oh, well...

---

### Post by GChriss on 2007-08-25
Hi,

This problem sounds very similar to one reported two weeks ago on the Madwifi bug tracking system:

[http://madwifi.org/ticket/1499](http://madwifi.org/ticket/1499)

Hope this helps, George

---

### Post by dooma on 2007-12-28
Thanks for the link to the madwifi ticket. I think this is the problem on my machine (t60p using fglrx for graphics card  and madwifi for atheros card).  I just posted this at that ticket if it helps anyone:  

 ¶

Yes. I have the same problem as well. Is there any workaround that works without having to reboot the computer? Also, I found something potentially interesting by looking at my kern.log:

Does anyone know what this means:

Dec 27 18:56:43 localhost kernel: [13641.904000] Uhhuh. NMI received for unknown reason b0 on CPU 0. Dec 27 18:56:43 localhost kernel: [13641.904000] You have some hardware problem, likely on the PCI bus.

Dec 27 18:56:43 localhost kernel: [13641.904000] Dazed and confused, but trying to continue

Dec 27 18:56:46 localhost kernel: [13644.560000] wifi0: rx FIFO overrun; resetting

The "FIFO Overrun" thing keeps on appearing onece every few seconds, but somewhere down the line, this pops up:

Dec 27 19:26:57 localhost kernel: [15455.724000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready

Dec 27 19:27:05 localhost kernel: [15463.684000] ADDRCONF(NETDEV_UP): ath0: link is not ready

Dec 27 19:27:07 localhost kernel: [15465.208000] ath_rate_sample: no rates for 00:19:7e:52:18:44?

Dec 27 19:27:12 localhost kernel: [15470.444000] ADDRCONF(NETDEV_UP): ath0: link is not ready

No clue if that helps at all.

Please help with this!

---

