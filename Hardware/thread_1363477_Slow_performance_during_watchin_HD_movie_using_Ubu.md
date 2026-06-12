---
title: "Slow performance during watchin HD movie using Ubuntu 9.10"
date: 2009-12-24
forum: Hardware
---

### Post by RisingForce on 2009-12-24
Dear Friends;

I have a CPU problem while watching HD Movie. Visualization and Audio is not sychronous as well. One of cpu core idle decreases to %0 and another core is not as much as high cpu usage core. Usage can be swithced between cores. 
Do you have any idea about this performance bottleneck?

My Hw info is attached as following:

cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 2003.000
cache size	: 6144 KB
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
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5999.87
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 10
cpu MHz		: 3003.000
cache size	: 6144 KB
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
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5999.29
clflush size	: 64
power management:





cat /proc/meminfo 
MemTotal:        2061092 kB
MemFree:           53496 kB
Buffers:          645572 kB
Cached:           736880 kB
SwapCached:         1952 kB
Active:           744056 kB
Inactive:        1115328 kB
Active(anon):     361056 kB
Inactive(anon):   137644 kB
Active(file):     383000 kB
Inactive(file):   977684 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       1187272 kB
HighFree:           2852 kB
LowTotal:         873820 kB
LowFree:           50644 kB
SwapTotal:       3903752 kB
SwapFree:        3895500 kB
Dirty:                56 kB
Writeback:             0 kB
AnonPages:        475164 kB
Mapped:           128932 kB
Slab:              36428 kB
SReclaimable:      24948 kB
SUnreclaim:        11480 kB
PageTables:         6280 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     4934296 kB
Committed_AS:    1227240 kB
VmallocTotal:     122880 kB
VmallocUsed:       21916 kB
VmallocChunk:      98688 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       86008 kB
DirectMap4M:      823296 kB




lshw output:




    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2012MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 3003MHz
          capacity: 3003MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:c000(size=4096) memory:fe800000-fe8fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV770 [Radeon HD 4850]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:28 memory:d0000000-dfffffff(prefetchable) memory:fe8e0000-fe8effff ioport:c000(size=256) memory:fe8c0000-fe8dffff(prefetchable)
           *-multimedia
                description: Audio device
                product: HD48x0 audio
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:fe8fc000-fe8fffff
        *-usb:0
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:b800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:b880(size=32)
        *-usb:2
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:bc00(size=32)
        *-usb:3
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fe7ffc00-fe7fffff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:fe7f8000-fe7fbfff
        *-pci:1
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:fdf00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:e000(size=4096) memory:fea00000-feafffff
           *-ide
                description: IDE interface
                product: 88SE6121 SATA II Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b2
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list
                configuration: driver=pata_marvell latency=0
                resources: irq:16 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) memory:feaffc00-feafffff
        *-pci:3
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:d000(size=4096) memory:fe900000-fe9fffff
           *-network
                description: Ethernet interface
                product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: b0
                serial: 00:22:15:7a:3e:2c
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 multicast=yes
                resources: irq:29 memory:fe9c0000-fe9fffff ioport:dc00(size=128)
        *-usb:4
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:b080(size=32)
        *-usb:5
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b400(size=32)
        *-usb:6
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:b480(size=32)
        *-usb:7
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe7ff800-fe7ffbff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:feb00000-febfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323
                vendor: Agere Systems
                physical id: 3
                bus info: pci@0000:05:03.0
                version: 70
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=24 mingnt=12
                resources: irq:19 memory:febff000-febfffff
        *-isa
             description: ISA bridge
             product: 82801JIR (ICH10R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801JI (ICH10 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:a000(size=8) ioport:9c00(size=4) ioport:9880(size=8) ioport:9800(size=4) ioport:9480(size=16) ioport:9400(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe7ff400-fe7ff4ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 82801JI (ICH10 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:b000(size=8) ioport:ac00(size=4) ioport:a880(size=8) ioport:a800(size=4) ioport:a480(size=16) ioport:a400(size=16)
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan2
       serial: 00:0e:2e:f8:8a:15
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.6 multicast=yes wireless=IEEE 802.11bg

---

