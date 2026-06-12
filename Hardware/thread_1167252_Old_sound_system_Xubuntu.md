---
title: "Old sound system Xubuntu"
date: 2009-05-22
forum: Hardware
---

### Post by Wolvenreign on 2009-05-22
Hello everyone!

I apologize if I've asked this before, as I have a faint memory of doing something like this.

At any rate, I've installed the latest version of Xubuntu 9.04 on my friend's old computer. It works wonderfully in most respects, other than the volume. I used Sysinfo to find his type of video card, and have yet to find a compatible Linux driver. Perhaps you wonderful people can help me find a solution.

Here's the type of video card sysinfo pulls up;

82801AA AC'97 Audio controller (rev 02)

Subsytem: Dell Device 00b4

---

### Post by kerry_s on 2009-05-22
have you tried installing alsa? **sudo apt-get install alsa-base alsa-utils**

---

### Post by Wolvenreign on 2009-05-22
Indeed, it doesn't seem to work.

---

### Post by kerry_s on 2009-05-22
that's strange, try uninstalling any other sound daemons that you might have installed such as pulseadio or esound-clients. you might need to reboot so alsa can properly detect and use the sound card.

my sound cards a ac97, im only using alsa.

---

### Post by Wolvenreign on 2009-05-22
Well, it seems as though it was already installed. When I did the procedure, it said it looked for updates, but it didn't find any.

This leads me to believe it was already on there. However, I will reboot and see if it works.

Edit: Unfortunately, the sound is still dysfunctional.

*sigh*

I try so hard to put Ubuntu on my friends' computers, but it always comes with some kind of serious problem. Printer doesn't work, sound doesn't work....I've had to reinstall windows on two other systems...v_v;;

Bah. I won't give up yet. There must be some way.

---

### Post by Wolvenreign on 2009-05-22
I am truly sorry to double post when I could edit, but I am quite desperate for some help. I really don't want to resort to reinstalling windows for a simple sound problem. Please...I'm in such a fix...

---

### Post by kerry_s on 2009-05-22
your sure it's not working, could it be muted?
click on the icon, to get the xfc4-mixer.
or open the terminal and type> **alsamixer**

---

### Post by kerry_s on 2009-05-22
hey i googled your sound card, theres a lot of bugs against that, but i did see a couple of suggestions.

[http://www.google.com/search?hl=en&safe=off&client=iceweasel-a&rls=org.debian%3Aen-US%3Aunofficial&q=ubuntu+82801AA+AC%2797+Audio&btnG=Search](http://www.google.com/search?hl=en&safe=off&client=iceweasel-a&rls=org.debian%3Aen-US%3Aunofficial&q=ubuntu+82801AA+AC%2797+Audio&btnG=Search)

i'd look through it, but i'm having hd issues right now, keeps locking up, then i get the no boot device message, so got to try a different hd see ya later.

---

### Post by Wolvenreign on 2009-05-23
I can't thank you enough, Kerry. I felt foolish posting twice in the span of only a half an hour...but I guess that's what you get for only 3 hours of sleep.

I'll look through this. and edit this post later.

Edit: The interesting thing is, some of these results had Ubuntu work for the sound system, whereas they were having problems with windows. Check this one out.

[http://www.tech-forums.net/computer/topic/47067.html](http://www.tech-forums.net/computer/topic/47067.html)

"hi - i've got a problem with installing my soundcard (chip, actually). i bought this secondhand computer, a compaq deskpro (i know its not the best but still!) and i had a hard time finding the drivers for the graphic card at the intel website, but i need drivers for the soundcard too, and intel doesn't provide them anymore.
it's about an intel 82801aa ac'97 audio, and the drivers i found on internet are no good (i get somekind of crystal wdm card the computer sais!?
but it sais the driver is the correct one, so i install it and the computer will either freeze or install, and when i check System it sais that not the right drivers are loaded.
Oh, i'm running win98.
I figured out what exact soundchip it was by running the live cd of ubuntu (linux version) that recognized it and also played sounds, so i know the problem is not the chip but windows...
please, help me!"

---

### Post by kerry_s on 2009-05-23
> **Wolvenreign said:**
> I can't thank you enough, Kerry. I felt foolish posting twice in the span of only a half an hour...but I guess that's what you get for only 3 hours of sleep.

I'll look through this. and edit this post later.

Edit: The interesting thing is, some of these results had Ubuntu work for the sound system, whereas they were having problems with windows. Check this one out.

[http://www.tech-forums.net/computer/topic/47067.html](http://www.tech-forums.net/computer/topic/47067.html)

"hi - i've got a problem with installing my soundcard (chip, actually). i bought this secondhand computer, a compaq deskpro (i know its not the best but still!) and i had a hard time finding the drivers for the graphic card at the intel website, but i need drivers for the soundcard too, and intel doesn't provide them anymore.
it's about an intel 82801aa ac'97 audio, and the drivers i found on internet are no good (i get somekind of crystal wdm card the computer sais!?
but it sais the driver is the correct one, so i install it and the computer will either freeze or install, and when i check System it sais that not the right drivers are loaded.
Oh, i'm running win98.
I figured out what exact soundchip it was by running the live cd of ubuntu (linux version) that recognized it and also played sounds, so i know the problem is not the chip but windows...
please, help me!"


give me a little time to look through those, i just got my desktop back up and running and i'm still setting up. i'll get back to you later.

---

### Post by kerry_s on 2009-05-23
can you post your /var/log/dmesg.log so i can look for errors or try and see what it's doing.

---

### Post by Wolvenreign on 2009-05-23
Certainly, but the computer in question is my friend's. First I must go to his house, which I will do shortly.

Edit: Oh, and forgive me for my noobishness, but how would I pull that up? (Pfft, nevermind. Brain skipped a beat.) Supposedly, I attached the file in the thread. I hope it shows up.

---

### Post by Wolvenreign on 2009-05-23
Just in case, here are the files again. I don't think they loaded the first time.

---

### Post by kerry_s on 2009-05-23
> **Wolvenreign said:**
> Just in case, here are the files again. I don't think they loaded the first time.

press alt+f2
type> gksudo mousepad /var/log/dmesg

click edit> select all

then copy and paste it here in the code tags(code tags are the # on the message window)

---

### Post by Wolvenreign on 2009-05-24
```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001feae000 (usable)
[    0.000000]  BIOS-e820: 000000001feae000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x1feae max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000093000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001feae000 (usable)
[    0.000000]  modified: 000000001feae000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 1feae000 @ 10000-16000
[    0.000000] RAMDISK: 1f75e000 - 1fe9dba4
[    0.000000] ACPI: RSDP 000FD790, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD7A4, 0028 (r1 DELL    GX110          7 ASL        61)
[    0.000000] ACPI: FACP 000FD7CC, 0074 (r1 DELL    GX110          7 ASL        61)
[    0.000000] ACPI: DSDT FFFE6000, 17FA (r1   DELL    dt_ex     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1FEAE000, 0040
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1feae000
[    0.000000]   low ram: 00000000 - 1feae000
[    0.000000]   bootmap 00012000 - 00015fd8
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001feae000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [001f75e000 - 001fe9dba4]          RAMDISK ==> [001f75e000 - 001fe9dba4]
[    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001feae
[    0.000000]   HighMem  0x0001feae -> 0x0001feae
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000093
[    0.000000]     0: 0x00000100 -> 0x0001feae
[    0.000000] On node 0 totalpages: 130612
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3942 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125648 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000093000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129590
[    0.000000] Kernel command line: root=UUID=5ea02a8e-2bba-46bb-bec6-f43f10e77de5 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 863.781 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2614680 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 499948k/522936k available (4126k kernel code, 22256k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xe06ae000 - 0xff3fe000   ( 493 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdfeae000   ( 510 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004025] Calibrating delay loop (skipped), value calculated using timer frequency.. 1727.56 BogoMIPS (lpj=3455124)
[    0.004081] Security Framework initialized
[    0.004106] SELinux:  Disabled at boot.
[    0.004163] AppArmor: AppArmor initialized
[    0.004188] Mount-cache hash table entries: 512
[    0.004549] Initializing cgroup subsys ns
[    0.004561] Initializing cgroup subsys cpuacct
[    0.004568] Initializing cgroup subsys memory
[    0.004578] Initializing cgroup subsys freezer
[    0.004618] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004626] CPU: L2 cache: 256K
[    0.004673] Checking 'hlt' instruction... OK.
[    0.021234] SMP alternatives: switching to UP code
[    0.293909] Freeing SMP alternatives: 18k freed
[    0.293924] ACPI: Core revision 20080926
[    0.302954] ACPI: Checking initramfs for custom DSDT
[    1.044887] ACPI: setting ELCR to 0200 (from 0e20)
[    1.045401] weird, boot CPU (#0) not listedby the BIOS.
[    1.045408] SMP motherboard not detected.
[    1.045417] Local APIC not detected. Using dummy APIC emulation.
[    1.045422] SMP disabled
[    1.046371] Brought up 1 CPUs
[    1.046382] Total of 1 processors activated (1727.56 BogoMIPS).
[    1.046432] CPU0 attaching NULL sched-domain.
[    1.047554] net_namespace: 776 bytes
[    1.047599] Booting paravirtualized kernel on bare hardware
[    1.048374] Time: 23:10:47  Date: 05/22/09
[    1.048391] regulator: core version 0.5
[    1.048513] NET: Registered protocol family 16
[    1.048911] EISA bus registered
[    1.048955] ACPI: bus type pci registered
[    1.074583] PCI: PCI BIOS revision 2.10 entry at 0xfc0be, last bus=1
[    1.074590] PCI: Using configuration type 1 for base access
[    1.078154] ACPI: EC: Look up EC in DSDT
[    1.085077] ACPI: Interpreter enabled
[    1.085095] ACPI: (supports S0 S1 S4 S5)
[    1.085143] ACPI: Using PIC for interrupt routing
[    1.092100] ACPI: No dock devices found.
[    1.092139] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.092302] pci 0000:00:01.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    1.092314] pci 0000:00:01.0: reg 14 32bit mmio: [0xff000000-0xff07ffff]
[    1.092484] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    1.092493] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    1.092544] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    1.092612] pci 0000:00:1f.2: reg 20 io port: [0xff80-0xff9f]
[    1.092679] pci 0000:00:1f.3: reg 20 io port: [0xdcd0-0xdcdf]
[    1.092725] pci 0000:00:1f.5: reg 10 io port: [0xd800-0xd8ff]
[    1.092737] pci 0000:00:1f.5: reg 14 io port: [0xdc80-0xdcbf]
[    1.092842] pci 0000:01:0c.0: reg 10 io port: [0xec80-0xecff]
[    1.092855] pci 0000:01:0c.0: reg 14 32bit mmio: [0xfdfffc00-0xfdfffc7f]
[    1.092887] pci 0000:01:0c.0: reg 30 32bit mmio: [0xfe000000-0xfe01ffff]
[    1.092902] pci 0000:01:0c.0: supports D1 D2
[    1.092909] pci 0000:01:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.092918] pci 0000:01:0c.0: PME# disabled
[    1.092953] pci 0000:00:1e.0: transparent bridge
[    1.092963] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    1.092972] pci 0000:00:1e.0: bridge 32bit mmio: [0xfd000000-0xfeffffff]
[    1.092989] bus 00 -> node 0
[    1.093006] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.093608] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    1.097214] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    1.097647] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.098075] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.098502] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    1.098738] ACPI: WMI: Mapper loaded
[    1.099424] SCSI subsystem initialized
[    1.099574] libata version 3.00 loaded.
[    1.099731] usbcore: registered new interface driver usbfs
[    1.099783] usbcore: registered new interface driver hub
[    1.099869] usbcore: registered new device driver usb
[    1.100249] PCI: Using ACPI for IRQ routing
[    1.100447] Bluetooth: Core ver 2.13
[    1.100447] NET: Registered protocol family 31
[    1.100447] Bluetooth: HCI device and connection manager initialized
[    1.100447] Bluetooth: HCI socket layer initialized
[    1.100447] NET: Registered protocol family 8
[    1.100447] NET: Registered protocol family 20
[    1.100447] NetLabel: Initializing
[    1.100447] NetLabel:  domain hash size = 128
[    1.100447] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.100447] NetLabel:  unlabeled traffic allowed by default
[    1.100558] AppArmor: AppArmor Filesystem Enabled
[    1.100594] pnp: PnP ACPI init
[    1.100594] ACPI: bus type pnp registered
[    1.115651] pnp 00:0c: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    1.115663] pnp 00:0c: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    1.116279] pnp: PnP ACPI: found 13 devices
[    1.116286] ACPI: ACPI bus type pnp unregistered
[    1.116298] PnPBIOS: Disabled by ACPI PNP
[    1.116330] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    1.116339] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    1.116347] system 00:00: iomem range 0x1000000-0x1feadfff could not be reserved
[    1.116355] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    1.116363] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    1.116371] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
[    1.116399] system 00:0c: ioport range 0xc00-0xc7f has been reserved
[    1.151491] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    1.151501] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    1.151514] pci 0000:00:1e.0:   MEM window: 0xfd000000-0xfeffffff
[    1.151524] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x000000300fffff
[    1.151553] pci 0000:00:1e.0: setting latency timer to 64
[    1.151565] bus: 00 index 0 io port: [0x00-0xffff]
[    1.151571] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.151577] bus: 01 index 0 io port: [0xe000-0xefff]
[    1.151583] bus: 01 index 1 mmio: [0xfd000000-0xfeffffff]
[    1.151589] bus: 01 index 2 mmio: [0x30000000-0x300fffff]
[    1.151595] bus: 01 index 3 io port: [0x00-0xffff]
[    1.151601] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    1.151636] NET: Registered protocol family 2
[    1.152061] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    1.152819] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    1.153217] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    1.153682] TCP: Hash tables configured (established 16384 bind 16384)
[    1.153693] TCP reno registered
[    1.154142] NET: Registered protocol family 1
[    1.154583] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.879274]  it is
[    2.824701] Freeing initrd memory: 7422k freed
[    2.824901] cpufreq: No nForce2 chipset.
[    2.825390] audit: initializing netlink socket (disabled)
[    2.825450] type=2000 audit(1243033848.824:1): initialized
[    2.846243] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.850299] VFS: Disk quotas dquot_6.5.1
[    2.850489] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.852609] fuse init (API version 7.10)
[    2.852872] msgmni has been set to 991
[    2.853541] alg: No test for stdrng (krng)
[    2.853584] io scheduler noop registered
[    2.853590] io scheduler anticipatory registered
[    2.853596] io scheduler deadline registered
[    2.853672] io scheduler cfq registered (default)
[    2.853728] pci 0000:00:01.0: Boot video device
[    2.858854] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.858881] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.859221] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.859230] ACPI: Power Button (FF) [PWRF]
[    2.859670] processor ACPI_CPU:00: registered as cooling_device0
[    2.862742] isapnp: Scanning for PnP cards...
[    3.216792] isapnp: No Plug & Play device found
[    3.220220] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.220365] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.220492] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.221235] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.221463] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.223618] brd: module loaded
[    3.224660] loop: module loaded
[    3.224934] Fixed MDIO Bus: probed
[    3.224954] PPP generic driver version 2.4.2
[    3.225143] input: Macintosh mouse button emulation as /devices/virtual/input/input1
[    3.225253] Driver 'sd' needs updating - please use bus_type methods
[    3.225280] Driver 'sr' needs updating - please use bus_type methods
[    3.225484] ata_piix 0000:00:1f.1: version 2.12
[    3.225670] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.226016] scsi0 : ata_piix
[    3.226395] scsi1 : ata_piix
[    3.226512] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.226521] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.388564] ata1.00: ATA-7: Maxtor 4R120L0, RAMB1TU0, max UDMA/133
[    3.388573] ata1.00: 240121728 sectors, multi 8: LBA48 
[    3.404503] ata1.00: configured for UDMA/66
[    3.568350] ata2.00: ATAPI: SAMSUNG CD-ROM  SC-148C, C002, max UDMA/33
[    3.576335] ata2.00: configured for UDMA/33
[    3.576953] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 4R120L0   RAMB PQ: 0 ANSI: 5
[    3.577264] sd 0:0:0:0: [sda] 240121728 512-byte hardware sectors: (122 GB/114 GiB)
[    3.577317] sd 0:0:0:0: [sda] Write Protect is off
[    3.577325] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.577407] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.577629] sd 0:0:0:0: [sda] 240121728 512-byte hardware sectors: (122 GB/114 GiB)
[    3.577675] sd 0:0:0:0: [sda] Write Protect is off
[    3.577682] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.577761] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.577773]  sda: sda1 sda2 < sda5 >
[    3.639141] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.639317] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.639796] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SC-148C   C002 PQ: 0 ANSI: 5
[    3.642681] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    3.642692] Uniform CD-ROM driver Revision: 3.20
[    3.643039] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.643180] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.644910] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.644974] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.645017] uhci_hcd: USB Universal Host Controller Interface driver
[    3.645907] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.645916] PCI: setting IRQ 11 as level-triggered
[    3.645926] uhci_hcd 0000:00:1f.2: PCI INT D -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.645950] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    3.645959] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    3.646194] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    3.646244] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ff80
[    3.646561] usb usb1: configuration #1 chosen from 1 choice
[    3.646642] hub 1-0:1.0: USB hub found
[    3.646674] hub 1-0:1.0: 2 ports detected
[    3.647075] usbcore: registered new interface driver libusual
[    3.647177] usbcore: registered new interface driver usbserial
[    3.647208] USB Serial support registered for generic
[    3.647245] usbcore: registered new interface driver usbserial_generic
[    3.647252] usbserial: USB Serial Driver core
[    3.647383] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    3.649421] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.649439] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.649765] mice: PS/2 mouse device common for all mice
[    3.650139] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.650173] rtc0: alarms up to one day, 242 bytes nvram
[    3.650471] device-mapper: uevent: version 1.0.3
[    3.650839] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.651015] device-mapper: multipath: version 1.0.5 loaded
[    3.651025] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.651321] EISA: Probing bus 0 at eisa.0
[    3.651380] EISA: Detected 0 cards.
[    3.651470] cpuidle: using governor ladder
[    3.651476] cpuidle: using governor menu
[    3.653141] TCP cubic registered
[    3.653498] NET: Registered protocol family 10
[    3.654748] lo: Disabled Privacy Extensions
[    3.655694] NET: Registered protocol family 17
[    3.655768] Bluetooth: L2CAP ver 2.11
[    3.655774] Bluetooth: L2CAP socket layer initialized
[    3.655783] Bluetooth: SCO (Voice Link) ver 0.6
[    3.655788] Bluetooth: SCO socket layer initialized
[    3.655945] Bluetooth: RFCOMM socket layer initialized
[    3.655974] Bluetooth: RFCOMM TTY layer initialized
[    3.655979] Bluetooth: RFCOMM ver 1.10
[    3.656183] IO APIC resources could be not be allocated.
[    3.656246] Using IPI No-Shortcut mode
[    3.656538] registered taskstats version 1
[    3.656788]   Magic number: 9:703:201
[    3.656963] rtc_cmos 00:05: setting system clock to 2009-05-22 23:10:50 UTC (1243033850)
[    3.656972] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.656977] EDD information not available.
[    3.659484] Freeing unused kernel memory: 532k freed
[    3.659865] Write protecting the kernel text: 4128k
[    3.659970] Write protecting the kernel read-only data: 1532k
[    3.700340] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    4.580479] Floppy drive(s): fd0 is 1.44M
[    4.599401] FDC 0 is a National Semiconductor PC87306
[    4.679454] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[    4.679468] PCI: setting IRQ 5 as level-triggered
[    4.679478] 3c59x 0000:01:0c.0: PCI INT A -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    4.679590] 3c59x: Donald Becker and others.
[    4.679607] 0000:01:0c.0: 3Com PCI 3c905C Tornado at e0802c00.
[    6.068425] PM: Starting manual resume from disk
[    6.068440] PM: Resume from partition 8:5
[    6.068445] PM: Checking hibernation image.
[    6.068995] PM: Resume from disk failed.
[    6.142768] kjournald starting.  Commit interval 5 seconds
[    6.142820] EXT3-fs: mounted filesystem with ordered data mode.
[   13.601396] udev: starting version 141
[   13.962236] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.978313] Intel 82802 RNG detected
[   14.007162] Linux agpgart interface v0.103
[   14.074124] agpgart-intel 0000:00:00.0: Intel i810 Chipset
[   14.080554] pci 0000:00:01.0: detected 4MB dedicated video ram
[   14.082873] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   14.318744] parport_pc 00:0b: reported by Plug and Play ACPI
[   14.318858] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[   14.539746] iTCO_vendor_support: vendor-support=0
[   14.600553] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   14.643244] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   14.644197] iTCO_wdt: Found a ICH TCO device (Version=1, TCOBASE=0x0860)
[   14.644415] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.866892] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   15.276701] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.378302] psmouse serio1: ID: 10 00 64<4>logips2pp: Detected unknown logitech mouse model 74
[   15.746042] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   15.746057] PCI: setting IRQ 10 as level-triggered
[   15.746068] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   15.746124] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   16.006578] ppdev: user-space parallel port driver
[   16.031903] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input4
[   16.416052] intel8x0_measure_ac97_clock: measured 54540 usecs
[   16.416065] intel8x0: clocking to 48000
[   16.815983] lp0: using parport0 (interrupt-driven).
[   17.113625] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k
[   17.899296] EXT3 FS on sda1, internal journal
[   19.829017] type=1505 audit(1243033866.671:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1735
[   19.829913] type=1505 audit(1243033866.671:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1735
[   19.830284] type=1505 audit(1243033866.671:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1735
[   19.830544] type=1505 audit(1243033866.671:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1735
[   20.330543] type=1505 audit(1243033867.171:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1740
[   20.331822] type=1505 audit(1243033867.171:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1740
[   20.442704] type=1505 audit(1243033867.283:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1744
[   25.171264] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.171276] Bluetooth: BNEP filters: protocol multicast
[   25.280558] Bridge firewalling registered
[   27.859841] [drm] Initialized drm 1.1.0 20060810
[   27.897438] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[   27.897451] PCI: setting IRQ 9 as level-triggered
[   27.897461] pci 0000:00:01.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[   27.897475] pci 0000:00:01.0: setting latency timer to 64
[   27.898053] [drm] Initialized i810 1.4.0 20030605 on minor 0
[   28.100211] mtrr: base(0xf8000000) is not aligned on a size(0x3aa000) boundary
[   28.114599] [drm] Using v1.4 init.
```

Here you are.

---

### Post by kerry_s on 2009-05-24
i don't even see it loading. let me see whats loaded.
in a terminal:
**lsmod > ~/Desktop/mod**

that should create a file on your desktop that shows all the modules you have loaded. copy and paste that here.

---

### Post by kerry_s on 2009-05-24
have you tried reinstalling, maybe something went wrong during install?
everything i see says it's suppose to just work.

you might want to give straight debian a shot, it will run a heck of a lot better with that 900mhz 512mb ram you have.
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

that's the debian net installer, choose advanced options> alternate desktops> xfce4

---

### Post by Wolvenreign on 2009-05-24
```
Module                  Size  Used by
binfmt_misc            16776  1 
i810                   26240  2 
drm                    96296  3 i810
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
ppdev                  15620  0 
snd_intel8x0           37532  4 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  2 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
dcdbas                 15264  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
soundcore              15200  2 snd
iTCO_wdt               19108  0 
pcspkr                 10496  0 
serio_raw              13316  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
iTCO_vendor_support    11652  1 iTCO_wdt
parport_pc             40100  1 
intel_agp              34108  1 
parport                42220  3 lp,ppdev,parport_pc
agpgart                42696  3 drm,intel_agp
intel_rng              12672  0 
shpchp                 40212  0 
3c59x                  49192  0 
mii                    13312  1 3c59x
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Here's the code you asked for. I'll look into doing straight Debian.

---

### Post by kerry_s on 2009-05-24
> **Wolvenreign said:**
> ```
Module                  Size  Used by
binfmt_misc            16776  1 
i810                   26240  2 
drm                    96296  3 i810
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
ppdev                  15620  0 
snd_intel8x0           37532  4 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  2 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
dcdbas                 15264  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
soundcore              15200  2 snd
iTCO_wdt               19108  0 
pcspkr                 10496  0 
serio_raw              13316  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
iTCO_vendor_support    11652  1 iTCO_wdt
parport_pc             40100  1 
intel_agp              34108  1 
parport                42220  3 lp,ppdev,parport_pc
agpgart                42696  3 drm,intel_agp
intel_rng              12672  0 
shpchp                 40212  0 
3c59x                  49192  0 
mii                    13312  1 3c59x
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Here's the code you asked for. I'll look into doing straight Debian.

okay, it has all the drivers for your sound card.
did you run "alsamixer" in terminal and crank up all the settings also the "MM" should be green use the "M" key to unmute.

---

### Post by Wolvenreign on 2009-05-25
Aha! Zingo bingo, it worked. Turns out Xubuntu thought the Master control should be muted by default. Not really sure why. Thanks Kerry! You stuck through this multi-day ordeal with me to the very end.

Edit: Strange...every time he turns the computer off, and turns it back on again...it defaults to being mute. Why is that?

---

