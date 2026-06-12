---
title: "Touchpad not working with Vaio Z"
date: 2015-05-09
forum: Hardware
---

### Post by oualid on 2015-05-09
Hey Guys !
I just bought a Vaio Z 2015 from Japan and installed ubuntu 15.04 Gnome on it. So far I'm pretty happy with it since everything works super nicely but the trouchpad.
It is behaving as a regular mouse, so I can't two fingers scroll and so on.
Here is the output of the commands that might help someone more advanced than me :
```
xinput&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; VAIO0001:00 04F3:0400                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; NTRG0F0A:00 1B96:0F0A Pen                   id=11    [slave  pointer  (2)]
&#9116;   &#8627; NTRG0F0A:00 1B96:0F0A                       id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Front Camera                                id=8    [slave  keyboard (3)]
    &#8627; Rear Camera                                 id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
```

```
cat /proc/bus/input/devices I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=0bda Product=56f9 Version=0002
N: Name="Rear Camera"
P: Phys=usb-0000:00:14.0-3/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0003 Vendor=04f2 Product=b473 Version=3261
N: Name="Front Camera"
P: Phys=usb-0000:00:14.0-4/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input6
U: Uniq=
H: Handlers=event6 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=10


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0018 Vendor=04f3 Product=0400 Version=0100
N: Name="VAIO0001:00 04F3:0400"
P: Phys=
S: Sysfs=/devices/pci0000:00/INT3432:00/i2c-0/i2c-VAIO0001:00/0018:04F3:0400.0002/input/input9
U: Uniq=
H: Handlers=mouse0 event9 
B: PROP=0
B: EV=17
B: KEY=30000 0 0 0 0
B: REL=143
B: MSC=10


I: Bus=0018 Vendor=1b96 Product=0f0a Version=0100
N: Name="NTRG0F0A:00 1B96:0F0A Pen"
P: Phys=
S: Sysfs=/devices/pci0000:00/INT3433:00/i2c-1/i2c-NTRG0F0A:00/0018:1B96:0F0A.0003/input/input10
U: Uniq=
H: Handlers=mouse1 event10 
B: PROP=0
B: EV=1b
B: KEY=c03 1 0 0 0 0
B: ABS=1000003
B: MSC=10


I: Bus=0018 Vendor=1b96 Product=0f0a Version=0100
N: Name="NTRG0F0A:00 1B96:0F0A"
P: Phys=
S: Sysfs=/devices/pci0000:00/INT3433:00/i2c-1/i2c-NTRG0F0A:00/0018:1B96:0F0A.0003/input/input11
U: Uniq=
H: Handlers=mouse2 event11 
B: PROP=2
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=3273800000000003

```
Thanks to anyone driving me to the right direction ...

---

### Post by jlgatewood on 2016-02-16
Bumping because I have the same issue and don't really know where to begin.

Here is my `dmesg' in case it helps someone

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-16-generic (buildd@lcy01-07) (gcc version 5.2.1 20151003 (Ubuntu 5.2.1-21ubuntu2) ) #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 (Ubuntu 4.2.0-16.19-generic 4.2.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-generic root=UUID=31c69bcf-b9de-4f68-878a-9e5a9eec9ae1 ro i8042.reset i8042.nomux i8042.nopnp i8042.noloop quiet splash vt.handoff=7 init=/sbin/upstart
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 0x340 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000008a3c5fff] usable
[    0.000000] BIOS-e820: [mem 0x000000008a3c6000-0x000000008a43efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008a43f000-0x00000000aaebffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000aaec0000-0x00000000ab0bffff] type 20
[    0.000000] BIOS-e820: [mem 0x00000000ab0c0000-0x00000000acdaefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000acdaf000-0x00000000acf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000acf9f000-0x00000000acffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000acfff000-0x00000000acffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f80f8000-0x00000000f80f8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000044effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by Phoenix Technologies Ltd.
[    0.000000] efi:  ACPI=0xacffe000  ACPI 2.0=0xacffe014  SMBIOS=0xacd71000  ESRT=0xabe35000 
[    0.000000] esrt: Reserving ESRT space from 0x00000000abe35000 to 0x00000000abe35038.
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: VAIO Corporation VJZ13A/VAIO, BIOS R0181B6 02/19/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x44f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00C0000000 mask 7FC0000000 uncachable
[    0.000000]   1 base 00B0000000 mask 7FF0000000 uncachable
[    0.000000]   2 base 00AE000000 mask 7FFE000000 uncachable
[    0.000000]   3 base 00AD000000 mask 7FFF000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: last_pfn = 0xad000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02ff0000, 0x02ff0fff] PGTABLE
[    0.000000] BRK [0x02ff1000, 0x02ff1fff] PGTABLE
[    0.000000] BRK [0x02ff2000, 0x02ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x44ee00000-0x44effffff]
[    0.000000]  [mem 0x44ee00000-0x44effffff] page 2M
[    0.000000] BRK [0x02ff3000, 0x02ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x440000000-0x44edfffff]
[    0.000000]  [mem 0x440000000-0x44edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x420000000-0x43fffffff]
[    0.000000]  [mem 0x420000000-0x43fffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0x8a3c5fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0x8a1fffff] page 2M
[    0.000000]  [mem 0x8a200000-0x8a3c5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x8a43f000-0xaaebffff]
[    0.000000]  [mem 0x8a43f000-0x8a5fffff] page 4k
[    0.000000]  [mem 0x8a600000-0xaadfffff] page 2M
[    0.000000]  [mem 0xaae00000-0xaaebffff] page 4k
[    0.000000] BRK [0x02ff4000, 0x02ff4fff] PGTABLE
[    0.000000] BRK [0x02ff5000, 0x02ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xacfff000-0xacffffff]
[    0.000000]  [mem 0xacfff000-0xacffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x41fffffff]
[    0.000000]  [mem 0x100000000-0x41fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x33dd6000-0x35ee2fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000ACFFE014 000024 (v02 VAIO  )
[    0.000000] ACPI: XSDT 0x00000000ACFFE1C0 0000FC (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: FACP 0x00000000ACFFB000 00010C (v05 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: DSDT 0x00000000ACFE3000 013146 (v02 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: FACS 0x00000000ACF9B000 000040
[    0.000000] ACPI: ASF! 0x00000000ACFFD000 0000A5 (v32 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: HPET 0x00000000ACFFC000 000038 (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: LPIT 0x00000000ACFFA000 000094 (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: APIC 0x00000000ACFF9000 000098 (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: MCFG 0x00000000ACFF8000 00003C (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: WDAT 0x00000000ACFF7000 000104 (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: SSDT 0x00000000ACFE2000 000250 (v02 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000ACFE1000 000542 (v02 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000ACFDF000 001260 (v01 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000ACFDE000 00032B (v02 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000ACFDD000 000539 (v02 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000ACFDC000 000B74 (v02 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000ACFD6000 005DFB (v02 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: SSDT 0x00000000ACFD5000 000394 (v02 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: PCCT 0x00000000ACFD4000 00006E (v05 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: SSDT 0x00000000ACFD3000 000AC4 (v02 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: UEFI 0x00000000ACFD2000 000042 (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: MSDM 0x00000000ACF75000 000055 (v03 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: TPM2 0x00000000ACFD1000 000034 (v03 VAIO   VAIO     20150219      00000000)
[    0.000000] ACPI: SSDT 0x00000000ACFD0000 000671 (v01 VAIO   VAIO     20150219 INTL 20120711)
[    0.000000] ACPI: BATB 0x00000000ACFCF000 000046 (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: FPDT 0x00000000ACFCE000 000064 (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: UEFI 0x00000000ACFCD000 0002A6 (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: BGRT 0x00000000ACFCC000 000038 (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: CSRT 0x00000000ACFCB000 0000C4 (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: DMAR 0x00000000ACFCA000 0000CC (v01 VAIO   VAIO     20150219 PTEC 00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000044effffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x44eff8000-0x44effcfff]
[    0.000000]  [ffffea0000000000-ffffea00113fffff] PMD -> [ffff88043e600000-ffff88044e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000044effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009cfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000008a3c5fff]
[    0.000000]   node   0: [mem 0x000000008a43f000-0x00000000aaebffff]
[    0.000000]   node   0: [mem 0x00000000acfff000-0x00000000acffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000044effffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000044effffff]
[    0.000000] On node 0 totalpages: 4169187
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3995 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10874 pages used for memmap
[    0.000000]   DMA32 zone: 695880 pages, LIFO batch:31
[    0.000000]   Normal zone: 54208 pages used for memmap
[    0.000000]   Normal zone: 3469312 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xae000000-0xafffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8a3c6000-0x8a43efff]
[    0.000000] PM: Registered nosave memory: [mem 0xaaec0000-0xab0bffff]
[    0.000000] PM: Registered nosave memory: [mem 0xab0c0000-0xacdaefff]
[    0.000000] PM: Registered nosave memory: [mem 0xacdaf000-0xacf9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xacf9f000-0xacffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xad000000-0xadffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xae000000-0xafffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xb0000000-0xf80f7fff]
[    0.000000] PM: Registered nosave memory: [mem 0xf80f8000-0xf80f8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xf80f9000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xffffffff]
[    0.000000] e820: [mem 0xb0000000-0xf80f7fff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88044ec00000 s96728 r8192 d30248 u262144
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4104019
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-generic root=UUID=31c69bcf-b9de-4f68-878a-9e5a9eec9ae1 ro i8042.reset i8042.nomux i8042.nopnp i8042.noloop quiet splash vt.handoff=7 init=/sbin/upstart
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16231832K/16676748K available (8146K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 444916K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:760 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3092.945 MHz processor
[    0.000022] Calibrating delay loop (skipped), value calculated using timer frequency.. 6185.89 BogoMIPS (lpj=12371780)
[    0.000025] pid_max: default: 32768 minimum: 301
[    0.000028] ACPI: Core revision 20150619
[    0.016562] ACPI: All ACPI Tables successfully acquired
[    0.036272] Security Framework initialized
[    0.036282] AppArmor: AppArmor initialized
[    0.036283] Yama: becoming mindful.
[    0.037057] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.039531] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.040626] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.040640] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.040839] Initializing cgroup subsys blkio
[    0.040841] Initializing cgroup subsys memory
[    0.040846] Initializing cgroup subsys devices
[    0.040848] Initializing cgroup subsys freezer
[    0.040850] Initializing cgroup subsys net_cls
[    0.040852] Initializing cgroup subsys perf_event
[    0.040853] Initializing cgroup subsys net_prio
[    0.040855] Initializing cgroup subsys hugetlb
[    0.040873] CPU: Physical Processor ID: 0
[    0.040874] CPU: Processor Core ID: 0
[    0.040878] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.040879] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.041744] mce: CPU supports 7 MCE banks
[    0.041752] CPU0: Thermal monitoring handled by SMI
[    0.041758] process: using mwait in idle threads
[    0.041760] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.041761] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.042039] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.044828] ftrace: allocating 30905 entries in 121 pages
[    0.055328] DMAR: Host address width 39
[    0.055330] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.055335] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e1ff0505e
[    0.055336] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.055340] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.055341] DMAR: RMRR base: 0x000000ac8e7000 end: 0x000000ac8fdfff
[    0.055342] DMAR: RMRR base: 0x000000ad800000 end: 0x000000afffffff
[    0.055343] DMAR: ANDD device: 1 name: \_SB.PCI0.SDMA
[    0.055344] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.055345] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.055346] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.055347] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.055710] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.055711] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.056316] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.095996] TSC deadline timer enabled
[    0.095998] smpboot: CPU0: Intel(R) Core(TM) i7-5557U CPU @ 3.10GHz (fam: 06, model: 3d, stepping: 04)
[    0.096020] Performance Events: PEBS fmt2+, 16-deep LBR, Broadwell events, full-width counters, Intel PMU driver.
[    0.096036] ... version:                3
[    0.096037] ... bit width:              48
[    0.096037] ... generic registers:      4
[    0.096038] ... value mask:             0000ffffffffffff
[    0.096039] ... max period:             0000ffffffffffff
[    0.096039] ... fixed-purpose events:   3
[    0.096040] ... event mask:             000000070000000f
[    0.096662] x86: Booting SMP configuration:
[    0.096663] .... node  #0, CPUs:      #1
[    0.098663] CPU1: Thermal monitoring handled by SMI
[    0.100869] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.100931]  #2
[    0.102932] CPU2: Thermal monitoring handled by SMI
[    0.105103]  #3
[    0.107104] CPU3: Thermal monitoring handled by SMI
[    0.109220] x86: Booted up 1 node, 4 CPUs
[    0.109222] smpboot: Total of 4 processors activated (24743.56 BogoMIPS)
[    0.112912] devtmpfs: initialized
[    0.115100] evm: security.selinux
[    0.115101] evm: security.SMACK64
[    0.115102] evm: security.SMACK64EXEC
[    0.115102] evm: security.SMACK64TRANSMUTE
[    0.115103] evm: security.SMACK64MMAP
[    0.115103] evm: security.ima
[    0.115104] evm: security.capability
[    0.115153] PM: Registering ACPI NVS region [mem 0xacdaf000-0xacf9efff] (2031616 bytes)
[    0.115223] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.115285] pinctrl core: initialized pinctrl subsystem
[    0.115369] RTC time: 10:27:59, date: 02/17/16
[    0.115455] NET: Registered protocol family 16
[    0.125048] cpuidle: using governor ladder
[    0.129047] cpuidle: using governor menu
[    0.129120] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.129121] ACPI: bus type PCI registered
[    0.129123] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.129183] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.129185] PCI: not using MMCONFIG
[    0.129186] PCI: Using configuration type 1 for base access
[    0.137281] ACPI: Added _OSI(Module Device)
[    0.137283] ACPI: Added _OSI(Processor Device)
[    0.137283] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.137284] ACPI: Added _OSI(Processor Aggregator Device)
[    0.141806] ACPI: Executed 17 blocks of module-level executable AML code
[    0.245774] ACPI: Dynamic OEM Table Load:
[    0.245783] ACPI: SSDT 0xFFFF88043BD8F400 0003D3 (v02 PmRef  Cpu0Cst  00003001 INTL 20120711)
[    0.246400] ACPI: Dynamic OEM Table Load:
[    0.246408] ACPI: SSDT 0xFFFF88043BD93000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120711)
[    0.247061] ACPI: Dynamic OEM Table Load:
[    0.247068] ACPI: SSDT 0xFFFF88043BD86800 000119 (v02 PmRef  ApCst    00003000 INTL 20120711)
[    0.248256] ACPI : EC: EC started
[    0.250394] ACPI: Interpreter enabled
[    0.250401] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.250407] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.250412] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20150619/hwxface-580)
[    0.250425] ACPI: (supports S0 S4 S5)
[    0.250426] ACPI: Using IOAPIC for interrupt routing
[    0.250445] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.251626] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboard resources
[    0.251641] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.252476] ACPI: Power Resource [PG00] (on)
[    0.252771] ACPI: Power Resource [PG01] (on)
[    0.253065] ACPI: Power Resource [PG02] (on)
[    0.256128] ACPI: Power Resource [PX04] (on)
[    0.256536] ACPI: Power Resource [PX0C] (on)
[    0.257052] ACPI: Power Resource [PSEN] (on)
[    0.257097] ACPI: Power Resource [PXTC] (on)
[    0.310712] ACPI: Power Resource [PAUD] (on)
[    0.314676] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.314681] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.315321] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.315322] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.315846] PCI host bridge to bus 0000:00
[    0.315848] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.315850] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.315851] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.315852] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.315853] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff window]
[    0.315854] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff window]
[    0.315855] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff window]
[    0.315856] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
[    0.315857] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[    0.315858] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.315859] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.315860] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.315861] pci_bus 0000:00: root bus resource [mem 0xb0000000-0xfeafffff window]
[    0.315868] pci 0000:00:00.0: [8086:1604] type 00 class 0x060000
[    0.316062] pci 0000:00:02.0: [8086:162b] type 00 class 0x030000
[    0.316072] pci 0000:00:02.0: reg 0x10: [mem 0xd0000000-0xd0ffffff 64bit]
[    0.316077] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.316080] pci 0000:00:02.0: reg 0x20: [io  0x3000-0x303f]
[    0.316264] pci 0000:00:03.0: [8086:160c] type 00 class 0x040300
[    0.316273] pci 0000:00:03.0: reg 0x10: [mem 0xd1210000-0xd1213fff 64bit]
[    0.316476] pci 0000:00:14.0: [8086:9cb1] type 00 class 0x0c0330
[    0.316496] pci 0000:00:14.0: reg 0x10: [mem 0xd1200000-0xd120ffff 64bit]
[    0.316534] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.316695] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.316723] pci 0000:00:16.0: [8086:9cba] type 00 class 0x078000
[    0.316748] pci 0000:00:16.0: reg 0x10: [mem 0xd1219000-0xd121901f 64bit]
[    0.316795] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.316991] pci 0000:00:1b.0: [8086:9ca0] type 00 class 0x040300
[    0.317011] pci 0000:00:1b.0: reg 0x10: [mem 0xd1214000-0xd1217fff 64bit]
[    0.317049] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.317217] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.317244] pci 0000:00:1c.0: [8086:9c94] type 01 class 0x060400
[    0.317302] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.317480] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.317510] pci 0000:00:1c.5: [8086:9c9a] type 01 class 0x060400
[    0.317568] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.317744] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.317776] pci 0000:00:1f.0: [8086:9cc3] type 00 class 0x060100
[    0.318041] pci 0000:00:1f.3: [8086:9ca2] type 00 class 0x0c0500
[    0.318053] pci 0000:00:1f.3: reg 0x10: [mem 0xd1218000-0xd12180ff 64bit]
[    0.318069] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf]
[    0.318449] pci 0000:01:00.0: [8086:095a] type 00 class 0x028000
[    0.318555] pci 0000:01:00.0: reg 0x10: [mem 0xd1100000-0xd1101fff 64bit]
[    0.318788] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.318866] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.329163] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.329166] pci 0000:00:1c.0:   bridge window [mem 0xd1100000-0xd11fffff]
[    0.329282] pci 0000:02:00.0: [144d:a801] type 00 class 0x010601
[    0.329342] pci 0000:02:00.0: reg 0x24: [mem 0xd1000000-0xd1001fff]
[    0.329401] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.341089] pci 0000:00:1c.5: PCI bridge to [bus 02]
[    0.341093] pci 0000:00:1c.5:   bridge window [mem 0xd1000000-0xd10fffff]
[    0.349438] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.349476] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.349510] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.349544] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.349578] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.349612] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.349646] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.349680] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.349937] ACPI: Enabled 3 GPEs in block 00 to 7F
[    0.349972] ACPI : EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    0.350047] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.350049] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.350050] vgaarb: loaded
[    0.350051] vgaarb: bridge control possible 0000:00:02.0
[    0.350227] SCSI subsystem initialized
[    0.350261] libata version 3.00 loaded.
[    0.350276] ACPI: bus type USB registered
[    0.350288] usbcore: registered new interface driver usbfs
[    0.350294] usbcore: registered new interface driver hub
[    0.350306] usbcore: registered new device driver usb
[    0.350424] PCI: Using ACPI for IRQ routing
[    0.351553] PCI: pci_cache_line_size set to 64 bytes
[    0.351917] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.351918] e820: reserve RAM buffer [mem 0x0009d000-0x0009ffff]
[    0.351919] e820: reserve RAM buffer [mem 0x8a3c6000-0x8bffffff]
[    0.351919] e820: reserve RAM buffer [mem 0xaaec0000-0xabffffff]
[    0.351920] e820: reserve RAM buffer [mem 0xad000000-0xafffffff]
[    0.351921] e820: reserve RAM buffer [mem 0x44f000000-0x44fffffff]
[    0.351999] NetLabel: Initializing
[    0.351999] NetLabel:  domain hash size = 128
[    0.352000] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.352009] NetLabel:  unlabeled traffic allowed by default
[    0.352067] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.352070] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.354092] clocksource: Switched to clocksource hpet
[    0.358547] AppArmor: AppArmor Filesystem Enabled
[    0.358599] pnp: PnP ACPI init
[    0.358690] system 00:00: [io  0x1660-0x1667] has been reserved
[    0.358691] system 00:00: [io  0x2000-0x2007] has been reserved
[    0.358694] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.358976] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.358977] system 00:01: [io  0xffff] has been reserved
[    0.358978] system 00:01: [io  0xffff] has been reserved
[    0.358980] system 00:01: [io  0xffff] has been reserved
[    0.358981] system 00:01: [io  0x1800-0x18fe] could not be reserved
[    0.358982] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.358984] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.359015] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.359039] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.359041] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.359057] pnp 00:04: Plug and Play ACPI device, IDs VAI0002 PNP030b (active)
[    0.359391] system 00:05: [mem 0xfe102000-0xfe102fff] has been reserved
[    0.359393] system 00:05: [mem 0xfe104000-0xfe104fff] has been reserved
[    0.359394] system 00:05: [mem 0xfe106000-0xfe106fff] has been reserved
[    0.359396] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.360026] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.360028] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.360029] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.360030] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.360032] system 00:06: [mem 0xf8000000-0xfbffffff] could not be reserved
[    0.360033] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.360034] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.360035] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.360037] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.360038] system 00:06: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.360039] system 00:06: [mem 0xb0010000-0xb001ffff] has been reserved
[    0.360040] system 00:06: [mem 0xb0000000-0xb000ffff] has been reserved
[    0.360042] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.360213] pnp: PnP ACPI: found 7 devices
[    0.366051] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.366072] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.366076] pci 0000:00:1c.0:   bridge window [mem 0xd1100000-0xd11fffff]
[    0.366083] pci 0000:00:1c.5: PCI bridge to [bus 02]
[    0.366089] pci 0000:00:1c.5:   bridge window [mem 0xd1000000-0xd10fffff]
[    0.366096] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.366098] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.366099] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.366100] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
[    0.366101] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
[    0.366102] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
[    0.366103] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
[    0.366104] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
[    0.366105] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
[    0.366106] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
[    0.366107] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
[    0.366108] pci_bus 0000:00: resource 15 [mem 0xb0000000-0xfeafffff window]
[    0.366110] pci_bus 0000:01: resource 1 [mem 0xd1100000-0xd11fffff]
[    0.366111] pci_bus 0000:02: resource 1 [mem 0xd1000000-0xd10fffff]
[    0.366136] NET: Registered protocol family 2
[    0.366291] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.366455] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.366567] TCP: Hash tables configured (established 131072 bind 65536)
[    0.366594] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.366634] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.366696] NET: Registered protocol family 1
[    0.366707] pci 0000:00:02.0: Video device with shadowed ROM
[    0.367053] PCI: CLS 64 bytes, default 64
[    0.367090] Trying to unpack rootfs image as initramfs...
[    0.763106] Freeing initrd memory: 33844K (ffff880033dd6000 - ffff880035ee3000)
[    0.763132] DMAR: ACPI device "INTL9C60:00" under DMAR at fed91000 as 00:15.0
[    0.763139] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.763141] software IO TLB [mem 0xa6aed000-0xaaaed000] (64MB) mapped at [ffff8800a6aed000-ffff8800aaaecfff]
[    0.763204] RAPL PMU detected, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    0.763205] hw unit of domain pp0-core 2^-14 Joules
[    0.763206] hw unit of domain package 2^-14 Joules
[    0.763206] hw unit of domain dram 2^-14 Joules
[    0.763207] hw unit of domain pp1-gpu 2^-14 Joules
[    0.763286] microcode: CPU0 sig=0x306d4, pf=0x40, revision=0x18
[    0.763293] microcode: CPU1 sig=0x306d4, pf=0x40, revision=0x18
[    0.763299] microcode: CPU2 sig=0x306d4, pf=0x40, revision=0x18
[    0.763304] microcode: CPU3 sig=0x306d4, pf=0x40, revision=0x18
[    0.763345] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.763402] Scanning for low memory corruption every 60 seconds
[    0.763642] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.763663] Initialise system trusted keyring
[    0.763682] audit: initializing netlink subsys (disabled)
[    0.763693] audit: type=2000 audit(1455704879.748:1): initialized
[    0.763942] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.763943] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.764913] zpool: loaded
[    0.764915] zbud: loaded
[    0.765046] VFS: Disk quotas dquot_6.6.0
[    0.765068] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.765384] fuse init (API version 7.23)
[    0.765481] Key type big_key registered
[    0.765726] Key type asymmetric registered
[    0.765729] Asymmetric key parser 'x509' registered
[    0.765737] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.765766] io scheduler noop registered
[    0.765768] io scheduler deadline registered (default)
[    0.765787] io scheduler cfq registered
[    0.766114] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.766115] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.766119] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.766133] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.766134] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.766138] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    0.766142] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.766146] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.766171] efifb: probing for efifb
[    0.766179] efifb: framebuffer at 0xc0000000, mapped to 0xffffc90002000000, using 14400k, total 14400k
[    0.766180] efifb: mode is 2560x1440x32, linelength=10240, pages=1
[    0.766181] efifb: scrolling: redraw
[    0.766182] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.766266] Console: switching to colour frame buffer device 320x90
[    0.766291] fb0: EFI VGA frame buffer device
[    0.766298] intel_idle: MWAIT substates: 0x11142120
[    0.766298] intel_idle: v0.4 model 0x3D
[    0.766299] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.766497] ACPI: AC Adapter [ADP1] (off-line)
[    0.766544] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.766674] ACPI: Lid Switch [LID0]
[    0.766706] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.766708] ACPI: Power Button [PWRB]
[    0.767804] thermal LNXTHERM:00: registered as thermal_zone0
[    0.767806] ACPI: Thermal Zone [TZ01] (56 C)
[    0.768504] thermal LNXTHERM:01: registered as thermal_zone1
[    0.768505] ACPI: Thermal Zone [TZ02] (28 C)
[    0.768545] GHES: HEST is not enabled!
[    0.768639] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.770604] Linux agpgart interface v0.103
[    0.772103] brd: module loaded
[    0.772112] ACPI: Battery Slot [BAT1] (battery present)
[    0.772763] loop: module loaded
[    0.772918] libphy: Fixed MDIO Bus: probed
[    0.772920] tun: Universal TUN/TAP device driver, 1.6
[    0.772921] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.772955] PPP generic driver version 2.4.2
[    0.773074] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.773079] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.773145] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00009810
[    0.773150] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.773210] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.773212] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.773213] usb usb1: Product: xHCI Host Controller
[    0.773214] usb usb1: Manufacturer: Linux 4.2.0-16-generic xhci-hcd
[    0.773215] usb usb1: SerialNumber: 0000:00:14.0
[    0.773298] hub 1-0:1.0: USB hub found
[    0.773311] hub 1-0:1.0: 11 ports detected
[    0.775700] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.775703] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.775725] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.775727] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.775728] usb usb2: Product: xHCI Host Controller
[    0.775728] usb usb2: Manufacturer: Linux 4.2.0-16-generic xhci-hcd
[    0.775729] usb usb2: SerialNumber: 0000:00:14.0
[    0.775808] hub 2-0:1.0: USB hub found
[    0.775819] hub 2-0:1.0: 4 ports detected
[    0.776577] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.776580] ehci-pci: EHCI PCI platform driver
[    0.776587] ehci-platform: EHCI generic platform driver
[    0.776594] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.776596] ohci-pci: OHCI PCI platform driver
[    0.776603] ohci-platform: OHCI generic platform driver
[    0.776609] uhci_hcd: USB Universal Host Controller Interface driver
[    0.776625] i8042: PNP detection disabled
[    0.777552] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.777555] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.777652] mousedev: PS/2 mouse device common for all mice
[    0.777755] rtc_cmos 00:02: RTC can wake from S4
[    0.777868] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.777893] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.777899] i2c /dev entries driver
[    0.777952] device-mapper: uevent: version 1.0.3
[    0.778011] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.778024] Intel P-state driver initializing.
[    0.778138] ledtrig-cpu: registered to indicate activity on CPUs
[    0.778148] EFI Variables Facility v0.08 2004-May-17
[    0.787118] Error parsing PCC subspaces from PCCT
[    0.787261] NET: Registered protocol family 10
[    0.787397] NET: Registered protocol family 17
[    0.787406] Key type dns_resolver registered
[    0.787639] Loading compiled-in X.509 certificates
[    0.788152] Loaded X.509 cert 'Build time autogenerated kernel key: 6a1c9c21f04ab86fd1d7ced6ca113540fc8e35b6'
[    0.788162] registered taskstats version 1
[    0.788175] zswap: loading zswap
[    0.788176] zswap: using zbud pool
[    0.788179] zswap: using lzo compressor
[    0.790348] Key type trusted registered
[    0.792352] Key type encrypted registered
[    0.792357] AppArmor: AppArmor sha1 policy hashing enabled
[    0.792360] ima: No TPM chip found, activating TPM-bypass!
[    0.792373] evm: HMAC attrs: 0x1
[    0.792815]   Magic number: 4:238:477
[    0.792908] rtc_cmos 00:02: setting system clock to 2016-02-17 10:27:59 UTC (1455704879)
[    0.792955] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.792956] EDD information not available.
[    0.793016] PM: Hibernation image not present or could not be loaded.
[    0.793255] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    0.793256] Write protecting the kernel read-only data: 12288k
[    0.793367] Freeing unused kernel memory: 36K (ffff8800027f7000 - ffff880002800000)
[    0.793426] Freeing unused kernel memory: 296K (ffff880002bb6000 - ffff880002c00000)
[    0.800071] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.801802] random: systemd-udevd urandom read with 11 bits of entropy available
[    0.827898] sdhci: Secure Digital Host Controller Interface driver
[    0.827901] sdhci: Copyright(c) Pierre Ossman
[    0.830632] hidraw: raw HID events driver (C) Jiri Kosina
[    0.839032] wmi: Mapper loaded
[    0.844728] [drm] Initialized drm 1.1.0 20060810
[    0.847466] ahci 0000:02:00.0: version 3.0
[    0.862152] ahci 0000:02:00.0: AHCI 0001.0300 32 slots 1 ports 6 Gbps 0x1 impl SATA mode
[    0.862154] ahci 0000:02:00.0: flags: 64bit ncq led clo only pio ccc 
[    0.862407] scsi host0: ahci
[    0.862457] ata1: SATA max UDMA/133 abar m8192@0xd1000000 port 0xd1000100 irq 45
[    0.866151] [drm] Memory usable by graphics device = 4096M
[    0.866155] checking generic (c0000000 e10000) vs hw (c0000000 10000000)
[    0.866156] fb: switching to inteldrmfb from EFI VGA
[    0.866184] Console: switching to colour dummy device 80x25
[    0.866259] [drm] Replacing VGA console driver
[    0.872231] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.872232] [drm] Driver supports precise vblank timestamp query.
[    0.872353] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    0.886652] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[    0.886799] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[    0.887940] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    0.887959] fbcon: inteldrmfb (fb0) is primary device
[    0.888061] Console: switching to colour frame buffer device 320x90
[    0.888100] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    0.888101] i915 0000:00:02.0: registered panic notifier
[    0.888251] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    0.888332] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    0.986646] usb 2-3: new SuperSpeed USB device number 2 using xhci_hcd
[    1.085964] usb 1-4: new high-speed USB device number 2 using xhci_hcd
[    1.097478] usb 2-3: New USB device found, idVendor=0bda, idProduct=56f9
[    1.097480] usb 2-3: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.097482] usb 2-3: Product: Rear Camera
[    1.097483] usb 2-3: Manufacturer: Generic
[    1.097483] usb 2-3: SerialNumber: 200901010001
[    1.190151] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.191159] ata1.00: ATA-9: SAMSUNG MZHPV512HDGL-00000, BXW2500Q, max UDMA/133
[    1.191164] ata1.00: 1000215216 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.191635] ata1.00: configured for UDMA/133
[    1.191786] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MZHPV512 500Q PQ: 0 ANSI: 5
[    1.191936] sd 0:0:0:0: [sda] 1000215216 512-byte logical blocks: (512 GB/476 GiB)
[    1.191977] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.191982] sd 0:0:0:0: [sda] Write Protect is off
[    1.191984] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.192001] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.192965]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
[    1.193324] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.222512] usb 1-4: New USB device found, idVendor=04f2, idProduct=b473
[    1.222514] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.222515] usb 1-4: Product: Front Camera
[    1.222516] usb 1-4: Manufacturer: Chicony
[    1.389865] usb 1-5: new full-speed USB device number 3 using xhci_hcd
[    1.519828] usb 1-5: New USB device found, idVendor=8087, idProduct=0a2a
[    1.519830] usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.761865] tsc: Refined TSC clocksource calibration: 3092.844 MHz
[    1.761868] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2c94dffea94, max_idle_ns: 440795361700 ns
[    2.439631] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    2.500846] upstart: plymouth-upstart-bridge main process (234) killed by TERM signal
[    2.545388] Adding 16675836k swap on /dev/sda8.  Priority:-1 extents:1 across:16675836k SSFS
[    2.555754] random: nonblocking pool is initialized
[    2.621078] lp: driver loaded but no devices found
[    2.624938] ppdev: user-space parallel port driver
[    2.653127] tpm_crb MSFT0101:00: TPM2 ACPI table has a zero address for the control area
[    2.653133] tpm_crb: probe of MSFT0101:00 failed with error -22
[    2.664305] dw_dmac INTL9C60:00: DesignWare DMA Controller, 8 channels
[    2.755317] Bluetooth: Core ver 2.20
[    2.755330] NET: Registered protocol family 31
[    2.755332] Bluetooth: HCI device and connection manager initialized
[    2.755335] Bluetooth: HCI socket layer initialized
[    2.755337] Bluetooth: L2CAP socket layer initialized
[    2.755342] Bluetooth: SCO socket layer initialized
[    2.755671] media: Linux media interface: v0.10
[    2.759659] Linux video capture interface: v2.00
[    2.762034] clocksource: Switched to clocksource tsc
[    2.762107] usbcore: registered new interface driver btusb
[    2.776179] uvcvideo: Found UVC 1.00 device Rear Camera (0bda:56f9)
[    2.777652] Bluetooth: hci0: read Intel version: 370810011003110e00
[    2.778720] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[    2.790316] input: Rear Camera as /devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.0/input/input6
[    2.794740] uvcvideo: Found UVC 1.00 device Front Camera (04f2:b473)
[    2.802216] input: Front Camera as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input7
[    2.802325] usbcore: registered new interface driver uvcvideo
[    2.802326] USB Video Class driver (1.1.1)
[    2.809513] AVX2 version of gcm_enc/dec engaged.
[    2.809515] AES CTR mode by8 optimization enabled
[    2.848061] intel_rapl: Found RAPL domain package
[    2.848064] intel_rapl: Found RAPL domain core
[    2.848065] intel_rapl: Found RAPL domain uncore
[    2.848067] intel_rapl: Found RAPL domain dram
[    2.936757] audit: type=1400 audit(1455672481.637:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=481 comm="apparmor_parser"
[    2.936764] audit: type=1400 audit(1455672481.637:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=481 comm="apparmor_parser"
[    2.936768] audit: type=1400 audit(1455672481.637:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=481 comm="apparmor_parser"
[    2.936772] audit: type=1400 audit(1455672481.637:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=481 comm="apparmor_parser"
[    2.938607] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    3.492336] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.492554] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.496492] i2c_hid i2c-NTRG0F0A:00: error in i2c_hid_init_report size:9 / ret_size:0
[    3.497281] i2c_hid i2c-NTRG0F0A:00: error in i2c_hid_init_report size:5 / ret_size:0
[    3.498163] i2c_hid i2c-NTRG0F0A:00: error in i2c_hid_init_report size:5 / ret_size:259
[    3.501542] i2c_hid i2c-NTRG0F0A:00: error in i2c_hid_init_report size:8 / ret_size:259
[    3.502634] i2c_hid i2c-NTRG0F0A:00: error in i2c_hid_init_report size:15 / ret_size:259
[    3.506495] i2c_hid i2c-NTRG0F0A:00: error in i2c_hid_init_report size:4 / ret_size:0
[    3.517249] i2c_hid i2c-NTRG0F0A:00: error in i2c_hid_init_report size:63 / ret_size:0
[    3.518316] i2c_hid i2c-NTRG0F0A:00: error in i2c_hid_init_report size:7 / ret_size:0
[    3.519718] input: NTRG0F0A:00 1B96:0F0A Pen as /devices/pci0000:00/INT3433:00/i2c-6/i2c-NTRG0F0A:00/0018:1B96:0F0A.0003/input/input8
[    3.522818] input: NTRG0F0A:00 1B96:0F0A as /devices/pci0000:00/INT3433:00/i2c-6/i2c-NTRG0F0A:00/0018:1B96:0F0A.0003/input/input9
[    3.523002] snd_hda_codec_realtek hdaudioC1D0: ALC282: SKU not ready 0x411111f0
[    3.523481] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC282: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.523484] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.523486] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    3.523487] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[    3.523488] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[    3.523490] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x18
[    3.523491] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
[    3.524045] hid-multitouch 0018:1B96:0F0A.0003: input,hidraw0: <UNKNOWN> HID v1.00 Mouse [NTRG0F0A:00 1B96:0F0A] on 
[    3.526054] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input11
[    3.526212] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input12
[    3.526703] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input13
[    3.535476] i2c_hid i2c-VAIO0001:00: error in i2c_hid_init_report size:633 / ret_size:7
[    3.538311] i2c_hid i2c-VAIO0001:00: error in i2c_hid_init_report size:69 / ret_size:7
[    3.538559] input: VAIO0001:00 04F3:0400 as /devices/pci0000:00/INT3432:00/i2c-5/i2c-VAIO0001:00/0018:04F3:0400.0002/input/input16
[    3.541990] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
[    3.542017] hid-generic 0018:04F3:0400.0002: input,hidraw1: <UNKNOWN> HID v1.00 Mouse [VAIO0001:00 04F3:0400] on 
[    3.542077] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input15
[    3.551134] cfg80211: World regulatory domain updated:
[    3.551136] cfg80211:  DFS Master region: unset
[    3.551137] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    3.551139] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    3.551140] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    3.551140] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    3.551142] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    3.551143] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    3.551144] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    3.551145] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    3.551145] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    3.555551] Intel(R) Wireless WiFi driver for Linux
[    3.555553] Copyright(c) 2003- 2015 Intel Corporation
[    3.557302] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-15.ucode failed with error -2
[    3.557316] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-14.ucode failed with error -2
[    3.560285] iwlwifi 0000:01:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    3.576153] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    3.576481] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    3.576986] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    3.655158] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.656943] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    4.151515] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[    4.183193] upstart: Error while reading from descriptor: Broken pipe
[    4.183344] upstart: failsafe main process (603) killed by TERM signal
[    4.209511] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.209514] Bluetooth: BNEP filters: protocol multicast
[    4.209517] Bluetooth: BNEP socket layer initialized
[    4.218193] upstart: avahi-cups-reload main process (685) terminated with status 1
[    4.219833] audit: type=1400 audit(1455672482.921:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=689 comm="apparmor_parser"
[    4.219837] audit: type=1400 audit(1455672482.921:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=689 comm="apparmor_parser"
[    4.219840] audit: type=1400 audit(1455672482.921:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="third_party" pid=689 comm="apparmor_parser"
[    4.224757] audit: type=1400 audit(1455672482.925:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=699 comm="apparmor_parser"
[    4.224762] audit: type=1400 audit(1455672482.925:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=699 comm="apparmor_parser"
[    4.296458] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    4.296809] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    4.297266] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    4.357759] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    4.358199] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    4.380298] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    4.462610] systemd-logind[1062]: New seat seat0.
[    4.463090] systemd-logind[1062]: Watching system buttons on /dev/input/event3 (Video Bus)
[    4.463172] systemd-logind[1062]: Watching system buttons on /dev/input/event1 (Power Button)
[    4.463249] systemd-logind[1062]: Watching system buttons on /dev/input/event0 (Lid Switch)
[    4.479570] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    4.594305] systemd-logind[1062]: Failed to start user service: Unknown unit: user@119.service
[    4.597062] systemd-logind[1062]: New session c1 of user lightdm.
[    5.334469] Bluetooth: RFCOMM TTY layer initialized
[    5.334476] Bluetooth: RFCOMM socket layer initialized
[    5.334482] Bluetooth: RFCOMM ver 1.11
[    7.775320] wlp1s0: authenticate with 00:22:cf:20:bb:04
[    7.782503] wlp1s0: send auth to 00:22:cf:20:bb:04 (try 1/3)
[    7.805285] wlp1s0: authenticated
[    7.808173] wlp1s0: associate with 00:22:cf:20:bb:04 (try 1/3)
[    7.811978] wlp1s0: RX AssocResp from 00:22:cf:20:bb:04 (capab=0xc11 status=0 aid=1)
[    7.812538] wlp1s0: associated
[    7.812557] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[   13.146825] systemd-logind[1062]: Failed to start user service: Unknown unit: user@1000.service
[   13.149625] systemd-logind[1062]: New session c2 of user j7.
[   31.132961] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[   63.385597] [drm:gen8_irq_handler [i915]] *ERROR* The master control interrupt lied (SDE)!
[  125.109838] systemd-logind[1062]: Removed session c1.
[  354.743694] audit_printk_skb: 66 callbacks suppressed
[  354.743696] audit: type=1400 audit(1455672833.537:33): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=4098 comm="apparmor_parser"
[  354.743701] audit: type=1400 audit(1455672833.537:34): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=4098 comm="apparmor_parser"
[  354.753210] audit: type=1400 audit(1455672833.549:35): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=4098 comm="apparmor_parser"




```

---

