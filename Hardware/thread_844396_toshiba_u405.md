---
title: "toshiba u405"
date: 2008-06-29
forum: Hardware
---

### Post by ms.shams on 2008-06-29
hi,
i want to buy toshiba satellite u405. but i don't know that this laptop works fine with ubuntu?
can anyone help me?

---

### Post by Mikecore on 2008-06-29
> **ms.shams said:**
> hi,
i want to buy toshiba satellite u405. but i don't know that this laptop works fine with ubuntu?
can anyone help me?

I have two toshiba laptops a U205 and a M55. Both worked right out of the box with Ubuntu. I went to the toshiba website and looked at the u405 system specs and you should be fine. I have found that toshiba laptops work great with linux because of the intel chips which are used in them, are well supported.

---

### Post by lisati on 2008-06-29
I have a Toshiba A100, which can be used with Ubuntu.

There are a few of us here on the forums who use Toshiba laptops, so feel free to ask questions.

---

### Post by wlan0 on 2008-07-28
> **ms.shams said:**
> hi,
i want to buy toshiba satellite u405. but i don't know that this laptop works fine with ubuntu?
can anyone help me?

works excelent....

currently using the u405 nice laptop!!! and nice price...

only thing... still looking for help on finger print reader to work

everything else work perfect better than windows vista :lolflag:

well if you have questions about the toshiba u405 and ubuntu let me know..

---

### Post by ms.shams on 2008-07-28
i bought one of this laptop. that is nice, thiny, and powerful. i installing ubuntu on it before booting vista ;) and ubuntu detects all of drivers barring ethernet and fingerprint. i run an script cause that ubuntu detects ethernet. but i can't work with fingerprint still. can anyone help me plz?

---

### Post by Zer0Nin3r on 2008-10-16
I bought a Toshiba Satellite U405D-2852.  I love it and everything works with the exception of both wired and wireless networking.

Reason?  The laptop features a wireless Atheros AR5007EG card and a Marvell Yukon 88E8040T ethernet controller both of which are unsupported in 8.04.

Hope this changes in 8.10

---

### Post by sdcope on 2008-10-16
I installed it on a u205, and everything works but the sound.

---

### Post by bizbirije on 2008-10-20
> **wlan0 said:**
> works excelent....

currently using the u405 nice laptop!!! and nice price...

only thing... still looking for help on finger print reader to work

everything else work perfect better than windows vista :lolflag:

well if you have questions about the toshiba u405 and ubuntu let me know..

I also have a Toshiba U405, works fine except for the mic, Wlan0 can you help me with the problem

Thanks:)

---

### Post by wlan0 on 2008-10-21
> **bizbirije said:**
> I also have a Toshiba U405, works fine except for the mic, Wlan0 can you help me with the problem

Thanks:)

ofcourse!! what is the exact model? u405xxx?

i´ll do my best mine it is from latin america so i got a couple of things diferent from yours... but we can try... maybe the same...

regards

Daniel.):P

---

### Post by bizbirije on 2008-10-29
Sorry Daniel, I was out for a week but now I'm back.

The exact model is Toshiba Satellite U405 - SP2803.

Thanks in advance.

---

### Post by pashabear on 2008-11-11
Zer0Nin3r, I have that same model (U405D-S2852), same problems (wired & wireless not working).  I've used Mint Linux, which has a nice ndis wrapper utility (it's built on Ubuntu), I found using the 64 bit release with the 64 bit driver it worked ok.  But detection isn't great.  The new releases seem to think they have a driver for the wireless, but it doesn't show up when you click on the networking icon.  Can anyone help?
Thanks
pb

---

### Post by elkuco009 on 2009-01-03
Do you still need help with your WLAN0???

I am pretty new into the UBUNTU world. But, I just fixed the problem of the WIFI so if you need help. Just let me know.

---

### Post by lalbertme on 2009-01-09
I also have the u405 sp2803 model, but the radio tuner do not work, any help?

```
[root@mortylap ~]# lsmod
Module                  Size  Used by
fuse                   49436  2 
i915                   53508  2 
drm                   158260  3 i915
bridge                 43668  0 
stp                     6148  1 bridge
bnep                   14848  2 
sco                    12932  2 
l2cap                  21504  3 bnep
bluetooth              48608  5 bnep,sco,l2cap
vboxnetflt             72784  0 
vboxdrv                95048  1 vboxnetflt
sunrpc                155924  3 
ip6t_REJECT             7296  2 
nf_conntrack_ipv6      15864  2 
ip6table_filter         6400  1 
ip6_tables             14736  1 ip6table_filter
ipv6                  230132  28 ip6t_REJECT,nf_conntrack_ipv6
cpufreq_ondemand        9996  1 
acpi_cpufreq           12172  1 
dm_multipath           17164  0 
uinput                 10624  0 
snd_hda_intel         395544  2 
snd_seq_dummy           6660  0 
snd_seq_oss            30364  0 
arc4                    5760  2 
snd_seq_midi_event      9600  1 snd_seq_oss
snd_seq                48320  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
ecb                     6528  2 
crypto_blkcipher       18052  1 ecb
snd_seq_device          9996  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            41600  0 
uvcvideo               51720  0 
snd_mixer_oss          16896  1 snd_pcm_oss
iwlagn                139268  0 
sdhci_pci              10624  0 
iwlcore               116804  1 iwlagn
snd_pcm                64772  2 snd_hda_intel,snd_pcm_oss
sdhci                  17540  1 sdhci_pci
compat_ioctl32          5120  1 uvcvideo
iTCO_wdt               13732  0 
videodev               32000  1 uvcvideo
mmc_core               43676  1 sdhci
snd_timer              21896  2 snd_seq,snd_pcm
firewire_ohci          22532  0 
iTCO_vendor_support     6916  1 iTCO_wdt
pcspkr                  6272  0 
v4l1_compat            15876  2 uvcvideo,videodev
snd_page_alloc         11144  2 snd_hda_intel,snd_pcm
firewire_core          35616  1 firewire_ohci
snd_hwdep              10372  1 snd_hda_intel
mac80211              173668  2 iwlagn,iwlcore
snd                    51768  14 snd_hda_intel,snd_seq_dummy,snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
i2c_i801               12048  0 
crc_itu_t               5760  1 firewire_core
i2c_core               21396  2 drm,i2c_i801
sky2                   42628  0 
rfkill                 11288  2 iwlcore
serio_raw               8836  0 
joydev                 12736  0 
cfg80211               23816  3 iwlagn,iwlcore,mac80211
soundcore               9416  1 snd
input_polldev           7176  0 
wmi                     9768  0 
video                  20244  0 
output                  6528  1 video
```

```
[root@mortylap ~]# dmesg
Initializing cgroup subsys cpuset
Initializing cgroup subsys cpu
Linux version 2.6.27.9-159.fc10.i686 (mockbuild@x86-3.fedora.phx.redhat.com) (gcc version 4.3.2 20081105 (Red Hat 4.3.2-7) (GCC) ) #1 SMP Tue Dec 16 15:12:04 EST 2008
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
 BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
 BIOS-e820: 00000000bf6d0000 - 00000000bf6e3000 (ACPI NVS)
 BIOS-e820: 00000000bf6e3000 - 00000000c0000000 (reserved)
 BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
 BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
 BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
 BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
DMI present.
last_pfn = 0xbf6d0 max_arch_pfn = 0x100000
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
kernel direct mapping tables up to 38000000 @ 7000-c000
Using x86 segment limits to approximate NX protection
RAMDISK: 37c70000 - 37fef574
ACPI: RSDP 000F76A0, 0024 (r2 TOSQCI)
ACPI: XSDT BF6D2CAE, 0074 (r1 TOSQCI TOSQCI00  6040000  LTP        0)
ACPI: FACP BF6DFC92, 00F4 (r3 TOSQCI TOSQCI00  6040000 ALAN        1)
ACPI: DSDT BF6D4136, BAE8 (r2 TOSQCI N.Jersey  6040000 MSFT  3000001)
ACPI: FACS BF6E2FC0, 0040
ACPI: HPET BF6DFD86, 0038 (r1 TOSQCI TOSQCI00  6040000 LOHR       5A)
ACPI: MCFG BF6DFDBE, 003C (r1 TOSQCI TOSQCI00  6040000 LOHR       5A)
ACPI: APIC BF6DFDFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
ACPI: BOOT BF6DFE62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
ACPI: SLIC BF6DFE8A, 0176 (r1 TOSQCI TOSQCI00  6040000  LTP        0)
ACPI: SSDT BF6D3E89, 02AD (r1 SataRe SataAhci     1000 INTL 20061109)
ACPI: SSDT BF6D32AE, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20061109)
ACPI: SSDT BF6D3208, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20061109)
ACPI: SSDT BF6D2D22, 04E6 (r1  PmRef    CpuPm     3000 INTL 20061109)
ACPI: DMI detected: Toshiba
2166MB HIGHMEM available.
896MB LOWMEM available.
  mapped low ram: 0 - 38000000
  low ram: 00000000 - 38000000
  bootmap 00008000 - 0000f000
(9 early reservations) ==> bootmem [0000000000 - 0038000000]
  #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
  #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
  #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
  #3 [0000400000 - 000097212c]    TEXT DATA BSS ==> [0000400000 - 000097212c]
  #4 [0037c70000 - 0037fef574]          RAMDISK ==> [0037c70000 - 0037fef574]
  #5 [0000973000 - 0000977000]    INIT_PG_TABLE ==> [0000973000 - 0000977000]
  #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
  #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
  #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
found SMP MP-table at [c00f7750] 000f7750
Zone PFN ranges:
  DMA      0x00000000 -> 0x00001000
  Normal   0x00001000 -> 0x00038000
  HighMem  0x00038000 -> 0x000bf6d0
Movable zone start PFN for each node
early_node_map[2] active PFN ranges
    0: 0x00000000 -> 0x0000009f
    0: 0x00000100 -> 0x000bf6d0
On node 0 totalpages: 783983
free_area_init_node: node 0, pgdat c07f3a80, node_mem_map c1000000
  DMA zone: 3967 pages, LIFO batch:0
  Normal zone: 223520 pages, LIFO batch:31
  HighMem zone: 550370 pages, LIFO batch:31
Using APIC driver default
ACPI: PM-Timer IO Port: 0x1008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
ACPI: HPET id: 0x8086a201 base: 0xfed00000
Using ACPI (MADT) for SMP configuration information
SMP: Allowing 2 CPUs, 0 hotplug CPUs
mapped APIC to ffffb000 (fee00000)
mapped IOAPIC to ffffa000 (fec00000)
PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
PERCPU: Allocating 41372 bytes of per cpu data
NR_CPUS: 32, nr_cpu_ids: 2, nr_node_ids 1
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777857
Kernel command line: ro root=/dev/VolGroup00/LogVol00 rhgb quiet
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
CPU 0 irqstacks, hard=c089f000 soft=c087f000
PID hash table entries: 4096 (order: 12, 16384 bytes)
Extended CMOS year: 2000
TSC: PIT calibration confirmed by PMTIMER.
TSC: using PIT calibration value
Detected 1994.976 MHz processor.
Console: colour VGA+ 80x25
console [tty0] enabled
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 3100284k/3136320k available (2738k kernel code, 34728k reserved, 1418k data, 412k init, 2218816k highmem)
virtual kernel memory layout:
    fixmap  : 0xffc57000 - 0xfffff000   (3744 kB)
    pkmap   : 0xff400000 - 0xff800000   (4096 kB)
    vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
    lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
      .init : 0xc0815000 - 0xc087c000   ( 412 kB)
      .data : 0xc06acb96 - 0xc080f618   (1418 kB)
      .text : 0xc0400000 - 0xc06acb96   (2738 kB)
Checking if this processor honours the WP bit even in supervisor mode...Ok.
CPA: page pool initialized 1 of 1 pages preallocated
SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
hpet clockevent registered
Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.95 BogoMIPS (lpj=1994976)
Security Framework initialized
SELinux:  Initializing.
SELinux:  Starting in permissive mode
Mount-cache hash table entries: 512
Initializing cgroup subsys ns
Initializing cgroup subsys cpuacct
Initializing cgroup subsys devices
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
using mwait in idle threads.
Checking 'hlt' instruction... OK.
ACPI: Core revision 20080609
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
CPU 1 irqstacks, hard=c08a0000 soft=c0880000
Booting processor 1/1 ip 6000
Initializing CPU#1
Calibrating delay using timer specific routine.. 3989.80 BogoMIPS (lpj=1994901)
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 1
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#1.
x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Brought up 2 CPUs
Total of 2 processors activated (7979.75 BogoMIPS).
sizeof(vma)=84 bytes
sizeof(page)=32 bytes
sizeof(inode)=340 bytes
sizeof(dentry)=132 bytes
sizeof(ext3inode)=492 bytes
sizeof(buffer_head)=56 bytes
sizeof(skbuff)=184 bytes
sizeof(task_struct)=3268 bytes
CPU0 attaching sched-domain:
 domain 0: span 0-1 level MC
  groups: 0 1
CPU1 attaching sched-domain:
 domain 0: span 0-1 level MC
  groups: 1 0
net_namespace: 840 bytes
Booting paravirtualized kernel on bare hardware
Time:  9:40:28  Date: 01/09/09
NET: Registered protocol family 16
No dock devices found.
ACPI: bus type pci registered
PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
PCI: MCFG area at e0000000 reserved in E820
PCI: Using MMCONFIG for extended config space
PCI: Using configuration type 1 for base access
ACPI: EC: Look up EC in DSDT
ACPI: BIOS _OSI(Linux) query ignored via DMI
ACPI: Interpreter enabled
ACPI: (supports S0 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
ACPI: EC: non-query interrupt received, switching to interrupt mode
ACPI: EC: missing confirmations, switch off interrupt mode.
ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
ACPI: EC: driver started in poll mode
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: 0000:00:02.0 reg 10 64bit mmio: [f0000000, f00fffff]
PCI: 0000:00:02.0 reg 18 64bit mmio: [d0000000, dfffffff]
PCI: 0000:00:02.0 reg 20 io port: [1800, 1807]
PCI: 0000:00:02.1 reg 10 64bit mmio: [f0100000, f01fffff]
PCI: 0000:00:1a.0 reg 20 io port: [1820, 183f]
PCI: 0000:00:1a.1 reg 20 io port: [1840, 185f]
PCI: 0000:00:1a.7 reg 10 32bit mmio: [f0704800, f0704bff]
pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
pci 0000:00:1a.7: PME# disabled
PCI: 0000:00:1b.0 reg 10 64bit mmio: [f0500000, f0503fff]
pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1b.0: PME# disabled
pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.0: PME# disabled
pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.3: PME# disabled
pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.4: PME# disabled
pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
pci 0000:00:1c.5: PME# disabled
PCI: 0000:00:1d.0 reg 20 io port: [1860, 187f]
PCI: 0000:00:1d.1 reg 20 io port: [1880, 189f]
PCI: 0000:00:1d.2 reg 20 io port: [18a0, 18bf]
PCI: 0000:00:1d.7 reg 10 32bit mmio: [f0704c00, f0704fff]
pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
pci 0000:00:1d.7: PME# disabled
pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
PCI: 0000:00:1f.1 reg 20 io port: [1810, 181f]
PCI: 0000:00:1f.2 reg 10 io port: [1c00, 1c07]
PCI: 0000:00:1f.2 reg 14 io port: [18d4, 18d7]
PCI: 0000:00:1f.2 reg 18 io port: [18d8, 18df]
PCI: 0000:00:1f.2 reg 1c io port: [18d0, 18d3]
PCI: 0000:00:1f.2 reg 20 io port: [18e0, 18ff]
PCI: 0000:00:1f.2 reg 24 32bit mmio: [f0704000, f07047ff]
pci 0000:00:1f.2: PME# supported from D3hot
pci 0000:00:1f.2: PME# disabled
PCI: 0000:00:1f.3 reg 10 32bit mmio: [0, ff]
PCI: 0000:00:1f.3 reg 20 io port: [1c20, 1c3f]
PCI: bridge 0000:00:1c.0 io port: [0, fff]
PCI: bridge 0000:00:1c.0 32bit mmio: [0, fffff]
PCI: bridge 0000:00:1c.0 64bit mmio pref: [0, fffff]
PCI: bridge 0000:00:1c.3 io port: [0, fff]
PCI: bridge 0000:00:1c.3 32bit mmio: [0, fffff]
PCI: bridge 0000:00:1c.3 64bit mmio pref: [0, fffff]
PCI: 0000:07:00.0 reg 10 64bit mmio: [f0200000, f0203fff]
PCI: 0000:07:00.0 reg 18 io port: [2000, 20ff]
pci 0000:07:00.0: supports D1
pci 0000:07:00.0: supports D2
pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:07:00.0: PME# disabled
PCI: bridge 0000:00:1c.4 io port: [0, fff]
PCI: bridge 0000:00:1c.4 32bit mmio: [0, fffff]
PCI: bridge 0000:00:1c.4 64bit mmio pref: [0, fffff]
PCI: 0000:08:00.0 reg 10 64bit mmio: [f0300000, f0301fff]
pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
pci 0000:08:00.0: PME# disabled
PCI: bridge 0000:00:1c.5 io port: [0, fff]
PCI: bridge 0000:00:1c.5 32bit mmio: [0, fffff]
PCI: bridge 0000:00:1c.5 64bit mmio pref: [0, fffff]
PCI: 0000:0a:01.0 reg 10 32bit mmio: [f0400000, f0400fff]
PCI: 0000:0a:01.0 reg 14 32bit mmio: [f0402000, f04027ff]
pci 0000:0a:01.0: supports D1
pci 0000:0a:01.0: supports D2
pci 0000:0a:01.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:0a:01.0: PME# disabled
PCI: 0000:0a:01.2 reg 10 32bit mmio: [f0402800, f04028ff]
pci 0000:0a:01.2: supports D1
pci 0000:0a:01.2: supports D2
pci 0000:0a:01.2: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:0a:01.2: PME# disabled
PCI: 0000:0a:01.3 reg 10 32bit mmio: [f0401000, f0401fff]
pci 0000:0a:01.3: supports D1
pci 0000:0a:01.3: supports D2
pci 0000:0a:01.3: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:0a:01.3: PME# disabled
pci 0000:00:1e.0: transparent bridge
PCI: bridge 0000:00:1e.0 32bit mmio: [f0400000, f04fffff]
bus 00 -> node 0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *7 11 12 14 15)
ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 *5 6 7 10 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp 00:05: io resource (0x2e-0x2f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x4e-0x4f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x61-0x61) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x63-0x63) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x65-0x65) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x67-0x67) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x68-0x68) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x6c-0x6c) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x80-0x80) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x92-0x92) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0xb2-0xb3) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x800-0x80f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x2e-0x2f) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x4e-0x4f) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x61-0x61) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x63-0x63) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x65-0x65) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x67-0x67) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x68-0x68) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x6c-0x6c) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x80-0x80) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x92-0x92) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0xb2-0xb3) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x800-0x80f) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x2e-0x2f) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x4e-0x4f) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x61-0x61) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x63-0x63) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x65-0x65) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x67-0x67) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x68-0x68) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x6c-0x6c) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x80-0x80) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x92-0x92) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0xb2-0xb3) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x800-0x80f) overlaps 0000:00:1c.4 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x2e-0x2f) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x4e-0x4f) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x61-0x61) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x63-0x63) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x65-0x65) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x67-0x67) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x68-0x68) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x6c-0x6c) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x80-0x80) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x92-0x92) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0xb2-0xb3) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp 00:05: io resource (0x800-0x80f) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
pnp: PnP ACPI: found 9 devices
ACPI: ACPI bus type pnp unregistered
SCSI subsystem initialized
libata version 3.00 loaded.
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Using ACPI for IRQ routing
pci 0000:00:1c.0: BAR 7: can't allocate resource
pci 0000:00:1c.0: BAR 8: can't allocate resource
pci 0000:00:1c.0: BAR 9: can't allocate resource
pci 0000:00:1c.3: BAR 7: can't allocate resource
pci 0000:00:1c.3: BAR 8: can't allocate resource
pci 0000:00:1c.3: BAR 9: can't allocate resource
pci 0000:00:1c.4: BAR 7: can't allocate resource
pci 0000:00:1c.4: BAR 8: can't allocate resource
pci 0000:00:1c.4: BAR 9: can't allocate resource
pci 0000:00:1c.5: BAR 7: can't allocate resource
pci 0000:00:1c.5: BAR 8: can't allocate resource
pci 0000:00:1c.5: BAR 9: can't allocate resource
pci 0000:07:00.0: BAR 0: can't allocate resource
pci 0000:07:00.0: BAR 2: can't allocate resource
pci 0000:08:00.0: BAR 0: can't allocate resource
NetLabel: Initializing
NetLabel:  domain hash size = 128
NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
hpet0: 3 64-bit timers, 14318180 Hz
Switched to high resolution mode on CPU 0
tracer: 772 pages allocated for 65536 entries of 48 bytes
   actual entries 65620
Switched to high resolution mode on CPU 1
ACPI Error (psargs-0358): [CDW1] Namespace lookup failure, AE_NOT_FOUND
ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f78165b8), AE_NOT_FOUND
ACPI: RTC can wake from S4
system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
system 00:01: iomem range 0xff80000-0xff8ffff could not be reserved
system 00:03: iomem range 0xfed00000-0xfed003ff could not be reserved
system 00:05: ioport range 0x1000-0x107f has been reserved
system 00:05: ioport range 0x1180-0x11bf has been reserved
system 00:05: ioport range 0xfe00-0xfe00 has been reserved
pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
pci 0000:00:1c.0:   IO window: disabled
pci 0000:00:1c.0:   MEM window: disabled
pci 0000:00:1c.0:   PREFETCH window: disabled
pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
pci 0000:00:1c.3:   IO window: disabled
pci 0000:00:1c.3:   MEM window: disabled
pci 0000:00:1c.3:   PREFETCH window: disabled
pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07
pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
pci 0000:00:1c.4:   MEM window: 0xc2000000-0xc20fffff
pci 0000:00:1c.4:   PREFETCH window: disabled
pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
pci 0000:00:1c.5:   IO window: disabled
pci 0000:00:1c.5:   MEM window: 0xc2100000-0xc21fffff
pci 0000:00:1c.5:   PREFETCH window: disabled
pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
pci 0000:00:1e.0:   IO window: disabled
pci 0000:00:1e.0:   MEM window: 0xf0400000-0xf04fffff
pci 0000:00:1e.0:   PREFETCH window: disabled
pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:1c.0: setting latency timer to 64
pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
pci 0000:00:1c.3: setting latency timer to 64
pci 0000:00:1c.4: enabling device (0000 -> 0003)
pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:1c.4: setting latency timer to 64
pci 0000:00:1c.5: enabling device (0000 -> 0002)
pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
pci 0000:00:1c.5: setting latency timer to 64
pci 0000:00:1e.0: setting latency timer to 64
bus: 00 index 0 io port: [0, ffff]
bus: 00 index 1 mmio: [0, ffffffffffffffff]
bus: 02 index 0 mmio: [0, fff]
bus: 02 index 1 mmio: [0, fffff]
bus: 02 index 2 mmio: [0, fffff]
bus: 02 index 3 mmio: [0, 0]
bus: 06 index 0 mmio: [0, fff]
bus: 06 index 1 mmio: [0, fffff]
bus: 06 index 2 mmio: [0, fffff]
bus: 06 index 3 mmio: [0, 0]
bus: 07 index 0 io port: [2000, 2fff]
bus: 07 index 1 mmio: [c2000000, c20fffff]
bus: 07 index 2 mmio: [0, fffff]
bus: 07 index 3 mmio: [0, 0]
bus: 08 index 0 mmio: [0, fff]
bus: 08 index 1 mmio: [c2100000, c21fffff]
bus: 08 index 2 mmio: [0, fffff]
bus: 08 index 3 mmio: [0, 0]
bus: 0a index 0 mmio: [0, 0]
bus: 0a index 1 mmio: [f0400000, f04fffff]
bus: 0a index 2 mmio: [0, 0]
bus: 0a index 3 io port: [0, ffff]
bus: 0a index 4 mmio: [0, ffffffffffffffff]
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
NET: Registered protocol family 1
checking if image is initramfs... it is
Freeing initrd memory: 3581k freed
Simple Boot Flag at 0x36 set to 0x1
apm: BIOS not found.
audit: initializing netlink socket (disabled)
type=2000 audit(1231494027.969:1): initialized
highmem bounce pool size: 64 pages
HugeTLB registered 4 MB page size, pre-allocated 0 pages
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
msgmni has been set to 1730
SELinux:  Registering netfilter hooks
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
pci 0000:00:02.0: Boot video device
pcieport-driver 0000:00:1c.0: setting latency timer to 64
pcieport-driver 0000:00:1c.0: found MSI capability
pci_express 0000:00:1c.0:pcie00: allocate port service
pci_express 0000:00:1c.0:pcie02: allocate port service
pci_express 0000:00:1c.0:pcie03: allocate port service
pcieport-driver 0000:00:1c.3: setting latency timer to 64
pcieport-driver 0000:00:1c.3: found MSI capability
pci_express 0000:00:1c.3:pcie00: allocate port service
pci_express 0000:00:1c.3:pcie02: allocate port service
pci_express 0000:00:1c.3:pcie03: allocate port service
pcieport-driver 0000:00:1c.4: setting latency timer to 64
pcieport-driver 0000:00:1c.4: found MSI capability
pci_express 0000:00:1c.4:pcie00: allocate port service
pci_express 0000:00:1c.4:pcie02: allocate port service
pci_express 0000:00:1c.4:pcie03: allocate port service
pcieport-driver 0000:00:1c.5: setting latency timer to 64
pcieport-driver 0000:00:1c.5: found MSI capability
pci_express 0000:00:1c.5:pcie00: allocate port service
pci_express 0000:00:1c.5:pcie02: allocate port service
pci_express 0000:00:1c.5:pcie03: allocate port service
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
acpiphp_glue: can't get bus number, assuming 0
ACPI: AC Adapter [ACAD] (off-line)
ACPI: Battery Slot [BAT1] (battery absent)
input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
ACPI: Power Button (FF) [PWRF]
input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
ACPI: Lid Switch [LID]
input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
ACPI: Power Button (CM) [PWRB]
ACPI: SSDT BF6D3B89, 0238 (r1  PmRef  Cpu0Ist     3000 INTL 20061109)
ACPI: SSDT BF6D350D, 05F7 (r1  PmRef  Cpu0Cst     3001 INTL 20061109)
Monitor-Mwait will be used to enter C-1 state
Monitor-Mwait will be used to enter C-2 state
Monitor-Mwait will be used to enter C-3 state
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
processor ACPI0007:00: registered as cooling_device0
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: SSDT BF6D3DC1, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20061109)
ACPI: SSDT BF6D3B04, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20061109)
ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
processor ACPI0007:01: registered as cooling_device1
ACPI: Processor [CPU1] (supports 8 throttling states)
thermal LNXTHERM:01: registered as thermal_zone0
ACPI: Thermal Zone [THRM] (54 C)
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
hpet_resources: 0xfed00000 is busy
Non-volatile memory driver v1.2
Linux agpgart interface v0.103
agpgart-intel 0000:00:00.0: Intel 965GM Chipset
agpgart-intel 0000:00:00.0: detected 7676K stolen memory
agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Serial: 8250/16550 driver4 ports, IRQ sharing enabled
brd: module loaded
loop: module loaded
input: Macintosh mouse button emulation as /devices/virtual/input/input3
Driver 'sd' needs updating - please use bus_type methods
Driver 'sr' needs updating - please use bus_type methods
ahci 0000:00:1f.2: version 3.0
ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
ahci 0000:00:1f.2: setting latency timer to 64
scsi0 : ahci
scsi1 : ahci
scsi2 : ahci
ata1: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704100 irq 19
ata2: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704180 irq 19
ata3: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704200 irq 19
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: _GTF unexpected object type 0x1
ata1.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC33P, max UDMA/133
ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
ata1.00: _GTF unexpected object type 0x1
ata1.00: configured for UDMA/133
ata2: SATA link down (SStatus 0 SControl 300)
ata3: SATA link down (SStatus 0 SControl 300)
scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 sda3 sda4 < sda5 >
sd 0:0:0:0: [sda] Attached SCSI disk
sd 0:0:0:0: Attached scsi generic sg0 type 0
ata_piix 0000:00:1f.1: version 2.12
ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
ata_piix 0000:00:1f.1: setting latency timer to 64
scsi3 : ata_piix
scsi4 : ata_piix
ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-U10F, TL01, max UDMA/33
ata4.00: configured for UDMA/33
ata5: port disabled. ignoring.
scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-U10F  TL01 PQ: 0 ANSI: 5
sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 3:0:0:0: Attached scsi CD-ROM sr0
sr 3:0:0:0: Attached scsi generic sg1 type 5
ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
ehci_hcd 0000:00:1a.7: setting latency timer to 64
ehci_hcd 0000:00:1a.7: EHCI Host Controller
ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:1a.7: debug port 1
ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0704800
ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 4 ports detected
usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb1: Product: EHCI Host Controller
usb usb1: Manufacturer: Linux 2.6.27.9-159.fc10.i686 ehci_hcd
usb usb1: SerialNumber: 0000:00:1a.7
ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: setting latency timer to 64
ehci_hcd 0000:00:1d.7: EHCI Host Controller
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
ehci_hcd 0000:00:1d.7: debug port 1
ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0704c00
ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 6 ports detected
usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb2: Product: EHCI Host Controller
usb usb2: Manufacturer: Linux 2.6.27.9-159.fc10.i686 ehci_hcd
usb usb2: SerialNumber: 0000:00:1d.7
ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
USB Universal Host Controller Interface driver v3.0
uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1a.0: setting latency timer to 64
uhci_hcd 0000:00:1a.0: UHCI Host Controller
uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb3: Product: UHCI Host Controller
usb usb3: Manufacturer: Linux 2.6.27.9-159.fc10.i686 uhci_hcd
usb usb3: SerialNumber: 0000:00:1a.0
uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:1a.1: setting latency timer to 64
uhci_hcd 0000:00:1a.1: UHCI Host Controller
uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 2-4: new high speed USB device using ehci_hcd and address 3
usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb4: Product: UHCI Host Controller
usb usb4: Manufacturer: Linux 2.6.27.9-159.fc10.i686 uhci_hcd
usb usb4: SerialNumber: 0000:00:1a.1
uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
uhci_hcd 0000:00:1d.0: setting latency timer to 64
uhci_hcd 0000:00:1d.0: UHCI Host Controller
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
usb 2-4: configuration #1 chosen from 1 choice
usb 2-4: New USB device found, idVendor=04f2, idProduct=b008
usb 2-4: New USB device strings: Mfr=2, Product=1, SerialNumber=3
usb 2-4: Product: Chicony USB 2.0 Camera
usb 2-4: Manufacturer: Chicony Electronics Co., Ltd.
usb 2-4: SerialNumber: SN0001
usb 3-2: new low speed USB device using uhci_hcd and address 2
usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb5: Product: UHCI Host Controller
usb usb5: Manufacturer: Linux 2.6.27.9-159.fc10.i686 uhci_hcd
usb usb5: SerialNumber: 0000:00:1d.0
uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: setting latency timer to 64
uhci_hcd 0000:00:1d.1: UHCI Host Controller
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
usb usb6: configuration #1 chosen from 1 choice
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 2 ports detected
usb 3-2: configuration #1 chosen from 1 choice
usb 3-2: New USB device found, idVendor=0458, idProduct=003a
usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 3-2: Product: Optical Mouse
usb 3-2: Manufacturer: Genius
usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb6: Product: UHCI Host Controller
usb usb6: Manufacturer: Linux 2.6.27.9-159.fc10.i686 uhci_hcd
usb usb6: SerialNumber: 0000:00:1d.1
uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: setting latency timer to 64
uhci_hcd 0000:00:1d.2: UHCI Host Controller
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
usb usb7: configuration #1 chosen from 1 choice
hub 7-0:1.0: USB hub found
hub 7-0:1.0: 2 ports detected
usb 5-2: new full speed USB device using uhci_hcd and address 2
usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb7: Product: UHCI Host Controller
usb usb7: Manufacturer: Linux 2.6.27.9-159.fc10.i686 uhci_hcd
usb usb7: SerialNumber: 0000:00:1d.2
PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
usb 5-2: configuration #1 chosen from 1 choice
usb 5-2: New USB device found, idVendor=08ff, idProduct=1600
usb 5-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
usb 5-2: Product: Fingerprint Sensor
rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
rtc0: alarms up to one month, y3k, hpet irqs
device-mapper: uevent: version 1.0.3
device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
cpuidle: using governor ladder
cpuidle: using governor menu
usbcore: registered new interface driver hiddev
Marking TSC unstable due to TSC halts in idle
input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5
input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1a.0-2
usbcore: registered new interface driver usbhid
usbhid: v2.6:USB HID core driver
nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
ip_tables: (C) 2000-2006 Netfilter Core Team
TCP cubic registered
Initializing XFRM netlink socket
NET: Registered protocol family 17
Using IPI No-Shortcut mode
registered taskstats version 1
  Magic number: 9:728:676
Freeing unused kernel memory: 412k freed
Write protecting the kernel text: 2740k
Write protecting the kernel read-only data: 1172k
Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1e0b1, caps: 0xd04711/0xa00000
synaptics: Toshiba Satellite U405 detected, limiting rate to 40pps.
input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: dm-0: orphan cleanup on readonly fs
ext3_orphan_cleanup: deleting unreferenced inode 3736772
ext3_orphan_cleanup: deleting unreferenced inode 3441014
ext3_orphan_cleanup: deleting unreferenced inode 3441013
ext3_orphan_cleanup: deleting unreferenced inode 3441012
ext3_orphan_cleanup: deleting unreferenced inode 3441007
ext3_orphan_cleanup: deleting unreferenced inode 3441005
ext3_orphan_cleanup: deleting unreferenced inode 3441003
ext3_orphan_cleanup: deleting unreferenced inode 3441001
ext3_orphan_cleanup: deleting unreferenced inode 3440994
ext3_orphan_cleanup: deleting unreferenced inode 3440988
ext3_orphan_cleanup: deleting unreferenced inode 3440987
ext3_orphan_cleanup: deleting unreferenced inode 3440983
ext3_orphan_cleanup: deleting unreferenced inode 3440967
ext3_orphan_cleanup: deleting unreferenced inode 3440953
ext3_orphan_cleanup: deleting unreferenced inode 3440952
ext3_orphan_cleanup: deleting unreferenced inode 3440937
ext3_orphan_cleanup: deleting unreferenced inode 3440935
ext3_orphan_cleanup: deleting unreferenced inode 3440934
ext3_orphan_cleanup: deleting unreferenced inode 3440785
ext3_orphan_cleanup: deleting unreferenced inode 3653656
EXT3-fs: dm-0: 20 orphan inodes deleted
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
SELinux:  Disabled at runtime.
SELinux:  Unregistering netfilter hooks
type=1404 audit(1231494035.904:2): selinux=0 auid=4294967295 ses=4294967295
udevd version 127 started
acpi device:03: registered as cooling_device2
acpi device:04: registered as cooling_device3
acpi device:05: registered as cooling_device4
acpi device:06: registered as cooling_device5
acpi device:07: registered as cooling_device6
input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input7
ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
ACPI: WMI: Mapper loaded
sky2 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
sky2 0000:07:00.0: setting latency timer to 64
sky2 0000:07:00.0: v1.22 addr 0xc2000000 irq 16 Yukon-2 FE+ rev 0
sky2 eth0: addr 00:1e:68:b7:7a:ae
i801_smbus 0000:00:1f.3: PCI INT C -> GSI 19 (level, low) -> IRQ 19
ACPI: I/O resource 0000:00:1f.3 [0x1c20-0x1c3f] conflicts with ACPI region SMBI [0x1c20-0x1c2f]
ACPI: Device needs an ACPI driver
input: PC Speaker as /devices/platform/pcspkr/input/input8
iTCO_vendor_support: vendor-support=0
Clocksource tsc unstable (delta = -72093732 ns)
firewire_ohci 0000:0a:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Linux video capture interface: v2.00
firewire_ohci: Added fw-ohci device 0000:0a:01.0, OHCI version 1.10
iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
sdhci-pci 0000:0a:01.2: SDHCI controller found [1217:7120] (rev 2)
sdhci-pci 0000:0a:01.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
mmc0: Unknown controller version (2). You may experience problems.
Registered led device: mmc0
mmc0: SDHCI controller on PCI [0000:0a:01.2] using DMA
iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27kds
iwlagn: Copyright(c) 2003-2008 Intel Corporation
iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
iwlagn 0000:08:00.0: setting latency timer to 64
iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
iwlagn 0000:08:00.0: PCI INT A disabled
phy0: Selected rate control algorithm 'iwl-agn-rs'
uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input9
usbcore: registered new interface driver uvcvideo
USB Video Class driver (v0.1.0)
firewire_core: created device fw0: GUID 001b24000123b071, S400
HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
HDA Intel 0000:00:1b.0: setting latency timer to 64
device-mapper: multipath: version 1.0.5 loaded
EXT3 FS on dm-0, internal journal
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda3, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
Adding 5144568k swap on /dev/mapper/VolGroup00-LogVol01.  Priority:-1 extents:1 across:5144568k
IA-32 Microcode Update Driver: v1.14a <tigran@aivazian.fsnet.co.uk>
firmware: requesting intel-ucode/06-0f-0d
firmware: requesting intel-ucode/06-0f-0d
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
ip6_tables: (C) 2000-2006 Netfilter Core Team
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
vboxdrv: Trying to deactivate the NMI watchdog permanently...
vboxdrv: Successfully done.
vboxdrv: Found 2 processor cores.
vboxdrv: fAsync=0 offMin=0x360 offMax=0x1458
vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
vboxdrv: Successfully loaded version 2.1.0 (interface 0x000a0008).
Bluetooth: Core ver 2.13
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP ver 2.11
Bluetooth: L2CAP socket layer initialized
Bluetooth: SCO (Voice Link) ver 0.6
Bluetooth: SCO socket layer initialized
Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Bluetooth: BNEP filters: protocol multicast
Bridge firewalling registered
pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
sky2 eth0: enabling interface
ADDRCONF(NETDEV_UP): eth0: link is not ready
iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
iwlagn 0000:08:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
firmware: requesting iwlwifi-4965-2.ucode
Registered led device: iwl-phy0:radio
Registered led device: iwl-phy0:assoc
Registered led device: iwl-phy0:RX
Registered led device: iwl-phy0:TX
ADDRCONF(NETDEV_UP): wlan0: link is not ready
wlan0: authenticate with AP 00:08:a1:9c:37:3f
wlan0: authenticated
wlan0: associate with AP 00:08:a1:9c:37:3f
wlan0: RX AssocResp from 00:08:a1:9c:37:3f (capab=0x421 status=0 aid=7)
wlan0: associated
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: disassociating by local choice (reason=3)
[drm] Initialized drm 1.1.0 20060810
pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
pci 0000:00:02.0: setting latency timer to 64
[drm] Initialized i915 1.6.0 20080730 on minor 0
CPU0 attaching NULL sched-domain.
CPU1 attaching NULL sched-domain.
CPU0 attaching sched-domain:
 domain 0: span 0-1 level MC
  groups: 0 1
  domain 1: span 0-1 level CPU
   groups: 0-1
CPU1 attaching sched-domain:
 domain 0: span 0-1 level MC
  groups: 1 0
  domain 1: span 0-1 level CPU
   groups: 0-1
wlan0: no IPv6 routers present
fuse init (API version 7.9)
CPU0 attaching NULL sched-domain.
CPU1 attaching NULL sched-domain.
CPU0 attaching sched-domain:
 domain 0: span 0-1 level MC
  groups: 0 1
  domain 1: span 0-1 level CPU
   groups: 0-1
CPU1 attaching sched-domain:
 domain 0: span 0-1 level MC
  groups: 1 0
  domain 1: span 0-1 level CPU
   groups: 0-1
wlan0: authenticate with AP 00:08:a1:9c:37:3f
wlan0: authenticate with AP 00:08:a1:9c:37:3f
wlan0: authenticated
wlan0: associate with AP 00:08:a1:9c:37:3f
wlan0: RX ReassocResp from 00:08:a1:9c:37:3f (capab=0x421 status=0 aid=7)
wlan0: associated
usb 3-2: USB disconnect, address 2
usb 3-2: new low speed USB device using uhci_hcd and address 3
usb 3-2: configuration #1 chosen from 1 choice
input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input10
input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1a.0-2
usb 3-2: New USB device found, idVendor=0458, idProduct=003a
usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 3-2: Product: Optical Mouse
usb 3-2: Manufacturer: Genius
```

---

### Post by 65daysofstatic on 2009-03-02
hi, i just bought a toshiba u405d-s2874, and I want to know if there is any problem with the drivers.
It has and AMD turion x2 64 processor, ati radeon 3100 graphics, the wirelss is Atheros, and conexant high definition smart audio.

---

### Post by snahaw0 on 2010-11-06
I have a U405-S2833 that I recently loaded Ubuntu 10.10 on. I have found one hardware issue so far. The CD/DVD drive reads, but will not burn. I tried several programs to burn including AcidRip, Brasero, K3B and ManDVD. They all run until I hit burn, then they just close. I am assuming that they are not seeing my drive as a burner, although when I put a blank disk in, it asks me if I want to make a data DVD, so I am confused. If this does not sound like a hardware problem, or belongs in another forum, I apologise. If I need to post somewhere else, please let me know where. Thank you.

---

