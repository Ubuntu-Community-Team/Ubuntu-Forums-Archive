---
title: "Lenovo Flex 6 14arr amd 2700u laptop touchpad"
date: 2019-04-18
forum: Hardware
---

### Post by arslin1 on 2019-04-18
Hello-

I have been running Linux (mostly ubuntu) off and on now for 15 years now. I tend to revert back to windows for games, but I am committed to Linux now. 

I have a new laptop that I have been trying to get the touchpad and touchscreen working on. It is my understanding that it the same as the Yoga 530. I have tried about 3 distro, countless kernels, and invested many hours. 

It is my understanding that the latest kernels should support my touchpad now, but I have not gotten it to work. 

I also have tried this module. that was fixing this problem before the kernel supported the hardware. 
[https://github.com/Syniurge/i2c-amd-mp2](https://github.com/Syniurge/i2c-amd-mp2)

I would greatly appreciate any help anyone could offer. All the other forum post I have read do not fix my problem... or I am missing something.

---

### Post by arslin1 on 2019-04-18
```
sudo lshw
[sudo] password for ******: 
lenovo-flex6                
    description: Convertible
    product: 81HA (LENOVO_MT_81HA_BU_idea_FM_ideapad FLEX 6-14ARR)
    vendor: LENOVO
    version: Lenovo ideapad FLEX 6-14ARR
    serial: PF1LPF3F
    width: 64 bits
    capabilities: smbios-3.1 dmi-3.1 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=convertible family=ideapad FLEX 6-14ARR frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=LENOVO_MT_81HA_BU_idea_FM_ideapad FLEX 6-14ARR uuid=40121CCD-A42D-E911-A225-E86A64B30CA4
  *-core
       description: Motherboard
       product: LNVNB161216
       vendor: LENOVO
       physical id: 0
       version: SDK0J40709 WIN
       serial: PF1LPF3F
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 8MCN45WW
          date: 08/17/2018
          size: 128KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb uefi
     *-cpu
          description: CPU
          product: AMD Ryzen 7 2700U with Radeon Vega Mobile Gfx
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Ryzen 7 2700U with Radeon Vega Mobile Gfx
          serial: Unknown
          slot: FP5
          size: 1433MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx hw_pstate sme ssbd sev ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov succor smca cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 - Cache
             size: 384KiB
             capacity: 384KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 - Cache
             size: 2MiB
             capacity: 2MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 - Cache
             size: 4MiB
             capacity: 4MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: HMA851S6CJR6N-VK
             vendor: Hynix
             physical id: 0
             serial: 2DCDDD51
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: HMA851S6CJR6N-VK
             vendor: Hynix
             physical id: 1
             serial: 2DCE73CB
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht bus_master cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:e0800000-e08fffff
           *-network DISABLED
                description: Wireless interface
                product: RTL8822BE 802.11a/b/g/n/ac WiFi adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 00
                serial: 0c:96:e6:c9:dc:9f
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=r8822be driverversion=4.18.0-10-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:71 ioport:2000(size=256) memory:e0800000-e080ffff
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.7
             bus info: pci@0000:00:01.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:e0700000-e07fffff
           *-storage
                description: Non-Volatile memory controller
                product: Sandisk Corp
                vendor: Sandisk Corp
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi msix pciexpress nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:48 memory:e0700000-e0703fff
        *-pci:2
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:1000(size=4096) memory:e0200000-e06fffff ioport:d0000000(size=270532608)
           *-display
                description: VGA compatible controller
                product: Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:03:00.0
                version: c3
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
                configuration: driver=amdgpu latency=0
                resources: irq:76 memory:d0000000-dfffffff memory:e0000000-e01fffff ioport:1000(size=256) memory:e0600000-e067ffff
           *-multimedia:0
                description: Audio device
                product: Advanced Micro Devices, Inc. [AMD/ATI]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:73 memory:e06c8000-e06cbfff
           *-generic:0 UNCLAIMED
                description: Encryption controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:03:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix cap_list
                configuration: latency=0
                resources: memory:e0500000-e05fffff memory:e06ce000-e06cffff
           *-usb:0
                description: USB controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:03:00.3
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:29 memory:e0400000-e04fffff
           *-usb:1
                description: USB controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.4
                bus info: pci@0000:03:00.4
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:38 memory:e0300000-e03fffff
           *-multimedia:1 UNCLAIMED
                description: Multimedia controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.5
                bus info: pci@0000:03:00.5
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:e0680000-e06bffff
           *-multimedia:2
                description: Audio device
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.6
                bus info: pci@0000:03:00.6
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:75 memory:e06c0000-e06c7fff
           *-generic:1
                description: Non-VGA unclassified device
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.7
                bus info: pci@0000:03:00.7
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list
                configuration: driver=pcie_mp2_amd latency=0
                resources: irq:29 memory:e0200000-e02fffff memory:e06cc000-e06cdfff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 61
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 51
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:08.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10a
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enx3c18a00f7b4e
       serial: 3c:18:a0:0f:7b:4e
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.09.9 duplex=full ip=10.50.35.144 link=yes multicast=yes port=MII speed=1Gbit/s
```

---

### Post by arslin1 on 2019-04-19
OK figured it out. Mostly followed this. 
[https://www.youtube.com/watch?v=xlpP8mS7dQo](https://www.youtube.com/watch?v=xlpP8mS7dQo)

> [COLOR=#0A0A0A][FONT=Roboto]sudo apt install git
git clone [/FONT][/COLOR][https://github.com/Syniurge/i2c-amd-mp2](https://github.com/Syniurge/i2c-amd-mp2)
[COLOR=#0A0A0A][FONT=Roboto]cd i2c-amd-mp2
sudo apt-get install dkms
sudo ./dkms-install.s

[/FONT][/COLOR]

I also ran this... not sure if it helped. 

[https://www.reddit.com/r/kernel/comments/9eb6yv/how_to_get_the_new_2018_lenovo_ideapad_330s/](https://www.reddit.com/r/kernel/comments/9eb6yv/how_to_get_the_new_2018_lenovo_ideapad_330s/)

I also edited grub according to this video:
[https://www.youtube.com/watch?v=ZAPSrbZvsjk](https://www.youtube.com/watch?v=ZAPSrbZvsjk)

---

