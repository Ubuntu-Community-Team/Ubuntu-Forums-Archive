---
title: "synaptic package manager fails to launch..."
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by ppillard on 2009-01-07
Hello all,

Brace yourselves, I'm a complete noob to linux.  Just had a clean install of Ubuntu 8.10 installed on this ol' Sony notebook of mine.  All seemed to be fine till I try installing updates.  The updates fail to install with no error message.  after asking for my admin password, the package window just vanishes, leaving the package item still in the managers list of updates.

Next, I tried to install the flash player plugin on Firefox, with the exact same effect.  A little research on the web led me to the Synaptic Package Manager.  When I try to launch it, it acts suspiciously like the above mentioned updates:  It asks me for my password and then fails to launch with no error message.

A little more research lead me here, where I found the terminal window to manually launch the flash package.  Again, the terminal window asks me for my password, then goes blech!

Any help would be greatly appreciated.  Do not dispair, with a little help I am fast learner!

---

### Post by Pumalite on 2009-01-07
Post:
```
cat /etc/apt/sources.list
```

---

### Post by albinootje on 2009-01-07
> **ppillard said:**
>  A little research on the web led me to the Synaptic Package Manager.  When I try to launch it, it acts suspiciously like the above mentioned updates:  It asks me for my password and then fails to launch with no error message.


Can you also post the output of :
```

df -h
sudo apt-get update

```
And lauch synaptic as following :
```

sudo synaptic

```
And post any errors in that terminal, and/or post screenshots from errors in Synaptic Package Manager.

---

### Post by ppillard on 2009-01-09
> **Pumalite said:**
> Post:
```
cat /etc/apt/sources.list
```

Per your request:

pillard@pillard-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
pillard@pillard-laptop:~$ 

hmmmm....

---

### Post by ppillard on 2009-01-09
> **albinootje said:**
> Can you also post the output of :
```

df -h
sudo apt-get update

```

Per your request:

pillard@pillard-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  2.4G   65G   4% /
tmpfs                 125M     0  125M   0% /lib/init/rw
varrun                125M  100K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M  2.7M  122M   3% /dev
tmpfs                 125M  148K  125M   1% /dev/shm
lrm                   125M  2.0M  123M   2% /lib/modules/2.6.27-7-generic/volatile 



> **albinootje said:**
> And lauch synaptic as following :
```

sudo synaptic

```
And post any errors in that terminal, and/or post screenshots from errors in Synaptic Package Manager.

Fails to launch, no error messages at all, just requests my password and returns to awaiting command prompt.

---

### Post by albinootje on 2009-01-09
> **ppillard said:**
> Fails to launch, no error messages at all, just requests my password and returns to awaiting command prompt.
Thanks.

Please post also the complete output of :
```

sudo apt-get update
sudo apt-get install flashplugin-nonfree

```
Thanks in advance.

---

### Post by ppillard on 2009-01-09
> **albinootje said:**
> Thanks.

Please post also the complete output of :
```

sudo apt-get update
sudo apt-get install flashplugin-nonfree

```
Thanks in advance.

pillard@pillard-laptop:~$ sudo apt-get update
[sudo] password for pillard: XXXXXXX
pillard@pillard-laptop:~$ 

(notice the lack of output?)

pillard@pillard-laptop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for pillard: 
pillard@pillard-laptop:~$ 

Same deal, just pukes.  Do I have a faulty install of Ubuntu on my hands?

---

### Post by albinootje on 2009-01-09
> **ppillard said:**
>  pillard@pillard-laptop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for pillard: 
pillard@pillard-laptop:~$ 

Same deal, just pukes.  Do I have a faulty install of Ubuntu on my hands?

Nothing happens ? Weird :(

Please post the complete output of :
```

dmesg
lspci
lsb_release -a

```

And can you do a memtest for your machine from the grub menu ?

When you boot the machine, press escape when grub wants to start.
Then choose memtest86+ and let that work for at least 5 - 10 minutes.

---

### Post by ppillard on 2009-01-11
dmesg (brace yourself):

[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffff800 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffff800 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xfff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to fff0000 @ 7000-d000
[    0.000000] RAMDISK: 0f80f000 - 0ffdfd1b
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP 000F6C30, 0014 (r0 SONY  )
[    0.000000] ACPI: RSDT 0FFFC369, 002C (r1 SONY   Z1       20000222 PTL         0)
[    0.000000] ACPI: FACP 0FFFF765, 0074 (r1 SONY   Z1       20000222 PTL     F4240)
[    0.000000] ACPI: DSDT 0FFFC395, 33D0 (r1   SONY  Z1      20000222 MSFT  1000007)
[    0.000000] ACPI: FACS 0FFFFFC0, 0040
[    0.000000] ACPI: BOOT 0FFFF7D9, 0027 (r1 SONY   Z1       20000222 PTL         1)
[    0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine
[    0.000000] ACPI: DMI detected: Sony
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fff0000
[    0.000000]   low ram: 00000000 - 0fff0000
[    0.000000]   bootmap 00002000 - 00004000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [000f80f000 - 000ffdfd1b]          RAMDISK ==> [000f80f000 - 000ffdfd1b]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fff0
[    0.000000]   HighMem  0x0000fff0 -> 0x0000fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fff0
[    0.000000] On node 0 totalpages: 65423
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 60884 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01241000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e9000
[    0.000000] PM: Registered nosave memory: 00000000000e9000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff80000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64847
[    0.000000] Kernel command line: root=UUID=8b69128c-6b82-4e34-9682-3de5b200b75d ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 496.304 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 246084k/262080k available (2572k kernel code, 15480k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0800000 - 0xff3fe000   ( 747 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004026] Calibrating delay loop (skipped), value calculated using timer frequency.. 992.60 BogoMIPS (lpj=1985216)
[    0.004102] Security Framework initialized
[    0.004131] SELinux:  Disabled at boot.
[    0.004220] AppArmor: AppArmor initialized
[    0.004255] Mount-cache hash table entries: 512
[    0.004885] Initializing cgroup subsys ns
[    0.004902] Initializing cgroup subsys cpuacct
[    0.004915] Initializing cgroup subsys memory
[    0.004971] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004986] CPU: L2 cache: 256K
[    0.005044] Checking 'hlt' instruction... OK.
[    0.021215] SMP alternatives: switching to UP code
[    0.036060] Freeing SMP alternatives: 11k freed
[    0.036077] ACPI: Core revision 20080609
[    0.038248] ACPI: Checking initramfs for custom DSDT
[    1.440684] weird, boot CPU (#0) not listedby the BIOS.
[    1.440700] SMP motherboard not detected.
[    1.440712] Local APIC not detected. Using dummy APIC emulation.
[    1.440723] SMP disabled
[    1.441021] Brought up 1 CPUs
[    1.441034] Total of 1 processors activated (992.60 BogoMIPS).
[    1.441079] CPU0 attaching sched-domain:
[    1.441093]  domain 0: span 0 level CPU
[    1.441105]   groups: 0
[    1.442208] net_namespace: 840 bytes
[    1.442252] Booting paravirtualized kernel on bare hardware
[    1.443250] Time: 21:51:53  Date: 01/10/09
[    1.443370] NET: Registered protocol family 16
[    1.445555] EISA bus registered
[    1.445629] ACPI: bus type pci registered
[    1.462200] PCI: PCI BIOS revision 2.10 entry at 0xfd99e, last bus=1
[    1.462215] PCI: Using configuration type 1 for base access
[    1.470007] ACPI: EC: Look up EC in DSDT
[    1.493499] ACPI: Interpreter enabled
[    1.493516] ACPI: (supports S0 S1 S3 S4 S5)
[    1.493596] ACPI: Using PIC for interrupt routing
[    1.503791] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.571380] ACPI: EC: GPE = 0x9, I/O: command/status = 0x66, data = 0x62
[    1.571396] ACPI: EC: driver started in interrupt mode
[    1.571680] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.571982] PCI: 0000:00:00.0 reg 10 32bit mmio: [40000000, 40ffffff]
[    1.572281] PCI: 0000:00:07.1 reg 20 io port: [fcb0, fcbf]
[    1.572376] PCI: 0000:00:07.2 reg 20 io port: [fc60, fc7f]
[    1.572496] pci 0000:00:07.3: quirk: region 8000-803f claimed by PIIX4 ACPI
[    1.572512] pci 0000:00:07.3: quirk: region 1040-104f claimed by PIIX4 SMB
[    1.572534] pci 0000:00:07.3: PIIX4 devres I PIO at 0398-0399
[    1.572548] pci 0000:00:07.3: PIIX4 devres J PIO at 0398-0399
[    1.572611] PCI: 0000:00:08.0 reg 10 32bit mmio: [fecfe000, fecfe7ff]
[    1.572631] PCI: 0000:00:08.0 reg 14 32bit mmio: [fecfec00, fecfedff]
[    1.572675] PCI: 0000:00:08.0 reg 30 32bit mmio: [0, ffff]
[    1.572747] PCI: 0000:00:09.0 reg 10 32bit mmio: [fecf0000, fecf7fff]
[    1.572766] PCI: 0000:00:09.0 reg 14 io port: [fc00, fc3f]
[    1.572784] PCI: 0000:00:09.0 reg 18 io port: [fcac, fcaf]
[    1.572840] pci 0000:00:09.0: supports D2
[    1.572889] PCI: 0000:00:0a.0 reg 10 32bit mmio: [fece0000, feceffff]
[    1.572908] PCI: 0000:00:0a.0 reg 14 io port: [fca0, fca7]
[    1.572970] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    1.572985] pci 0000:00:0a.0: PME# disabled
[    1.573040] PCI: 0000:00:0b.0 reg 10 32bit mmio: [fecff000, fecfffff]
[    1.573060] PCI: 0000:00:0b.0 reg 14 io port: [fcc0, fcff]
[    1.573078] PCI: 0000:00:0b.0 reg 18 32bit mmio: [fed00000, fedfffff]
[    1.573134] pci 0000:00:0b.0: supports D1
[    1.573143] pci 0000:00:0b.0: supports D2
[    1.573153] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot
[    1.573167] pci 0000:00:0b.0: PME# disabled
[    1.573217] PCI: 0000:00:0c.0 reg 10 32bit mmio: [0, fff]
[    1.573247] pci 0000:00:0c.0: supports D1
[    1.573255] pci 0000:00:0c.0: supports D2
[    1.573266] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.573280] pci 0000:00:0c.0: PME# disabled
[    1.573330] PCI: 0000:00:0d.0 reg 10 32bit mmio: [fecfe800, fecfebff]
[    1.573477] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    1.573497] PCI: 0000:01:00.0 reg 14 32bit mmio: [fe400000, fe7fffff]
[    1.573516] PCI: 0000:01:00.0 reg 18 32bit mmio: [feb00000, febfffff]
[    1.573569] pci 0000:01:00.0: supports D1
[    1.573577] pci 0000:01:00.0: supports D2
[    1.573643] PCI: bridge 0000:00:01.0 32bit mmio: [fe400000, febfffff]
[    1.573659] PCI: bridge 0000:00:01.0 32bit mmio pref: [fd000000, fdffffff]
[    1.573706] bus 00 -> node 0
[    1.573742] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.587252] ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
[    1.587743] ACPI: PCI Interrupt Link [LNKB] (IRQs 9) *0, disabled.
[    1.588320] ACPI: PCI Interrupt Link [LNKC] (IRQs 9) *0, disabled.
[    1.588811] ACPI: PCI Interrupt Link [LNKD] (IRQs 9) *0, disabled.
[    1.589579] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.589777] pnp: PnP ACPI init
[    1.589817] ACPI: bus type pnp registered
[    1.661202] pnp: PnP ACPI: found 13 devices
[    1.661217] ACPI: ACPI bus type pnp unregistered
[    1.661235] PnPBIOS: Disabled by ACPI PNP
[    1.663259] PCI: Using ACPI for IRQ routing
[    1.664419] NET: Registered protocol family 8
[    1.664419] NET: Registered protocol family 20
[    1.664419] NetLabel: Initializing
[    1.664419] NetLabel:  domain hash size = 128
[    1.664419] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.664419] NetLabel:  unlabeled traffic allowed by default
[    1.665700] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.665712]    actual entries 65620
[    1.666254] AppArmor: AppArmor Filesystem Enabled
[    1.666315] ACPI: RTC can wake from S4
[    1.666415] system 00:01: ioport range 0x398-0x399 has been reserved
[    1.666415] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    1.666415] system 00:01: ioport range 0x1040-0x104f has been reserved
[    1.666415] system 00:01: ioport range 0x8000-0x804f could not be reserved
[    1.666415] system 00:02: iomem range 0x100000-0xfffffff could not be reserved
[    1.666415] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[    1.666415] system 00:02: iomem range 0xdc000-0xdffff has been reserved
[    1.666415] system 00:02: iomem range 0xe0000-0xfffff could not be reserved
[    1.666415] system 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[    1.666415] system 00:02: iomem range 0xfff7f600-0xfff7ffff has been reserved
[    1.705109] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.705124] pci 0000:00:01.0:   IO window: disabled
[    1.705140] pci 0000:00:01.0:   MEM window: 0xfe400000-0xfebfffff
[    1.705156] pci 0000:00:01.0:   PREFETCH window: 0x000000fd000000-0x000000fdffffff
[    1.705177] pci 0000:00:0c.0: CardBus bridge, secondary bus 0000:02
[    1.705190] pci 0000:00:0c.0:   IO window: 0x001400-0x0014ff
[    1.705204] pci 0000:00:0c.0:   IO window: 0x001800-0x0018ff
[    1.705219] pci 0000:00:0c.0:   PREFETCH window: 0x20000000-0x23ffffff
[    1.705234] pci 0000:00:0c.0:   MEM window: 0x24000000-0x27ffffff
[    1.705297] pci 0000:00:01.0: power state changed by ACPI to D0
[    1.705340] pci 0000:00:0c.0: power state changed by ACPI to D0
[    1.706592] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[    1.706607] PCI: setting IRQ 9 as level-triggered
[    1.706622] pci 0000:00:0c.0: PCI INT A -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
[    1.706641] pci 0000:00:0c.0: setting latency timer to 64
[    1.706656] bus: 00 index 0 io port: [0, ffff]
[    1.706667] bus: 00 index 1 mmio: [0, ffffffff]
[    1.706677] bus: 01 index 0 mmio: [0, 0]
[    1.706688] bus: 01 index 1 mmio: [fe400000, febfffff]
[    1.706699] bus: 01 index 2 mmio: [fd000000, fdffffff]
[    1.706709] bus: 01 index 3 mmio: [0, 0]
[    1.706721] bus: 02 index 0 io port: [1400, 14ff]
[    1.706731] bus: 02 index 1 io port: [1800, 18ff]
[    1.706742] bus: 02 index 2 mmio: [20000000, 23ffffff]
[    1.706753] bus: 02 index 3 mmio: [24000000, 27ffffff]
[    1.706799] NET: Registered protocol family 2
[    1.707526] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    1.708696] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    1.708908] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    1.709113] TCP: Hash tables configured (established 8192 bind 8192)
[    1.709127] TCP reno registered
[    1.709550] NET: Registered protocol family 1
[    1.710082] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    3.095959]  it is
[    4.729153] Freeing initrd memory: 8003k freed
[    4.729926] Simple Boot Flag at 0x35 set to 0x1
[    4.732086] audit: initializing netlink socket (disabled)
[    4.732149] type=2000 audit(1231624316.732:1): initialized
[    4.757911] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    4.772642] VFS: Disk quotas dquot_6.5.1
[    4.773215] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.773759] msgmni has been set to 496
[    4.774476] io scheduler noop registered
[    4.774491] io scheduler anticipatory registered
[    4.774502] io scheduler deadline registered
[    4.774593] io scheduler cfq registered (default)
[    4.774634] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    4.774745] pci 0000:00:0b.0: Firmware left e100 interrupts enabled; disabling
[    4.774793] pci 0000:01:00.0: Boot video device
[    4.776628] isapnp: Scanning for PnP cards...
[    5.130917] isapnp: No Plug & Play device found
[    5.385864] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    5.386250] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    5.387494] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 8250
[    5.390401] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    5.400603] brd: module loaded
[    5.401010] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    5.401668] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    5.404975] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.405007] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.407236] mice: PS/2 mouse device common for all mice
[    5.408106] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    5.408153] rtc0: alarms up to one month, y3k
[    5.408860] EISA: Probing bus 0 at eisa.0
[    5.408886] Cannot allocate resource for EISA slot 1
[    5.408939] Cannot allocate resource for EISA slot 8
[    5.408949] EISA: Detected 0 cards.
[    5.408962] cpuidle: using governor ladder
[    5.408972] cpuidle: using governor menu
[    5.411850] TCP cubic registered
[    5.411974] Using IPI No-Shortcut mode
[    5.413408] registered taskstats version 1
[    5.413882]   Magic number: 9:287:904
[    5.414086] tty ptyz0: hash matches
[    5.414290] rtc_cmos 00:04: setting system clock to 2009-01-10 21:51:57 UTC (1231624317)
[    5.414306] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.414316] EDD information not available.
[    5.416218] Freeing unused kernel memory: 424k freed
[    5.416478] Write protecting the kernel text: 2576k
[    5.416629] Write protecting the kernel read-only data: 936k
[    5.439887] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    6.323984] fuse init (API version 7.9)
[    6.503470] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    6.503749] processor ACPI0007:00: registered as cooling_device0
[    6.503773] ACPI: Processor [CPU0] (supports 8 throttling states)
[    6.524889] thermal LNXTHERM:01: registered as thermal_zone0
[    6.528428] ACPI: Thermal Zone [ATF0] (44 C)
[    9.230442] usbcore: registered new interface driver usbfs
[    9.230539] usbcore: registered new interface driver hub
[    9.282284] No dock devices found.
[    9.424790] usbcore: registered new device driver usb
[    9.831836] SCSI subsystem initialized
[    9.852888] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    9.852903] e100: Copyright(c) 1999-2006 Intel Corporation
[    9.867927] e100 0000:00:0b.0: power state changed by ACPI to D0
[    9.869221] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    9.869240] e100 0000:00:0b.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    9.892149] e100 0000:00:0b.0: PME# disabled
[    9.895424] USB Universal Host Controller Interface driver v3.0
[    9.965445] e100: eth0: e100_probe: addr 0xfecff000, irq 9, MAC addr 08:00:46:06:78:1a
[    9.965676] uhci_hcd 0000:00:07.2: power state changed by ACPI to D0
[    9.966915] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    9.966934] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    9.966964] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    9.967154] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    9.967212] uhci_hcd 0000:00:07.2: irq 9, io base 0x0000fc60
[    9.967907] usb usb1: configuration #1 chosen from 1 choice
[    9.968113] hub 1-0:1.0: USB hub found
[    9.968157] hub 1-0:1.0: 2 ports detected
[   10.134189] ohci1394 0000:00:08.0: power state changed by ACPI to D0
[   10.134216] ohci1394 0000:00:08.0: enabling device (0000 -> 0002)
[   10.134245] ohci1394 0000:00:08.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[   10.187306] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[fecfe000-fecfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   10.201365] libata version 3.00 loaded.
[   10.253345] ata_piix 0000:00:07.1: version 2.12
[   10.255997] scsi0 : ata_piix
[   10.256812] scsi1 : ata_piix
[   10.257828] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xfcb0 irq 14
[   10.257843] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xfcb8 irq 15
[   10.420689] ata1.00: ATA-6: ST9808211A, 8.03, max UDMA/100
[   10.420707] ata1.00: 156301488 sectors, multi 16: LBA48 
[   10.436623] ata1.00: configured for UDMA/33
[   10.592770] scsi 0:0:0:0: Direct-Access     ATA      ST9808211A       8.03 PQ: 0 ANSI: 5
[   11.496654] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603004f6e49]
[   12.637338] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   12.720894] Driver 'sd' needs updating - please use bus_type methods
[   12.721329] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   12.721426] sd 0:0:0:0: [sda] Write Protect is off
[   12.721441] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.721608] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.721937] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   12.722028] sd 0:0:0:0: [sda] Write Protect is off
[   12.722043] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.722209] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.722234]  sda:Marking TSC unstable due to TSC halts in idle
[   12.743639]  sda1 sda2 < sda5 >
[   12.763995] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.204073] Clocksource tsc unstable (delta = -230375947 ns)
[   13.234378] PM: Starting manual resume from disk
[   13.234397] PM: Resume from partition 8:5
[   13.234406] PM: Checking hibernation image.
[   13.234892] PM: Resume from disk failed.
[   13.359125] EXT3-fs: INFO: recovery required on readonly filesystem.
[   13.359141] EXT3-fs: write access will be enabled during recovery.
[   16.512575] kjournald starting.  Commit interval 5 seconds
[   16.512644] EXT3-fs: sda1: orphan cleanup on readonly fs
[   16.512672] ext3_orphan_cleanup: deleting unreferenced inode 4136984
[   16.512781] EXT3-fs: sda1: 1 orphan inode deleted
[   16.512792] EXT3-fs: recovery complete.
[   16.522829] EXT3-fs: mounted filesystem with ordered data mode.
[   25.862106] udevd version 124 started
[   30.088950] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.612547] Linux agpgart interface v0.103
[   30.743192] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.954990] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[   31.957454] agpgart-intel 0000:00:00.0: AGP aperture is 16M @ 0x40000000
[   31.962998] piix4_smbus 0000:00:07.3: SMBus Host Controller at 0x1040, revision 0
[   32.035609] Yenta: CardBus bridge found at 0000:00:0c.0 [104d:8082]
[   32.173036] Yenta: ISA IRQ mask 0x08b8, PCI irq 9
[   32.173051] Socket status: 30000819
[   32.769605] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   32.868130] pccard: PCMCIA card inserted into slot 0
[   33.058881] udev: renamed network interface eth0 to eth1
[   33.449884] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   33.464174] ACPI: Power Button (CM) [PWRB]
[   35.259848] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input4
[   35.281152] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input5
[   37.627169] parport_pc 00:0c: reported by Plug and Play ACPI
[   37.627260] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   38.225937] sony-laptop: Sony Programmable IO Control Driver v0.6.
[   38.225965] sony-laptop: detected Type1 model
[   38.262635] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0f/SNY6001:00/input/input6
[   38.272601] input: Sony Vaio Jogdial as /devices/virtual/input/input7
[   38.285054] sony-laptop: device allocated minor is 60
[   38.291005] sony-laptop: Sony Notebook Control Driver v0.6.
[   39.360005] irda_init()
[   39.360103] NET: Registered protocol family 23
[   39.570848] nsc_ircc_pnp_probe() : From PnP, found firbase 0x3E8 ; irq 10 ; dma 0.
[   39.570932] nsc-ircc, chip->init
[   39.570945] nsc-ircc, Found chip at base=0x398
[   39.570984] nsc-ircc, driver loaded (Dag Brattli)
[   39.571009] nsc_ircc_open(), can't get iobase of 0x3e8
[   39.571042] nsc-ircc, Found chip at base=0x398
[   39.571080] nsc-ircc, driver loaded (Dag Brattli)
[   39.571093] nsc_ircc_open(), can't get iobase of 0x3e8
[   39.577281] nsc-ircc 00:0b: disabled
[   40.440005] ACPI: AC Adapter [ACAD] (on-line)
[   40.487857] ACPI: Battery Slot [BAT1] (battery present)
[   41.440412] Yamaha DS-1 PCI 0000:00:09.0: enabling device (0006 -> 0007)
[   41.441645] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   41.441664] Yamaha DS-1 PCI 0000:00:09.0: PCI INT A -> Link[LNKC] -> GSI 9 (level, low) -> IRQ 9
[   41.444172] firmware: requesting yamaha/ds1_dsp.fw
[   45.327915] cs: IO port probe 0x100-0x3af: clean.
[   45.330188] cs: IO port probe 0x3e0-0x4ff: clean.
[   45.331217] cs: IO port probe 0x820-0x8ff: clean.
[   45.332145] cs: IO port probe 0xc00-0xcf7: clean.
[   45.333622] cs: IO port probe 0xa00-0xaff: clean.
[   45.334620] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   45.341488] pcmcia: registering new device pcmcia0.0
[   47.418112] firmware: requesting yamaha/ds1e_ctrl.fw
[   48.008940] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   48.031269] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   48.267707] eth0: Hardware identity 800c:0000:0001:0000
[   48.267851] eth0: Station identity  001f:0005:0001:0003
[   48.267865] eth0: Firmware determined as Intersil 1.3.5
[   48.267876] eth0: Ad-hoc demo mode supported
[   48.267886] eth0: IEEE standard IBSS ad-hoc mode supported
[   48.267895] eth0: WEP supported, 104-bit key
[   48.267994] eth0: MAC address 00:05:5d:5b:d5:85
[   48.268136] eth0: Station name "Prism  I"
[   48.268802] eth0: ready
[   48.271281] eth0: orinoco_cs at 0.0, irq 3, io 0x0100-0x013f
[   48.365760] ieee80211_crypt: registered algorithm 'NULL'
[   48.498234] udev: renamed network interface eth0 to eth2
[   49.851775] lp0: using parport0 (interrupt-driven).
[   50.342624] Adding 2931820k swap on /dev/sda5.  Priority:-1 extents:1 across:2931820k
[   51.077836] EXT3 FS on sda1, internal journal
[   53.085021] type=1505 audit(1231624365.639:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3829
[   54.089979] type=1505 audit(1231624366.643:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3834
[   54.091127] type=1505 audit(1231624366.643:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3834
[   54.527100] ip_tables: (C) 2000-2006 Netfilter Core Team
[   56.677728] ACPI: WMI: Mapper loaded
[   60.630404] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   60.843101] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   60.843133] apm: overridden by ACPI.
[   61.258955] ppdev: user-space parallel port driver
[   62.182157] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   62.187059] sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers)
[   62.187144] sonypi: ioport 0x1080 busy, using sony-laptop? if not use check_ioport=0
[   62.187160] sonypi: failed to request ioports
[   62.204101] sonypi: probe of sonypi failed with error -16
[   64.428534] ttyS2: LSR safety check engaged!
[   64.975088] Bluetooth: Core ver 2.13
[   64.982795] NET: Registered protocol family 31
[   64.982823] Bluetooth: HCI device and connection manager initialized
[   64.982838] Bluetooth: HCI socket layer initialized
[   65.102105] Bluetooth: L2CAP ver 2.11
[   65.102138] Bluetooth: L2CAP socket layer initialized
[   65.199766] Bluetooth: RFCOMM socket layer initialized
[   65.200961] Bluetooth: RFCOMM TTY layer initialized
[   65.200992] Bluetooth: RFCOMM ver 1.10
[   65.211017] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   65.211043] Bluetooth: BNEP filters: protocol multicast
[   65.419140] Bridge firewalling registered
[   65.424367] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   65.507525] Bluetooth: SCO (Voice Link) ver 0.6
[   65.507555] Bluetooth: SCO socket layer initialized
[   69.810359] eth2: New link status: Disconnected (0002)
[   70.050275] NET: Registered protocol family 17
[   70.165701] eth2: New link status: Connected (0001)
[  100.683099] eth2: New link status: Disconnected (0002)
[  101.264484] eth2: New link status: Connected (0001)
[  179.895803] NET: Registered protocol family 10
[  179.903505] lo: Disabled Privacy Extensions
[  179.909260] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  183.104744] ppdev0: registered pardevice
[  183.243748] ppdev0: unregistered pardevice
[  184.564419] ppdev0: registered pardevice
[  184.616160] ppdev0: unregistered pardevice
[  184.846717] ttyS2: LSR safety check engaged!
[  184.846792] type=1503 audit(1231624495.231:5): operation="capable" name="sys_admin" pid=5435 profile="/usr/sbin/cupsd"
[  187.929034] ppdev0: registered pardevice
[  187.976691] ppdev0: unregistered pardevice
[  190.720062] eth2: no IPv6 routers present
pillard@pillard-laptop:~$ 

lspci: 00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 FireWire (IEEE 1394): Sony Corporation CXD3222 i.LINK Controller (rev 02)
00:09.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
00:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem (Mob WorldW SmartDAA) (rev 01)
00:0b.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
00:0c.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
00:0d.0 FLASH memory: Sony Corporation Memory Stick Controller (rev 01)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
pillard@pillard-laptop:~$ 

and finally - lsb_release -a:

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
pillard@pillard-laptop:~$ 

Will do the memtest now....

---

### Post by ppillard on 2009-01-11
Tried to initiate memtest, but escape just took me into my bios setup.  Question:  this is an old machine with only 256 megs o' RAM.  Could that be my problem?

---

### Post by Pumalite on 2009-01-11
Try Xubuntu Alternate CD
If not; Puppy or DSL

---

### Post by albinootje on 2009-01-11
> **ppillard said:**
> Tried to initiate memtest, but escape just took me into my bios setup.  Question:  this is an old machine with only 256 megs o' RAM.  Could that be my problem?

You need to press "escape" the moment you see the Grub boot menu "press escape" line.
Now you've probably pressed "escape" too early.

And 256 Mb of RAM should be fine. At least 
```

sudo apt-get update

```
should show something, not nothing at all.

From you dmesg output, afaik, there's no real sign about BIOS bugs, or other serious problems.

---

### Post by ppillard on 2009-01-11
Got the memtest to run.  I let it run for a full 30 minutes.  Wasn't really sure what I was looking for, but there were no crashes or error messages.

---

### Post by albinootje on 2009-01-11
> **ppillard said:**
> Got the memtest to run.  I let it run for a full 30 minutes.  Wasn't really sure what I was looking for, but there were no crashes or error messages.

OK. That's good news!

---

### Post by Pumalite on 2009-01-11
memtest; if one really wants to know for sure; should run 8 to 10 HRS.

---

### Post by ppillard on 2009-01-12
Do you guys think I should try re-installing ubuntu?  What is the xbuntu alternate cd, puppy or dsl?

---

### Post by albinootje on 2009-01-12
> **ppillard said:**
> Do you guys think I should try re-installing ubuntu?  

Is it possible for you to add more RAM memory in your machine ?
At least a total of 512 Mb is more pleasant to work with.

Although it's a mystery to me why your installation is not working well :(
> 
What is the xbuntu alternate cd, puppy or dsl?

Xubuntu alternate installation cdrom is a text based installation cdrom for Xubuntu in cases where you have problems with getting the GUI working automatically, or if you don't have so much RAM memory.

Puppy Linux : [http://en.wikipedia.org/wiki/Puppy_Linux](http://en.wikipedia.org/wiki/Puppy_Linux)

DSL : [http://en.wikipedia.org/wiki/Damn_Small_Linux](http://en.wikipedia.org/wiki/Damn_Small_Linux)

---

