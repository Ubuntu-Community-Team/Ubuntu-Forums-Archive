---
title: "wifi connection issue hp probook"
date: 2012-06-04
forum: Hardware
---

### Post by sidharth4788 on 2012-06-04
I have installed ubuntu 12.04 64 bit on my laptop HP Probook 4420s. Sometimes wifi get connected and sometimes it just tried to connect but did not get connected. Following are the information as par [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) post which i fetch when wifi did not get connected.


**1 ) Machine Brand and Model (PC/Laptop):**
HP Probook 4420s

[B]2 ) Wireless Brand, Model and Wireless Chipset:
[/B]43:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)**3 ) check interface:**

$ ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:26:82:c7:d3:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



$ iwconfig

wlan0     IEEE 802.11abgn  ESSID: off/any  
          Mode:Managed  Access Point:  Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          


[B]4 ) Check for modules:

[/B]$ lsmod

Module                  Size  Used by
usbhid                 47199  0 
hid                    99559  1 usbhid
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
parport_pc             32866  0 
bnep                   18281  2 
ppdev                  17113  0 
rfcomm                 47604  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
bluetooth             180104  10 bnep,rfcomm
wl                   2568210  0 
lib80211               14381  1 wl
bcma                   26696  0 
arc4                   12529  2 
joydev                 17693  0 
binfmt_misc            17540  1 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
psmouse                87603  0 
serio_raw              13211  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  468651  8 
drm_kms_helper         46978  1 i915
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
brcmsmac              570859  0 
drm                   242038  4 i915,drm_kms_helper
mac80211              506816  1 brcmsmac
intel_ips              18089  0 
brcmutil               15139  1 brcmsmac
i2c_algo_bit           13423  1 i915
cfg80211              205544  2 brcmsmac,mac80211
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmac
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19596  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
wmi                    19256  1 hp_wmi
mac_hid                13253  0 
r8169                  62099  0 


[B]5 ) Kernel boot messages

[/B]$ dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=57b35422-576b-4d8e-8a32-bcb37b530470 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000076fcf000 (usable)
[    0.000000]  BIOS-e820: 0000000076fcf000 - 00000000776cf000 (reserved)
[    0.000000]  BIOS-e820: 00000000776cf000 - 00000000777cf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000777cf000 - 00000000777ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000777ff000 - 0000000077800000 (usable)
[    0.000000]  BIOS-e820: 0000000077800000 - 0000000078000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed19000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffd80000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP ProBook 4420s/1423, BIOS 68AHH Ver. F.09 06/29/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x77800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 078000000 mask FF8000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-0000000077800000
[    0.000000]  0000000000 - 0077800000 page 2M
[    0.000000] kernel direct mapping tables up to 77800000 @ 1fffd000-20000000
[    0.000000] RAMDISK: 364ee000 - 3726f000
[    0.000000] ACPI: RSDP 00000000000f2b20 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000777fe120 0007C (v01 HPQOEM SLIC-MPC 0000000F      01000013)
[    0.000000] ACPI: FACP 00000000777fc000 000F4 (v03 HPQOEM 1423     0000000F HP   00000001)
[    0.000000] ACPI: DSDT 00000000777d9000 1D9BF (v02 HPQOEM 1423     00000001 INTL 20060912)
[    0.000000] ACPI: FACS 000000007777e000 00040
[    0.000000] ACPI: HPET 00000000777fb000 00038 (v01 HPQOEM 1423     00000001 HP   00000001)
[    0.000000] ACPI: APIC 00000000777fa000 000BC (v01 HPQOEM 1423     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 00000000777f9000 0003C (v01 HPQOEM 1423     00000001 HP   00000001)
[    0.000000] ACPI: ASF! 00000000777f8000 000A0 (v32 HPQOEM 1423     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 00000000777d6000 000CB (v01 HPQOEM SataAhci 00001000 INTL 20060912)
[    0.000000] ACPI: SSDT 00000000777d5000 00314 (v01 HPQOEM PtidDevc 00001000 INTL 20060912)
[    0.000000] ACPI: SSDT 00000000777d4000 0005F (v01 HPQOEM   HPQNLP 00000001 INTL 20060912)
[    0.000000] ACPI: SSDT 00000000777d3000 00A10 (v01  PmRef    CpuPm 00003000 INTL 20060912)
[    0.000000] ACPI: SSDT 00000000777d2000 00288 (v01  PmRef  Cpu0Tst 00003000 INTL 20060912)
[    0.000000] ACPI: SSDT 00000000777d1000 00225 (v01  PmRef    ApTst 00003000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000077800000
[    0.000000] Initmem setup node 0 0000000000000000-0000000077800000
[    0.000000]   NODE_DATA [0000000076fca000 - 0000000076fcefff]
[    0.000000]  [ffffea0000000000-ffffea0001dfffff] PMD -> [ffff880074800000-ffff8800765fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00076fcf
[    0.000000]     0: 0x000777ff -> 0x00077800
[    0.000000] On node 0 totalpages: 487263
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3914 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7584 pages used for memmap
[    0.000000]   DMA32 zone: 475696 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000076fcf000 - 00000000776cf000
[    0.000000] PM: Registered nosave memory: 00000000776cf000 - 00000000777cf000
[    0.000000] PM: Registered nosave memory: 00000000777cf000 - 00000000777ff000
[    0.000000] Allocating PCI resources starting at 78000000 (gap: 78000000:68000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880076c00000 s83072 r8192 d23424 u262144
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 479610
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=57b35422-576b-4d8e-8a32-bcb37b530470 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 1887780k/1957888k available (6566k kernel code, 8836k absent, 61272k reserved, 6637k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 15728640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2400.073 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4800.14 BogoMIPS (lpj=9600292)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000028] Security Framework initialized
[    0.000043] AppArmor: AppArmor initialized
[    0.000044] Yama: becoming mindful.
[    0.000256] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000946] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.001244] Mount-cache hash table entries: 256
[    0.001368] Initializing cgroup subsys cpuacct
[    0.001373] Initializing cgroup subsys memory
[    0.001380] Initializing cgroup subsys devices
[    0.001382] Initializing cgroup subsys freezer
[    0.001384] Initializing cgroup subsys blkio
[    0.001389] Initializing cgroup subsys perf_event
[    0.001416] CPU: Physical Processor ID: 0
[    0.001417] CPU: Processor Core ID: 0
[    0.001423] mce: CPU supports 9 MCE banks
[    0.001433] CPU0: Thermal monitoring enabled (TM1)
[    0.001441] using mwait in idle threads.
[    0.003401] ACPI: Core revision 20110623
[    0.011860] ftrace: allocating 27049 entries in 107 pages
[    0.019782] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059406] CPU0: Intel(R) Core(TM) i5 CPU       M 450  @ 2.40GHz stepping 05
[    0.163946] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.163953] ... version:                3
[    0.163954] ... bit width:              48
[    0.163955] ... generic registers:      4
[    0.163956] ... value mask:             0000ffffffffffff
[    0.163957] ... max period:             000000007fffffff
[    0.163958] ... fixed-purpose events:   3
[    0.163959] ... event mask:             000000070000000f
[    0.164156] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164236] Booting Node   0, Processors  #1
[    0.164238] smpboot cpu 1: start_ip = 9a000
[    0.271940] NMI watchdog enabled, takes one hw-pmu counter.
[    0.272052]  #2
[    0.272053] smpboot cpu 2: start_ip = 9a000
[    0.379692] NMI watchdog enabled, takes one hw-pmu counter.
[    0.379793]  #3
[    0.379794] smpboot cpu 3: start_ip = 9a000
[    0.487521] NMI watchdog enabled, takes one hw-pmu counter.
[    0.487562] Brought up 4 CPUs
[    0.487565] Total of 4 processors activated (19199.65 BogoMIPS).
[    0.490455] devtmpfs: initialized
[    0.491207] EVM: security.selinux
[    0.491208] EVM: security.SMACK64
[    0.491209] EVM: security.capability
[    0.491236] PM: Registering ACPI NVS region at 776cf000 (1048576 bytes)
[    0.492026] print_constraints: dummy: 
[    0.492057] RTC time: 22:21:46, date: 06/04/12
[    0.492088] NET: Registered protocol family 16
[    0.492182] Trying to unpack rootfs image as initramfs...
[    0.492192] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.492195] ACPI: bus type pci registered
[    0.492265] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.492268] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.518123] PCI: Using configuration type 1 for base access
[    0.518941] bio: create slab <bio-0> at 0
[    0.519031] ACPI: Added _OSI(Module Device)
[    0.519032] ACPI: Added _OSI(Processor Device)
[    0.519034] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.519036] ACPI: Added _OSI(Processor Aggregator Device)
[    0.520701] ACPI: EC: Look up EC in DSDT
[    0.548752] ACPI: Executed 2 blocks of module-level executable AML code
[    0.579369] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.612898] ACPI: SSDT 00000000776c8918 003F9 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.613298] ACPI: Dynamic OEM Table Load:
[    0.613301] ACPI: SSDT           (null) 003F9 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.613423] ACPI: SSDT 00000000776c6018 008AA (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.613798] ACPI: Dynamic OEM Table Load:
[    0.613800] ACPI: SSDT           (null) 008AA (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.659440] ACPI: SSDT 00000000776c7a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.659884] ACPI: Dynamic OEM Table Load:
[    0.659886] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.679265] ACPI: SSDT 00000000776c5d98 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.679685] ACPI: Dynamic OEM Table Load:
[    0.679687] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.717151] Freeing initrd memory: 13828k freed
[    1.138019] ACPI: Interpreter enabled
[    1.138026] ACPI: (supports S0 S3 S4 S5)
[    1.138047] ACPI: Using IOAPIC for interrupt routing
[    1.139587] ACPI: Power Resource [APPR] (off)
[    1.142855] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    1.143030] ACPI: No dock devices found.
[    1.143032] HEST: Table not found.
[    1.143035] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.143702] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.144268] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.144270] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.144272] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.144275] pci_root PNP0A08:00: host bridge window [mem 0x7c000000-0xdfffffff]
[    1.144277] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfedfffff]
[    1.144278] pci_root PNP0A08:00: host bridge window [mem 0xfee01000-0xffffffff]
[    1.144290] pci 0000:00:00.0: [8086:0044] type 0 class 0x000600
[    1.144308] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    1.144329] pci 0000:00:02.0: [8086:0046] type 0 class 0x000300
[    1.144339] pci 0000:00:02.0: reg 10: [mem 0x90000000-0x903fffff 64bit]
[    1.144345] pci 0000:00:02.0: reg 18: [mem 0x80000000-0x8fffffff 64bit pref]
[    1.144349] pci 0000:00:02.0: reg 20: [io  0x5030-0x5037]
[    1.144411] pci 0000:00:16.0: [8086:3b64] type 0 class 0x000780
[    1.144438] pci 0000:00:16.0: reg 10: [mem 0x94904000-0x9490400f 64bit]
[    1.144532] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.144537] pci 0000:00:16.0: PME# disabled
[    1.144576] pci 0000:00:1a.0: [8086:3b3c] type 0 class 0x000c03
[    1.144600] pci 0000:00:1a.0: reg 10: [mem 0x94909000-0x949093ff]
[    1.144708] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.144712] pci 0000:00:1a.0: PME# disabled
[    1.144743] pci 0000:00:1b.0: [8086:3b56] type 0 class 0x000403
[    1.144764] pci 0000:00:1b.0: reg 10: [mem 0x94900000-0x94903fff 64bit]
[    1.144858] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.144863] pci 0000:00:1b.0: PME# disabled
[    1.144891] pci 0000:00:1c.0: [8086:3b42] type 1 class 0x000604
[    1.144989] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.144993] pci 0000:00:1c.0: PME# disabled
[    1.145022] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    1.145121] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.145125] pci 0000:00:1c.1: PME# disabled
[    1.145155] pci 0000:00:1c.3: [8086:3b48] type 1 class 0x000604
[    1.145254] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.145258] pci 0000:00:1c.3: PME# disabled
[    1.145290] pci 0000:00:1c.5: [8086:3b4c] type 1 class 0x000604
[    1.145389] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.145393] pci 0000:00:1c.5: PME# disabled
[    1.145429] pci 0000:00:1d.0: [8086:3b34] type 0 class 0x000c03
[    1.145453] pci 0000:00:1d.0: reg 10: [mem 0x94908000-0x949083ff]
[    1.145561] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.145565] pci 0000:00:1d.0: PME# disabled
[    1.145589] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    1.145674] pci 0000:00:1f.0: [8086:3b0b] type 0 class 0x000601
[    1.145801] pci 0000:00:1f.2: [8086:3b2f] type 0 class 0x000106
[    1.145827] pci 0000:00:1f.2: reg 10: [io  0x5028-0x502f]
[    1.145838] pci 0000:00:1f.2: reg 14: [io  0x503c-0x503f]
[    1.145848] pci 0000:00:1f.2: reg 18: [io  0x5020-0x5027]
[    1.145859] pci 0000:00:1f.2: reg 1c: [io  0x5038-0x503b]
[    1.145870] pci 0000:00:1f.2: reg 20: [io  0x5000-0x501f]
[    1.145881] pci 0000:00:1f.2: reg 24: [mem 0x94907000-0x949077ff]
[    1.145945] pci 0000:00:1f.2: PME# supported from D3hot
[    1.145950] pci 0000:00:1f.2: PME# disabled
[    1.145983] pci 0000:00:1f.6: [8086:3b32] type 0 class 0x001180
[    1.146010] pci 0000:00:1f.6: reg 10: [mem 0x94906000-0x94906fff 64bit]
[    1.146159] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.146167] pci 0000:00:1c.0:   bridge window [mem 0x94800000-0x948fffff]
[    1.146227] pci 0000:00:1c.1: PCI bridge to [bus 02-42]
[    1.146231] pci 0000:00:1c.1:   bridge window [io  0x3000-0x4fff]
[    1.146236] pci 0000:00:1c.1:   bridge window [mem 0x90800000-0x947fffff]
[    1.146355] pci 0000:43:00.0: [14e4:4353] type 0 class 0x000280
[    1.146386] pci 0000:43:00.0: reg 10: [mem 0x90700000-0x90703fff 64bit]
[    1.146550] pci 0000:43:00.0: supports D1 D2
[    1.154491] pci 0000:00:1c.3: PCI bridge to [bus 43-43]
[    1.154498] pci 0000:00:1c.3:   bridge window [mem 0x90700000-0x907fffff]
[    1.154576] pci 0000:44:00.0: [10ec:8168] type 0 class 0x000200
[    1.154591] pci 0000:44:00.0: reg 10: [io  0x2000-0x20ff]
[    1.154618] pci 0000:44:00.0: reg 18: [mem 0x90404000-0x90404fff 64bit pref]
[    1.154636] pci 0000:44:00.0: reg 20: [mem 0x90400000-0x90403fff 64bit pref]
[    1.154647] pci 0000:44:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    1.154709] pci 0000:44:00.0: supports D1 D2
[    1.154710] pci 0000:44:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.154715] pci 0000:44:00.0: PME# disabled
[    1.162443] pci 0000:00:1c.5: PCI bridge to [bus 44-44]
[    1.162450] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    1.162460] pci 0000:00:1c.5:   bridge window [mem 0x90600000-0x906fffff]
[    1.162467] pci 0000:00:1c.5:   bridge window [mem 0x90400000-0x904fffff 64bit pref]
[    1.162540] pci 0000:00:1e.0: PCI bridge to [bus 45-45] (subtractive decode)
[    1.162547] pci 0000:00:1e.0:   bridge window [mem 0x90500000-0x905fffff]
[    1.162554] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.162556] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.162558] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.162560] pci 0000:00:1e.0:   bridge window [mem 0x7c000000-0xdfffffff] (subtractive decode)
[    1.162562] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfedfffff] (subtractive decode)
[    1.162564] pci 0000:00:1e.0:   bridge window [mem 0xfee01000-0xffffffff] (subtractive decode)
[    1.162595] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.162787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    1.162832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.162859] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.162905] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.162935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.163317]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.164309]  pci0000:00: ACPI _OSC control (0x1d) granted
[    1.169048] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    1.169108] pci 0000:ff:00.0: [8086:2c62] type 0 class 0x000600
[    1.169126] pci 0000:ff:00.1: [8086:2d01] type 0 class 0x000600
[    1.169145] pci 0000:ff:02.0: [8086:2d10] type 0 class 0x000600
[    1.169161] pci 0000:ff:02.1: [8086:2d11] type 0 class 0x000600
[    1.169177] pci 0000:ff:02.2: [8086:2d12] type 0 class 0x000600
[    1.169193] pci 0000:ff:02.3: [8086:2d13] type 0 class 0x000600
[    1.169221]  pci0000:ff: Requesting ACPI _OSC control (0x1d)
[    1.169224]  pci0000:ff: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    1.169225] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.169419] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.169458] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    1.169495] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.169531] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.169568] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.169607] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.169643] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.169680] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.169778] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.169785] vgaarb: loaded
[    1.169786] vgaarb: bridge control possible 0000:00:02.0
[    1.169873] i2c-core: driver [aat2870] using legacy suspend method
[    1.169875] i2c-core: driver [aat2870] using legacy resume method
[    1.169931] SCSI subsystem initialized
[    1.169986] libata version 3.00 loaded.
[    1.170021] usbcore: registered new interface driver usbfs
[    1.170030] usbcore: registered new interface driver hub
[    1.170052] usbcore: registered new device driver usb
[    1.170123] PCI: Using ACPI for IRQ routing
[    1.179925] PCI: pci_cache_line_size set to 64 bytes
[    1.179994] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    1.179996] reserve RAM buffer: 0000000076fcf000 - 0000000077ffffff 
[    1.179998] reserve RAM buffer: 0000000077800000 - 0000000077ffffff 
[    1.180082] NetLabel: Initializing
[    1.180084] NetLabel:  domain hash size = 128
[    1.180085] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.180094] NetLabel:  unlabeled traffic allowed by default
[    1.180140] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.180145] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.182158] Switching to clocksource hpet
[    1.187709] AppArmor: AppArmor Filesystem Enabled
[    1.187738] pnp: PnP ACPI init
[    1.187754] ACPI: bus type pnp registered
[    1.188097] pnp 00:00: [bus 00-fe]
[    1.188099] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.188101] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.188103] pnp 00:00: [io  0x0d00-0xffff window]
[    1.188104] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.188106] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.188108] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.188109] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.188111] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.188112] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.188114] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.188115] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.188117] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.188119] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.188120] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.188122] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.188123] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.188125] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.188127] pnp 00:00: [mem 0x7c000000-0xdfffffff window]
[    1.188128] pnp 00:00: [mem 0xf0000000-0xfedfffff window]
[    1.188130] pnp 00:00: [mem 0xfee01000-0xffffffff window]
[    1.188215] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.188380] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    1.188381] pnp 00:01: [mem 0xfed10000-0xfed13fff]
[    1.188383] pnp 00:01: [mem 0xfed1b000-0xfed1bfff]
[    1.188384] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    1.188386] pnp 00:01: [mem 0x7c000000-0x7c000fff]
[    1.188387] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    1.188389] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    1.188390] pnp 00:01: [mem 0xfed90000-0xfed8ffff disabled]
[    1.188392] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    1.188393] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    1.188442] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.188444] system 00:01: [mem 0xfed10000-0xfed13fff] has been reserved
[    1.188446] system 00:01: [mem 0xfed1b000-0xfed1bfff] has been reserved
[    1.188448] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.188450] system 00:01: [mem 0x7c000000-0x7c000fff] has been reserved
[    1.188452] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    1.188456] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.188458] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.188460] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    1.188463] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.188531] pnp 00:02: [io  0x0000-0x001f]
[    1.188533] pnp 00:02: [io  0x0081-0x0091]
[    1.188536] pnp 00:02: [io  0x0093-0x009f]
[    1.188537] pnp 00:02: [io  0x00c0-0x00df]
[    1.188539] pnp 00:02: [dma 4]
[    1.188565] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.188572] pnp 00:03: [mem 0xff000000-0xffffffff]
[    1.188597] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    1.188665] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    1.188693] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.188702] pnp 00:05: [io  0x00f0]
[    1.188713] pnp 00:05: [irq 13]
[    1.188739] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.188747] pnp 00:06: [io  0x002e-0x002f]
[    1.188749] pnp 00:06: [io  0x004e-0x004f]
[    1.188750] pnp 00:06: [io  0x0061]
[    1.188752] pnp 00:06: [io  0x0063]
[    1.188753] pnp 00:06: [io  0x0065]
[    1.188754] pnp 00:06: [io  0x0067]
[    1.188755] pnp 00:06: [io  0x0070]
[    1.188757] pnp 00:06: [io  0x0080]
[    1.188758] pnp 00:06: [io  0x0092]
[    1.188759] pnp 00:06: [io  0x00b2-0x00b3]
[    1.188761] pnp 00:06: [io  0x0200-0x027f]
[    1.188762] pnp 00:06: [io  0x1000-0x100f]
[    1.188763] pnp 00:06: [io  0xffff]
[    1.188765] pnp 00:06: [io  0xffff]
[    1.188766] pnp 00:06: [io  0x0400-0x047f]
[    1.188767] pnp 00:06: [io  0x0500-0x057f]
[    1.188769] pnp 00:06: [io  0xef80-0xef9f]
[    1.188812] system 00:06: [io  0x0200-0x027f] has been reserved
[    1.188814] system 00:06: [io  0x1000-0x100f] has been reserved
[    1.188816] system 00:06: [io  0xffff] has been reserved
[    1.188817] system 00:06: [io  0xffff] has been reserved
[    1.188819] system 00:06: [io  0x0400-0x047f] has been reserved
[    1.188821] system 00:06: [io  0x0500-0x057f] has been reserved
[    1.188823] system 00:06: [io  0xef80-0xef9f] has been reserved
[    1.188825] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.188832] pnp 00:07: [io  0x0070-0x0077]
[    1.188838] pnp 00:07: [irq 8]
[    1.188865] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.188873] pnp 00:08: [io  0x0060]
[    1.188874] pnp 00:08: [io  0x0064]
[    1.188879] pnp 00:08: [irq 1]
[    1.188905] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.188914] pnp 00:09: [irq 12]
[    1.188942] pnp 00:09: Plug and Play ACPI device, IDs SYN0168 SYN0100 SYN0002 PNP0f13 (active)
[    1.189136] pnp 00:0a: [irq 23]
[    1.189174] pnp 00:0a: Plug and Play ACPI device, IDs HPQ0004 (active)
[    1.189288] pnp 00:0b: [bus ff]
[    1.189325] pnp 00:0b: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.189405] pnp: PnP ACPI: found 12 devices
[    1.189406] ACPI: ACPI bus type pnp unregistered
[    1.196106] pci 0000:44:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    1.196113] PCI: max bus depth: 1 pci_try_num: 2
[    1.196164] pci 0000:00:1c.1: BAR 15: assigned [mem 0x7c100000-0x7c2fffff 64bit pref]
[    1.196166] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.196172] pci 0000:00:1c.0:   bridge window [mem 0x94800000-0x948fffff]
[    1.196182] pci 0000:00:1c.1: PCI bridge to [bus 02-42]
[    1.196185] pci 0000:00:1c.1:   bridge window [io  0x3000-0x4fff]
[    1.196191] pci 0000:00:1c.1:   bridge window [mem 0x90800000-0x947fffff]
[    1.196196] pci 0000:00:1c.1:   bridge window [mem 0x7c100000-0x7c2fffff 64bit pref]
[    1.196204] pci 0000:00:1c.3: PCI bridge to [bus 43-43]
[    1.196209] pci 0000:00:1c.3:   bridge window [mem 0x90700000-0x907fffff]
[    1.196220] pci 0000:44:00.0: BAR 6: assigned [mem 0x90420000-0x9043ffff pref]
[    1.196222] pci 0000:00:1c.5: PCI bridge to [bus 44-44]
[    1.196226] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    1.196231] pci 0000:00:1c.5:   bridge window [mem 0x90600000-0x906fffff]
[    1.196236] pci 0000:00:1c.5:   bridge window [mem 0x90400000-0x904fffff 64bit pref]
[    1.196243] pci 0000:00:1e.0: PCI bridge to [bus 45-45]
[    1.196249] pci 0000:00:1e.0:   bridge window [mem 0x90500000-0x905fffff]
[    1.196273] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.196279] pci 0000:00:1c.0: setting latency timer to 64
[    1.196291] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.196296] pci 0000:00:1c.1: setting latency timer to 64
[    1.196306] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.196310] pci 0000:00:1c.3: setting latency timer to 64
[    1.196317] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.196322] pci 0000:00:1c.5: setting latency timer to 64
[    1.196330] pci 0000:00:1e.0: setting latency timer to 64
[    1.196334] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.196336] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.196338] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.196339] pci_bus 0000:00: resource 7 [mem 0x7c000000-0xdfffffff]
[    1.196341] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfedfffff]
[    1.196343] pci_bus 0000:00: resource 9 [mem 0xfee01000-0xffffffff]
[    1.196345] pci_bus 0000:01: resource 1 [mem 0x94800000-0x948fffff]
[    1.196347] pci_bus 0000:02: resource 0 [io  0x3000-0x4fff]
[    1.196348] pci_bus 0000:02: resource 1 [mem 0x90800000-0x947fffff]
[    1.196350] pci_bus 0000:02: resource 2 [mem 0x7c100000-0x7c2fffff 64bit pref]
[    1.196352] pci_bus 0000:43: resource 1 [mem 0x90700000-0x907fffff]
[    1.196354] pci_bus 0000:44: resource 0 [io  0x2000-0x2fff]
[    1.196356] pci_bus 0000:44: resource 1 [mem 0x90600000-0x906fffff]
[    1.196358] pci_bus 0000:44: resource 2 [mem 0x90400000-0x904fffff 64bit pref]
[    1.196360] pci_bus 0000:45: resource 1 [mem 0x90500000-0x905fffff]
[    1.196362] pci_bus 0000:45: resource 4 [io  0x0000-0x0cf7]
[    1.196364] pci_bus 0000:45: resource 5 [io  0x0d00-0xffff]
[    1.196366] pci_bus 0000:45: resource 6 [mem 0x000a0000-0x000bffff]
[    1.196368] pci_bus 0000:45: resource 7 [mem 0x7c000000-0xdfffffff]
[    1.196369] pci_bus 0000:45: resource 8 [mem 0xf0000000-0xfedfffff]
[    1.196371] pci_bus 0000:45: resource 9 [mem 0xfee01000-0xffffffff]
[    1.196404] NET: Registered protocol family 2
[    1.196499] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    1.196979] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    1.198190] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.198490] TCP: Hash tables configured (established 262144 bind 65536)
[    1.198493] TCP reno registered
[    1.198502] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    1.198515] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    1.198613] NET: Registered protocol family 1
[    1.198628] pci 0000:00:02.0: Boot video device
[    1.198647] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.198677] pci 0000:00:1a.0: PCI INT A disabled
[    1.198708] pci 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.198727] pci 0000:00:1d.0: PCI INT A disabled
[    1.198755] PCI: CLS 64 bytes, default 64
[    1.199245] audit: initializing netlink socket (disabled)
[    1.199256] type=2000 audit(1338848506.040:1): initialized
[    1.224066] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.233710] VFS: Disk quotas dquot_6.5.2
[    1.233762] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.234216] fuse init (API version 7.17)
[    1.234296] msgmni has been set to 3714
[    1.234738] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.234774] io scheduler noop registered
[    1.234776] io scheduler deadline registered
[    1.234803] io scheduler cfq registered (default)
[    1.234911] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.234971] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.235053] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.235102] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    1.235189] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.235237] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    1.235316] pcieport 0000:00:1c.5: setting latency timer to 64
[    1.235364] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    1.235469] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.235474] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.235492] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    1.235497] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    1.235515] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    1.235517] pci 0000:43:00.0: Signaling PME through PCIe PME interrupt
[    1.235521] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    1.235540] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    1.235542] pci 0000:44:00.0: Signaling PME through PCIe PME interrupt
[    1.235547] pcie_pme 0000:00:1c.5cie01: service driver pcie_pme loaded
[    1.235559] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.235620] pciehp 0000:00:1c.1cie04: HPC vendor_id 8086 device_id 3b44 ss_vid 103c ss_did 1423
[    1.235640] pciehp 0000:00:1c.1cie04: service driver pciehp loaded
[    1.235651] pciehp 0000:00:1c.5cie04: HPC vendor_id 8086 device_id 3b4c ss_vid 103c ss_did 1423
[    1.235668] pciehp 0000:00:1c.5cie04: service driver pciehp loaded
[    1.235673] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.235714] intel_idle: MWAIT substates: 0x1120
[    1.235715] intel_idle: v0.4 model 0x25
[    1.235716] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.235923] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.236007] ACPI: AC Adapter [AC] (off-line)
[    1.236181] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    1.236186] ACPI: Sleep Button [SLPB]
[    1.236219] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.236240] ACPI: Lid Switch [LID]
[    1.236272] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.236275] ACPI: Power Button [PWRF]
[    1.243683] thermal LNXTHERM:00: registered as thermal_zone0
[    1.243685] ACPI: Thermal Zone [EXTZ] (34 C)
[    1.243724] thermal LNXTHERM:01: registered as thermal_zone1
[    1.243726] ACPI: Thermal Zone [EX2Z] (0 C)
[    1.243766] thermal LNXTHERM:02: registered as thermal_zone2
[    1.243767] ACPI: Thermal Zone [PWMZ] (0 C)
[    1.246284] thermal LNXTHERM:03: registered as thermal_zone3
[    1.246286] ACPI: Thermal Zone [LOCZ] (34 C)
[    1.246658] thermal LNXTHERM:04: registered as thermal_zone4
[    1.246660] ACPI: Thermal Zone [GFXZ] (0 C)
[    1.256693] thermal LNXTHERM:05: registered as thermal_zone5
[    1.256695] ACPI: Thermal Zone [BATZ] (34 C)
[    1.266408] thermal LNXTHERM:06: registered as thermal_zone6
[    1.266410] ACPI: Thermal Zone [EGXZ] (0 C)
[    1.266583] thermal LNXTHERM:07: registered as thermal_zone7
[    1.266585] ACPI: Thermal Zone [CPUZ] (43 C)
[    1.266726] thermal LNXTHERM:08: registered as thermal_zone8
[    1.266728] ACPI: Thermal Zone [MCHZ] (45 C)
[    1.266866] thermal LNXTHERM:09: registered as thermal_zone9
[    1.266867] ACPI: Thermal Zone [PCHZ] (59 C)
[    1.266886] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.266895] ACPI: Battery Slot [BAT0] (battery present)
[    1.266927] ERST: Table is not found!
[    1.266929] GHES: HEST is not enabled!
[    1.267013] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.313413] ACPI: Battery Slot [BAT0] (battery present)
[    1.434106] Linux agpgart interface v0.103
[    1.434169] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.434239] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.434952] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.435095] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[    1.436369] brd: module loaded
[    1.437024] loop: module loaded
[    1.437141] ahci 0000:00:1f.2: version 3.0
[    1.437163] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.437210] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.437246] ahci: SSS flag set, parallel bus scan disabled
[    1.437288] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
[    1.437291] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.437297] ahci 0000:00:1f.2: setting latency timer to 64
[    1.450166] scsi0 : ahci
[    1.450250] scsi1 : ahci
[    1.450319] scsi2 : ahci
[    1.450387] scsi3 : ahci
[    1.450456] scsi4 : ahci
[    1.450521] scsi5 : ahci
[    1.450656] ata1: SATA max UDMA/133 abar m2048@0x94907000 port 0x94907100 irq 44
[    1.450659] ata2: SATA max UDMA/133 abar m2048@0x94907000 port 0x94907180 irq 44
[    1.450661] ata3: DUMMY
[    1.450662] ata4: DUMMY
[    1.450664] ata5: SATA max UDMA/133 abar m2048@0x94907000 port 0x94907300 irq 44
[    1.450666] ata6: DUMMY
[    1.450998] Fixed MDIO Bus: probed
[    1.451013] tun: Universal TUN/TAP device driver, 1.6
[    1.451014] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.451065] PPP generic driver version 2.4.2
[    1.451159] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.451175] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.451188] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.451191] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.451231] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.451258] ehci_hcd 0000:00:1a.0: debug port 2
[    1.455138] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.455154] ehci_hcd 0000:00:1a.0: irq 16, io mem 0x94909000
[    1.469680] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.469823] hub 1-0:1.0: USB hub found
[    1.469827] hub 1-0:1.0: 2 ports detected
[    1.469883] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.469894] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.469898] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.469938] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.469964] ehci_hcd 0000:00:1d.0: debug port 2
[    1.473849] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.473862] ehci_hcd 0000:00:1d.0: irq 20, io mem 0x94908000
[    1.489647] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.489779] hub 2-0:1.0: USB hub found
[    1.489782] hub 2-0:1.0: 2 ports detected
[    1.489830] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.489839] uhci_hcd: USB Universal Host Controller Interface driver
[    1.489875] usbcore: registered new interface driver libusual
[    1.489908] i8042: PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
[    1.491635] i8042: Detected active multiplexing controller, rev 1.1
[    1.492351] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.492357] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.492381] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.492398] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.492418] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.492516] mousedev: PS/2 mouse device common for all mice
[    1.492685] rtc_cmos 00:07: RTC can wake from S4
[    1.492797] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.492828] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.492886] device-mapper: uevent: version 1.0.3
[    1.492950] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.493030] cpuidle: using governor ladder
[    1.493148] cpuidle: using governor menu
[    1.493150] EFI Variables Facility v0.08 2004-May-17
[    1.493336] TCP cubic registered
[    1.493419] NET: Registered protocol family 10
[    1.493822] NET: Registered protocol family 17
[    1.493834] Registering the dns_resolver key type
[    1.493979] PM: Hibernation image not present or could not be loaded.
[    1.493990] registered taskstats version 1
[    1.508038]   Magic number: 0:457:400
[    1.508200] rtc_cmos 00:07: setting system clock to 2012-06-04 22:21:47 UTC (1338848507)
[    1.508986] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.508987] EDD information not available.
[    1.514568] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.781262] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.825196] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.826052] ata1.00: unexpected _GTF length (8)
[    1.826211] ata1.00: ATA-8: TOSHIBA MK3256GSY, LH013C, max UDMA/100
[    1.826216] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.827228] ata1.00: unexpected _GTF length (8)
[    1.827402] ata1.00: configured for UDMA/100
[    1.827774] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3256GS LH01 PQ: 0 ANSI: 5
[    1.828002] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.828008] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.828169] sd 0:0:0:0: [sda] Write Protect is off
[    1.828172] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.828239] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.913867] hub 1-1:1.0: USB hub found
[    1.914064] hub 1-1:1.0: 6 ports detected
[    1.925764]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.927966] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.024858] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.144696] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.148459] ata2.00: unexpected _GTF length (
[    2.148465] ata2.00: ATAPI: hp      DVDRAM GT31L, mP01, max UDMA/100
[    2.152499] ata2.00: unexpected _GTF length (
[    2.152507] ata2.00: configured for UDMA/100
[    2.155506] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT31L     mP01 PQ: 0 ANSI: 5
[    2.157763] hub 2-1:1.0: USB hub found
[    2.157943] hub 2-1:1.0: 8 ports detected
[    2.159629] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.159636] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.159926] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.160104] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.196614] Refined TSC clocksource calibration: 2399.970 MHz.
[    2.196621] Switching to clocksource tsc
[    2.228700] usb 1-1.3: new full-speed USB device number 3 using ehci_hcd
[    2.392425] usb 1-1.5: new high-speed USB device number 4 using ehci_hcd
[    2.480154] ata5: SATA link down (SStatus 0 SControl 300)
[    2.481911] Freeing unused kernel memory: 920k freed
[    2.482057] Write protecting the kernel read-only data: 12288k
[    2.487085] Freeing unused kernel memory: 1608k freed
[    2.490925] Freeing unused kernel memory: 1196k freed
[    2.509525] udevd[107]: starting version 175
[    2.554148] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.554177] r8169 0000:44:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.554216] r8169 0000:44:00.0: setting latency timer to 64
[    2.554286] r8169 0000:44:00.0: irq 45 for MSI/MSI-X
[    2.554864] r8169 0000:44:00.0: eth0: RTL8168d/8111d at 0xffffc9000036a000, 60:eb:69:12:a8:fa, XID 083000c0 IRQ 45
[    2.554868] r8169 0000:44:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    3.052834] EXT3-fs (sda3): recovery required on readonly filesystem
[    3.052840] EXT3-fs (sda3): write access will be enabled during recovery
[    9.043468] kjournald starting.  Commit interval 5 seconds
[    9.043531] EXT3-fs (sda3): recovery complete
[    9.044987] EXT3-fs (sda3): mounted filesystem with ordered data mode
[   11.632851] atkbd serio0: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   11.632856] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
[   11.744384] atkbd serio0: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   11.744391] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
[   12.254177] atkbd serio0: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[   12.254184] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
[   12.344843] atkbd serio0: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[   12.344849] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
[   21.700774] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.718390] udevd[352]: starting version 175
[   21.776240] wmi: Mapper loaded
[   21.783095] hp_accel: hardware type HPB442x found
[   21.783752] lis3lv02d: 8 bits sensor found
[   21.797931] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   21.798391] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.798398] mei 0000:00:16.0: setting latency timer to 64
[   21.798471] mei 0000:00:16.0: irq 46 for MSI/MSI-X
[   21.817402] EXT3-fs (sda3): using internal journal
[   21.820009] Linux video capture interface: v2.00
[   21.820905] uvcvideo: Found UVC 1.00 device HP Webcam [2 MP Fixed] (05c8:0403)
[   21.826441] cfg80211: Calling CRDA to update world regulatory domain
[   21.837182] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   21.837757] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input4
[   21.838417] Registered led device: hp::hddprotect
[   21.838528] hp_accel: driver loaded
[   21.839015] input: HP Webcam [2 MP Fixed] as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input5
[   21.839301] usbcore: registered new interface driver uvcvideo
[   21.839304] USB Video Class driver (1.1.1)
[   21.840401] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   21.840457] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   21.846015] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   21.850072] brcmsmac 0000:43:00.0: bus 67 slot 0 func 0 irq 10
[   21.850094] brcmsmac 0000:43:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   21.850103] brcmsmac 0000:43:00.0: setting latency timer to 64
[   21.851462] [drm] Initialized drm 1.1.0 20060810
[   21.860765] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.860772] i915 0000:00:02.0: setting latency timer to 64
[   21.861707] type=1400 audit(1338828727.883:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=568 comm="apparmor_parser"
[   21.862158] type=1400 audit(1338828727.883:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=568 comm="apparmor_parser"
[   21.862458] type=1400 audit(1338828727.883:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=568 comm="apparmor_parser"
[   21.900156] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   21.900162] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   21.900164] [drm] Driver supports precise vblank timestamp query.
[   21.900210] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   22.009723] cfg80211: World regulatory domain updated:
[   22.009726] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.009729] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.009732] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.009735] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.009737] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.009740] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029515] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   22.029519] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029522] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   22.029525] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029527] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   22.029530] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029532] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   22.029535] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029538] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   22.029541] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029543] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   22.029545] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029548] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   22.029550] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029553] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   22.029556] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029558] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   22.029562] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029564] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   22.029567] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029569] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   22.029571] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029573] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   22.029575] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.029577] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   22.029579] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.029581] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   22.029584] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.029586] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   22.029588] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029590] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   22.029592] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029594] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   22.029596] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029598] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   22.029600] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029602] cfg80211: Disabling freq 5260 MHz
[   22.029603] cfg80211: Disabling freq 5280 MHz
[   22.029604] cfg80211: Disabling freq 5300 MHz
[   22.029606] cfg80211: Disabling freq 5320 MHz
[   22.029607] cfg80211: Disabling freq 5500 MHz
[   22.029608] cfg80211: Disabling freq 5520 MHz
[   22.029609] cfg80211: Disabling freq 5540 MHz
[   22.029611] cfg80211: Disabling freq 5560 MHz
[   22.029612] cfg80211: Disabling freq 5580 MHz
[   22.029613] cfg80211: Disabling freq 5600 MHz
[   22.029614] cfg80211: Disabling freq 5620 MHz
[   22.029616] cfg80211: Disabling freq 5640 MHz
[   22.029617] cfg80211: Disabling freq 5660 MHz
[   22.029618] cfg80211: Disabling freq 5680 MHz
[   22.029619] cfg80211: Disabling freq 5700 MHz
[   22.029621] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   22.029623] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029625] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   22.029627] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029629] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   22.029632] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029633] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   22.029636] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.029637] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   22.029640] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.031792] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   22.033265] lib80211: common routines for IEEE802.11 drivers
[   22.033268] lib80211_crypt: registered algorithm 'NULL'
[   22.035101] wl: module license 'MIXED/Proprietary' taints kernel.
[   22.035106] Disabling lock debugging due to kernel taint
[   22.038955] cfg80211: Calling CRDA for country: DE
[   22.047076] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   22.047080] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047082] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   22.047085] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047087] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   22.047090] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047092] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   22.047094] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047096] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   22.047099] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047101] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   22.047103] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047105] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   22.047108] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047110] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   22.047113] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047115] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   22.047118] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047120] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   22.047123] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047125] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   22.047128] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047130] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   22.047133] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047135] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   22.047138] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047140] cfg80211: Disabling freq 2484 MHz
[   22.047142] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   22.047146] cfg80211: 5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047148] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   22.047151] cfg80211: 5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047153] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   22.047156] cfg80211: 5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047158] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   22.047161] cfg80211: 5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047163] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   22.047166] cfg80211: 5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047168] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   22.047171] cfg80211: 5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047174] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   22.047176] cfg80211: 5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047178] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   22.047181] cfg80211: 5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   22.047183] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[   22.047186] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047189] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[   22.047191] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047194] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[   22.047197] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047199] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[   22.047202] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047204] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[   22.047207] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047210] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[   22.047213] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047215] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[   22.047218] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047221] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[   22.047224] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047226] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[   22.047229] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047232] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[   22.047235] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047237] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[   22.047240] cfg80211: 5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A mBi, 2698 mBm)
[   22.047242] cfg80211: Disabling freq 5745 MHz
[   22.047244] cfg80211: Disabling freq 5765 MHz
[   22.047246] cfg80211: Disabling freq 5785 MHz
[   22.047248] cfg80211: Disabling freq 5805 MHz
[   22.047249] cfg80211: Disabling freq 5825 MHz
[   22.047254] cfg80211: Regulatory domain changed to country: DE
[   22.047256] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.047259] cfg80211:     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.047262] cfg80211:     (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.047265] cfg80211:     (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.047267] cfg80211:     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   22.121413] input: HP WMI hotkeys as /devices/virtual/input/input6
[   22.173835] init: failsafe main process (759) killed by TERM signal
[   22.190043] Bluetooth: Core ver 2.16
[   22.190093] NET: Registered protocol family 31
[   22.190096] Bluetooth: HCI device and connection manager initialized
[   22.190099] Bluetooth: HCI socket layer initialized
[   22.190101] Bluetooth: L2CAP socket layer initialized
[   22.190113] Bluetooth: SCO socket layer initialized
[   22.201717] lp: driver loaded but no devices found
[   22.201770] Bluetooth: RFCOMM TTY layer initialized
[   22.201776] Bluetooth: RFCOMM socket layer initialized
[   22.201778] Bluetooth: RFCOMM ver 1.11
[   22.204330] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.204334] Bluetooth: BNEP filters: protocol multicast
[   22.210204] ppdev: user-space parallel port driver
[   22.236250] type=1400 audit(1338828728.255:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=897 comm="apparmor_parser"
[   22.237006] type=1400 audit(1338828728.259:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=897 comm="apparmor_parser"
[   22.253644] type=1400 audit(1338828728.275:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=927 comm="apparmor_parser"
[   22.254075] type=1400 audit(1338828728.275:: apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=927 comm="apparmor_parser"
[   22.254323] type=1400 audit(1338828728.275:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=927 comm="apparmor_parser"
[   22.256816] type=1400 audit(1338828728.275:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=926 comm="apparmor_parser"
[   22.257797] type=1400 audit(1338828728.279:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=930 comm="apparmor_parser"
[   22.305102] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   22.305107] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   22.306536] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   22.306751] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.307209] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.363513] r8169 0000:44:00.0: eth0: link down
[   22.363736] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.364227] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.444799] fbcon: inteldrmfb (fb0) is primary device
[   22.444998] Console: switching to colour frame buffer device 170x48
[   22.445029] fb0: inteldrmfb frame buffer device
[   22.445031] drm: registered panic notifier
[   22.703983] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04733/0xe40000/0x5a0400
[   22.746124] init: alsa-restore main process (987) terminated with status 19
[   22.751443] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   22.776148] init: anacron main process (1101) killed by TERM signal
[   22.956091] acpi device:0e: registered as cooling_device4
[   22.956403] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   22.956476] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   22.957077] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.962113] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[   22.962124] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[   22.962135] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.962223] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   22.962263] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   23.414158] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   24.026699] HDMI status: Codec=3 Pin=6 Presence_Detect=0 ELD_Valid=0
[   24.026785] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   24.027014] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   24.027158] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   27.037393] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   28.752555] usb 1-1.4: new low-speed USB device number 5 using ehci_hcd
[   28.868901] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input12
[   28.870685] generic-usb 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.4/input0
[   28.870826] usbcore: registered new interface driver usbhid
[   28.870829] usbhid: USB HID core driver
[   29.381500] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[   29.577421] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[   29.777109] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[   29.976791] wlan0: authentication with 00:15:e9:00:00:02 timed out
[   36.981711] kbd_keycode: 42 callbacks suppressed
[   36.981714] keyboard: can't emulate rawmode for keycode 247
[   37.142121] keyboard: can't emulate rawmode for keycode 247
[   38.080399] keyboard: can't emulate rawmode for keycode 247
[   38.191015] keyboard: can't emulate rawmode for keycode 247
[   41.468811] type=1400 audit(1338828747.519:26): apparmor="DENIED" operation="open" parent=1951 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1952 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   41.922896] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   41.922900] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   41.924309] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   41.924494] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.914713] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[   49.110532] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[   49.310279] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[   49.509955] wlan0: authentication with 00:15:e9:00:00:02 timed out
[   57.445155] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[   57.645071] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[   57.848792] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[   58.048495] wlan0: authentication with 00:15:e9:00:00:02 timed out
[   66.027708] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[   66.223596] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[   66.423300] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[   66.623003] wlan0: authentication with 00:15:e9:00:00:02 timed out
[   74.554192] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[   74.750135] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[   74.949852] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[   75.149537] wlan0: authentication with 00:15:e9:00:00:02 timed out
[   83.088940] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[   83.288684] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[   83.488357] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[   83.688029] wlan0: authentication with 00:15:e9:00:00:02 timed out
[   91.635426] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[   91.835163] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[   92.034879] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[   92.234547] wlan0: authentication with 00:15:e9:00:00:02 timed out
[  100.205899] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[  100.405697] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[  100.605368] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[  100.805047] wlan0: authentication with 00:15:e9:00:00:02 timed out
[  110.485831] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[  110.685446] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[  110.885161] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[  111.084783] wlan0: authentication with 00:15:e9:00:00:02 timed out
[  119.092248] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[  119.291850] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[  119.495507] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[  119.695230] wlan0: authentication with 00:15:e9:00:00:02 timed out
[  127.638515] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[  127.834415] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[  128.034107] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[  128.233753] wlan0: authentication with 00:15:e9:00:00:02 timed out
[  136.165157] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[  136.364955] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[  136.564609] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[  136.764256] wlan0: authentication with 00:15:e9:00:00:02 timed out
[  144.735849] wlan0: authenticate with 00:15:e9:00:00:02 (try 1)
[  144.935464] wlan0: authenticate with 00:15:e9:00:00:02 (try 2)
[  145.135135] wlan0: authenticate with 00:15:e9:00:00:02 (try 3)
[  145.334850] wlan0: authentication with 00:15:e9:00:00:02 timed out


[B]6 ) Network configuration

[/B]$ sudo lshw -C network

  *-network
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:43:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:82:c7:d3:92
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:90700000-90703fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:44:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:12:a8:fa
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.1.9 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:2000(size=256) memory:90404000-90404fff memory:90400000-90403fff memory:90420000-9043ffff


[B]7 ) Scan for networks:


[/B]$ iwlist scan

wlan0     No scan results


[B]8 ) Ubuntu Version: 

[/B]$ lsb_release -d

Description:    Ubuntu 12.04 LTS


[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 

[/B]$ uname -mr

3.2.0-23-generic x86_64


[B]10 ) Restarting the network:

[/B]$ sudo /etc/init.d/networking restart

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.


Any suggestion will be helpful  for me.

Thanks,

Sidharth

---

### Post by ibaiandi on 2012-06-05
I have the same problem with my HP Probook 4520s.
 
I hope someone will soon suggest something helpful...

---

### Post by virtualXTC on 2012-08-28
*bump*
I have the same problem, same computer (Probok 4420s).

The problem seems to be with encryption (it has no issues with unsecured networks).   The network I'm trying to connect to is using 'WPA2 Personal' mode with the 'TKIP' algorithm.  Are both of you trying to connect to a network with the same encryption types?

---

### Post by virtualXTC on 2012-08-28
The consensus on other [threads]("http://ubuntuforums.org/showthread.php?t=1608989") and [forums]("http://forums.linuxmint.com/viewtopic.php?f=53&t=70466") seems to be to install [the latest brodcom driver]("http://www.broadcom.com/support/802.11/linux_sta.php").

Unfortunately, even though I have the same computer (probook 4420s) my witless card is different: Atheros AR9285 PCI Express (rev 01) which is making me think it's actually a power management issue.

---

