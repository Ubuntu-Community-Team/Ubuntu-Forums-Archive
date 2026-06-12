---
title: "LUbuntu 15.04 Usb 2.0 not working"
date: 2015-07-12
forum: Hardware
---

### Post by lance bermudez on 2015-07-12
When first install was working now after update work for may be 5 minits then they shutoff. How do I fix?

uname
```

root@Tardis:~# uname -a
Linux Tardis 3.19.0-22-generic #22-Ubuntu SMP Tue Jun 16 17:15:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

lsb-release
```

root@Tardis:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"

```

lspci
```

root@Tardis:~# lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
01:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

```

lshw
```

tardis
    description: Computer
    width: 64 bits
    capabilities: smbios-2.8 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-generic:0 UNCLAIMED
          physical id: 0
          bus info: parisc@0
     *-generic:1 UNCLAIMED
          physical id: 2
          bus info: parisc@2
        *-generic UNCLAIMED
             physical id: 0
             bus info: parisc@0
     *-generic:2 UNCLAIMED
          physical id: 4
          bus info: parisc@4
     *-memory
          description: System memory
          physical id: 1
          size: 4860MiB
     *-cpu
          product: AMD A6-6310 APU with AMD Radeon R4 Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          size: 1GHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt topoext perfctr_nb perfctr_l2 arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshold vmmcall bmi1 xsaveopt cpufreq
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Mullins [Radeon R4/R5 Graphics]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:39 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:3000(size=256) memory:f0c00000-f0c3ffff memory:f0c80000-f0c9ffff
        *-multimedia:0
             description: Audio device
             product: Kabini HDMI/DP Audio
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:f0c60000-f0c63fff
        *-pci:0
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:f0b00000-f0bfffff
           *-generic
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom
                configuration: driver=rtsx_pci latency=0
                resources: irq:34 memory:f0b05000-f0b05fff memory:f0b10000-f0b1ffff
           *-network DISABLED
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.1
                bus info: pci@0000:01:00.1
                logical name: eth0
                version: 12
                serial: f0:76:1c:2a:c0:67
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=1Gbit/s
                resources: irq:37 ioport:2000(size=256) memory:f0b04000-f0b04fff memory:f0b00000-f0b03fff
        *-pci:1
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.4
             bus info: pci@0000:00:02.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:f0a00000-f0afffff
           *-network
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 30:10:b3:85:76:49
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.19.0-22-generic firmware=N/A ip=192.168.2.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:45 memory:f0a00000-f0a7ffff memory:f0a80000-f0a8ffff
        *-generic:0
             description: Encryption controller
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msix ht pm bus_master cap_list
             configuration: driver=AMD Cryptographic Coprocessor latency=0
             resources: irq:0 memory:f0c40000-f0c5ffff memory:f0900000-f09fffff memory:f0c70000-f0c70fff memory:f0c6a000-f0c6bfff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0c68000-f0c69fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 3.19.0-22-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 3.19
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 3.19.0-22-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: Mouse
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 16.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:36 ioport:3118(size=8) ioport:3124(size=4) ioport:3110(size=8) ioport:3120(size=4) ioport:3100(size=16) memory:f0c6f000-f0c6f3ff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:18 memory:f0c6e000-f0c6e0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Advanced Micro Devices, Inc.
                   physical id: 1
                   bus info: usb@3:1
                   version: 0.18
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Mouse
                      product: USB Receiver
                      vendor: Logitech
                      physical id: 1
                      bus info: usb@3:1.1
                      version: 16.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
                 *-usb:1
                      description: Bluetooth wireless interface
                      vendor: Lite-On Technology Corp.
                      physical id: 3
                      bus info: usb@3:1.3
                      version: 0.02
                      capabilities: bluetooth usb-1.10
                      configuration: driver=btusb maxpower=100mA speed=12Mbit/s
                 *-usb:2
                      description: Video
                      product: HD WebCam
                      vendor: Chicony Electronics Co.,Ltd.
                      physical id: 4
                      bus info: usb@3:1.4
                      version: 29.69
                      serial: 0001
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-usb:2
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:18 memory:f0c6d000-f0c6d0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Advanced Micro Devices, Inc.
                   physical id: 1
                   bus info: usb@4:1
                   version: 0.18
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Human interface device
                      physical id: 3
                      bus info: usb@4:1.3
                      version: 0.08
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:44 memory:f0c64000-f0c67fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-generic:1
             description: SD Host controller
             product: FCH SD Flash Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.7
             bus info: pci@0000:00:14.7
             version: 01
             width: 64 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=39
             resources: irq:16 memory:f0c6c000-f0c6c0ff
     *-pci:1
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 5
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10JPVX-22J
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A01
             serial: WD-WXW1E54UUAM6
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=0e73f036
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: a4b372c5-83f9-4870-9f7d-5f12311d9496
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2015-07-10 22:00:12 mount.fstype=ext2 mount.options=rw,relatime,stripe=4 mounted=2015-07-10 21:59:40 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 931GiB
                capacity: 931GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 931GiB


```

---

### Post by Vladlenin5000 on 2015-07-12
Have you installed the AMD proprietary drivers? You probably have to in order to have a stable system where everything else works. It isn't only for graphics, the proprietary blob also has 'something' chipset, hence USB, related...

---

### Post by Yellow Pasque on 2015-07-12
First of all, your hardware is really new, so get some updated, human-readable names for the lspci and lsusb output:
```
sudo update-pciids
sudo update-usbids
```

Second, look at ouput of lsusb while the devices are functioning. Then, when the USB problems arise, check lsusb again and also look at the end of dmesg:
```
dmesg | tail -n 20
```

> It isn't only for graphics, the proprietary blob also has 'something' chipset, hence USB, related... 
Do you have a source on that? I know that sometimes, one has to download AMD chipset drivers on Windows, but I've never heard of fglrx/Catalyst on Linux providing kernel modules/drivers for anything other than the GPU.

---

### Post by Vladlenin5000 on 2015-07-12
I am the source :lolflag:

No, seriously, since last year I've been dealing with a lot of low to mid range notebooks based on the new APUs and one common issue is non-working USBs (literally, they're as good as dead) after installation. They all started working after installing fglrx (Ubuntu recommend version in "Additional drivers") so, I infer, it must have something to do with it. Exactly what, up to this day, I'm not sure.

---

### Post by Yellow Pasque on 2015-07-12
Hmm, I guess it's possible with these new APU's/SoC's. I wish I had the money to buy new hardware for testing because the last integrated graphics system I had was an 880G/HD4250 laptop. LOL. I suck at making money/staying employed.

---

