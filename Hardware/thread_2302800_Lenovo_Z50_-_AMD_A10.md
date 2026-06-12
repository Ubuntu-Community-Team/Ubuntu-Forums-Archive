---
title: "Lenovo Z50 - AMD A10"
date: 2015-11-13
forum: Hardware
---

### Post by IONx64 on 2015-11-13
Hello Dear Friends,

I have such issue on my above mentioned laptop. I have installed Ubuntu on it. when i watch movies display quality is bad. i look for drivers but there are no drivers for ubuntu on manufacturer website. what should do? tanks in advanced.

---

### Post by mörgæs on 2015-11-14
Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by IONx64 on 2015-11-15
> **mörgæs said:**
> Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Thanks for replay sir. 

computer
    description: Computer
    width: 64 bits
    capabilities: smbios-2.7 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3379MiB
     *-cpu
          product: AMD A10-7300 Radeon R6, 10 Compute Cores 4C+6G
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 1500MHz
          capacity: 1900MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm perfctr_core perfctr_nb bpext arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold vmmcall fsgsbase bmi1 xsaveopt cpufreq
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 30h-3fh) Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Kaveri [Radeon R6 Graphics]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:35 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:2000(size=256) memory:f0a00000-f0a3ffff memory:f0a60000-f0a7ffff
        *-multimedia:0
             description: Audio device
             product: Kaveri HDMI/DP Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:37 memory:f0a40000-f0a43fff
        *-pci:0
             description: PCI bridge
             product: Family 15h (Models 30h-3fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:f0900000-f09fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: enp1s0
                version: 10
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:33 ioport:1000(size=256) memory:f0904000-f0904fff memory:f0900000-f0903fff
        *-pci:1
             description: PCI bridge
             product: Family 15h (Models 30h-3fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:f0800000-f08fffff
           *-network
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=4.2.0-18-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:38 memory:f0800000-f087ffff memory:f0880000-f088ffff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0a48000-f0a49fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.2.0-18-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.02
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.2.0-18-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:32 ioport:2118(size=8) ioport:2124(size=4) ioport:2110(size=8) ioport:2120(size=4) ioport:2100(size=16) memory:f0a4d000-f0a4d7ff
        *-usb:1
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f0a4c000-f0a4cfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-18-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
              *-usb
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: PixArt
                   physical id: 1
                   bus info: usb@5:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
        *-usb:2
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f0a4d900-f0a4d9ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-18-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
              *-usb
                   description: Generic USB device
                   product: USB2.0-CRW
                   vendor: Generic
                   physical id: 3
                   bus info: usb@3:3
                   version: 39.60
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=rtsx_usb maxpower=500mA speed=480Mbit/s
        *-usb:3
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f0a4b000-f0a4bfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-18-generic ohci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
              *-usb
                   description: Bluetooth wireless interface
                   product: AR3012 Bluetooth 4.0
                   vendor: Atheros Communications, Inc.
                   physical id: 2
                   bus info: usb@6:2
                   version: 0.02
                   capabilities: bluetooth usb-1.10
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f0a4d800-f0a4d8ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-18-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
              *-usb
                   description: Video
                   product: Lenovo EasyCamera
                   vendor: Generic
                   physical id: 1
                   bus info: usb@4:1
                   version: 3.12
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 16
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:f0a44000-f0a47fff
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
        *-pci:2
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:5
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f0a4a000-f0a4afff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-18-generic ohci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
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
          bus info: pci@0000:00:03.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:04.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h (Models 30h-3fh) Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 15h (Models 30h-3fh) Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 15h (Models 30h-3fh) Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 15h (Models 30h-3fh) Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Family 15h (Models 30h-3fh) Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:9
          description: Host bridge
          product: Family 15h (Models 30h-3fh) Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST320LT012-1DG14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: LVM1
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=d9fa2484
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2015-10-27 04:08:14 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 42GiB
                capacity: 42GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2015-10-27 04:08:34 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: [REMOVED]
                size: 197GiB
                capacity: 197GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2015-10-26 17:47:17 filesystem=ntfs state=clean
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 57GiB
                capacity: 57GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 19GiB
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 881MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 18GiB
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   logical name: /
                   capacity: 18GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RW DA8A6SH
             vendor: PLDS
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: GL61
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

i paste here content because .txt file size exceed to forums limit.

---

### Post by Vladlenin5000 on 2015-11-15
You needs to install proprietary AMD drivers - *fglrx *-.  How you do it depends on the Ubuntu version you're running. Please post details.

---

### Post by IONx64 on 2015-11-16
> **Vladlenin5000 said:**
> You needs to install proprietary AMD drivers - *fglrx *-.  How you do it depends on the Ubuntu version you're running. Please post details.

Thanks. its my ubuntu details. i made screenshot. Please help how to install it. thanks

---

### Post by Vladlenin5000 on 2015-11-16
I was hoping for 14.04 (or 15.04) because... There's a problem with AMD drivers and 15.10 that should be completely solved soon if not already.
Here's what I did to one test machine with AMD graphics (results may vary):
1. Go to System Settings > Software Properties, Updates tab and select the "proposed" repository (wily-proposed) which is disabled by default and for very good reasons. Close and reload (it'll do the same as *sudo apt-get update*);
2. Go to System Settings > Software Properties, Additional Drivers tab. Select and apply "fglrx-updates"
3. Reboot.
4. Disable "wily-proposed".

---

### Post by IONx64 on 2015-11-18
> **Vladlenin5000 said:**
> I was hoping for 14.04 (or 15.04) because... There's a problem with AMD drivers and 15.10 that should be completely solved soon if not already.
Here's what I did to one test machine with AMD graphics (results may vary):
1. Go to System Settings > Software Properties, Updates tab and select the "proposed" repository (wily-proposed) which is disabled by default and for very good reasons. Close and reload (it'll do the same as *sudo apt-get update*);
2. Go to System Settings > Software Properties, Additional Drivers tab. Select and apply "fglrx-updates"
3. Reboot.
4. Disable "wily-proposed".

I did everything that and after reload booting is freezed in one place screen is violet color without any titles. what should i do next? please help me.

---

### Post by Vladlenin5000 on 2015-11-19
Were you able to login? If not, you can do CTRL+ALT+F1 to get to text only where you should type your username, enter, password, enter... Then you can uninstall the drivers:
```
sudo apt-get purge fglrx*
```

[EDIT]
Also read [http://ubuntuforums.org/showthread.php?t=2299981&page=2&p=13383588#post13383588](http://ubuntuforums.org/showthread.php?t=2299981&page=2&p=13383588#post13383588) . After removing using the aforementioned method you can try this alternative without the need to enable the proposed repository. Good luck.

---

### Post by IONx64 on 2015-11-20
> **Vladlenin5000 said:**
> Were you able to login? If not, you can do CTRL+ALT+F1 to get to text only where you should type your username, enter, password, enter... Then you can uninstall the drivers:
```
sudo apt-get purge fglrx*
```

[EDIT]
Also read [http://ubuntuforums.org/showthread.php?t=2299981&page=2&p=13383588#post13383588](http://ubuntuforums.org/showthread.php?t=2299981&page=2&p=13383588#post13383588) . After removing using the aforementioned method you can try this alternative without the need to enable the proposed repository. Good luck.

I can not get to that stage. screen is empty. thanks for link.

---

