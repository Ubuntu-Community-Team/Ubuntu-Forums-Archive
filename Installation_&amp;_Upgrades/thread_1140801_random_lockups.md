---
title: "random lockups"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by jag7720 on 2009-04-27
I am running 9.04 and I am getting random lockups

I have ran nothing but Ubuntu on this machine since it was bought new.  Everything works great.. no issues at al/.

Now I upgraded to 9.04 and bam!... all these random lockups.  No errors. It just freezes.
 
Anyone know what is going on?


```
 cat /etc/issue
Ubuntu 9.04 \n \l

```


here is my hardware

```
cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 43
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 1
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good pni lahf_lm cmp_legacy
bogomips	: 2003.96
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 43
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 1
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good pni lahf_lm cmp_legacy
bogomips	: 2003.96
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp


```


```
cat /proc/meminfo 
MemTotal:        1011460 kB
MemFree:           11308 kB
Buffers:           30524 kB
Cached:           407464 kB
SwapCached:         4384 kB
Active:           404120 kB
Inactive:         487424 kB
Active(anon):     223812 kB
Inactive(anon):   235004 kB
Active(file):     180308 kB
Inactive(file):   252420 kB
Unevictable:           8 kB
Mlocked:               8 kB
SwapTotal:       2048248 kB
SwapFree:        2026576 kB
Dirty:               176 kB
Writeback:             0 kB
AnonPages:        449544 kB
Mapped:            55300 kB
Slab:              55340 kB
SReclaimable:      40064 kB
SUnreclaim:        15276 kB
PageTables:        20304 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2553976 kB
Committed_AS:     942120 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      106880 kB
VmallocChunk:   34359627771 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       25536 kB
DirectMap2M:     1021952 kB
```

```

sudo lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping Enable+ Fixed-

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] #00 [00fe]
	Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa000000-fcffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: [40] Subsystem: nVidia Corporation Device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping Enable+ Fixed-

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f03c:2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fd00 [size=16]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at f800 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at f300 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=128
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff
	Capabilities: [b8] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at f200 [size=8]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
	Subsystem: eVga.com. Corp. Device c428
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 2a3e
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at fddff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs Device 0051
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at df00 [size=32]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

03:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
	Subsystem: Creative Labs Device 0040
	Flags: bus master, medium devsel, latency 32
	I/O ports at de00 [size=8]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp

03:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10)
	Subsystem: Creative Labs Device 0010
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fddfe000 (32-bit, non-prefetchable) [size=2K]
	Memory at fddf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:0a.0 Communication controller: Agere Systems Device 0620
	Subsystem: Agere Systems Device 0620
	Flags: bus master, medium devsel, latency 32, IRQ 255
	I/O ports at dc00 [size=256]
	Capabilities: [f8] Power Management version 3



```

---

### Post by jag7720 on 2009-04-28
bump

---

### Post by waldrepdebater on 2009-04-29
I've got the exact same issue on my laptop.  About a third of the times I boot it will just freeze right after the gnome panel background displays, but before the desktop background/icons/AWN.  Other times I will be just staring at a pdf file or a web page and everything just freezes up.  I used 8.10 since it came out and had to do less than five forced reboots.  In the last week I've had to do twenty or more with 9.04...

Everything else about 9.04 is perfect.  The OS is more stable in other aspects, runs smoother, and boots faster.  However this random freezing issue is starting to get irritating.

EDIT: Some threads reporting a similar problem:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1138180](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1138180)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1134920](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1134920)

Specs:

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2060  @ 1.60GHz
stepping	: 12
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr pdcm
bogomips	: 3192.12
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2060  @ 1.60GHz
stepping	: 12
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr pdcm
bogomips	: 3192.10
clflush size	: 64
power management:
```

```
cat /proc/meminfo
MemTotal:        1017060 kB
MemFree:          394272 kB
Buffers:           56260 kB
Cached:           266144 kB
SwapCached:            0 kB
Active:           383836 kB
Inactive:         160868 kB
Active(anon):     294816 kB
Inactive(anon):        8 kB
Active(file):      89020 kB
Inactive(file):   160860 kB
Unevictable:           8 kB
Mlocked:               8 kB
HighTotal:        133640 kB
HighFree:            224 kB
LowTotal:         883420 kB
LowFree:          394048 kB
SwapTotal:       1116476 kB
SwapFree:        1116476 kB
Dirty:               152 kB
Writeback:             0 kB
AnonPages:        222408 kB
Mapped:            67384 kB
Slab:              31632 kB
SReclaimable:      23452 kB
SUnreclaim:         8180 kB
PageTables:         2880 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1625004 kB
Committed_AS:     692412 kB
VmallocTotal:     122880 kB
VmallocUsed:        5796 kB
VmallocChunk:     115700 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       53240 kB
DirectMap4M:      851968 kB

```

Not sure what this part means but I hope it helps...

```
sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 5088 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0200000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 2
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 0
	Memory at d0180000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d0240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0090
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0090
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0090
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0090
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 50a0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 50c0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 50e0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 5400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d0444000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0000000-d00fffff
	Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
	Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device 0090

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 5440 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: medium devsel, IRQ 10
	I/O ports at 5420 [size=32]
	Kernel modules: i2c-i801

06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 64, IRQ 21
	Memory at d0010000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: b44
	Kernel modules: b44

06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0418
	Flags: bus master, medium devsel, latency 168, IRQ 22
	Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at d0012000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 00002000-000020ff
	I/O window 1: 00002400-000024ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: medium devsel, IRQ 11
	Memory at d0013000 (32-bit, non-prefetchable) [disabled] [size=128]
	Capabilities: [80] Power Management version 2

06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: medium devsel, IRQ 17
	Memory at d0013400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: medium devsel, IRQ 11
	Memory at d0013800 (32-bit, non-prefetchable) [disabled] [size=128]
	Capabilities: [80] Power Management version 2

06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: medium devsel, IRQ 17
	Memory at d0013100 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

```

[

---

### Post by jag7720 on 2009-04-29
I downgraded my nvidia driver from 180 to 173 and the issue seems to have subsided.  I did a lot of work trying to get it to lockup but it didn't and then I let it sit all night (it locked up just sitting too) and it was still running.

One thing I noticed with the 180 driver was the screen would flicker a lot and have a hard time re-writing.

I will update if the issue returns.

---

### Post by m2.g5ru6y7s on 2009-04-29
Maybe it has to do with this reported bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/332563](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/332563)

---

### Post by mkpelletier78 on 2009-05-09
Well, I have an ATI HD3650 and I am using the open source radeon drivers and I STILL get lockups.  I would use the proprietary installer, except that too toasted my system and rendered X useless.  In any case, your particular problem my be related to Nvidia, but mine is clearly not.  Nevertheless, I have found that generally any system instability is caused by graphics problems.  And this has been demonstrably true for Nvidia, ATI, and Intel.  Maybe we need Matrox cards back?!?

I must say, so far Jaunty is proving to be a serious disappointment and extremely unstable.

---

