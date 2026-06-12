---
title: "MMCBLK0 issue/ boot time"
date: 2016-05-23
forum: Hardware
---

### Post by timothy13 on 2016-05-23
I have an internal mmc/sd, whichever you prefer to call it, it takes quite a bit to read when booting. i have installed Ubuntu 16.04 on an acer aspire one cloud book 14. most everything works fine, i did have to change the Kernel parameters adding noapic and edd=off to get it to load. it would fail and tell me in the bash menu turn apic=off or noapic.

```
LSHW=
tim-aspire-one-1-431      
    description: Computer
    width: 64 bits
    capabilities: smbios-2.8 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1918MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU  N3050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2159MHz
          capacity: 2160MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:17 memory:90000000-90ffffff memory:80000000-8fffffff ioport:1000(size=64)
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:18 memory:9131c000-9131cfff
        *-generic:1
             description: SD Host controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=0
             resources: irq:11 memory:91321000-91321fff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:16 memory:91300000-9130ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-21-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-21-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=7 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: Cruzer Blade
                   vendor: SanDisk
                   physical id: 1
                   bus info: usb@1:1
                   logical name: scsi0
                   version: 1.26
                   serial: 200422048107C4631855
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Cruzer Blade
                      vendor: SanDisk
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 1.26
                      serial: 200422048107C4631855
                      size: 7633MiB (8004MB)
                      capabilities: partitioned partitioned:dos
                      configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512 signature=58f1d488
                    *-volume
                         description: Windows FAT volume
                         vendor: SYSLINUX
                         physical id: 1
                         bus info: scsi@0:0.0.0,1
                         logical name: /dev/sda1
                         logical name: /media/tim/MYLINUXLIVE
                         version: FAT32
                         serial: 4c14-49c4
                         size: 7628MiB
                         capacity: 7631MiB
                         capabilities: primary bootable fat initialized
                         configuration: FATs=2 filesystem=fat label=MYLINUXLIVE mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
              *-usb:1
                   description: Mouse
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@1:2
                   version: 46.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
              *-usb:2
                   description: Generic USB device
                   product: USB2.0-CRW
                   vendor: Generic
                   physical id: 3
                   bus info: usb@1:3
                   version: 39.60
                   serial: 20100201396000000
                   capabilities: usb-2.00
                   configuration: driver=rtsx_usb maxpower=500mA speed=480Mbit/s
              *-usb:3
                   description: Video
                   product: VGA Webcam
                   vendor: SuYin
                   physical id: 4
                   bus info: usb@1:4
                   version: 1.00
                   serial: HF031A-T803-SE02-REV0100
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:4
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 5
                   bus info: usb@1:5
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
        *-generic:2
             description: DMA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm eisa_dma bus_master cap_list
             configuration: driver=dw_dmac_pci latency=0
             resources: irq:11 memory:91318000-9131bfff
        *-serial:0
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 18.1
             bus info: pci@0000:00:18.1
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=i2c-designware-pci latency=0
             resources: irq:11 memory:9131f000-9131ffff
        *-generic:3
             description: Encryption controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:19 memory:91200000-912fffff memory:91100000-911fffff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:20 memory:91310000-91313fff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:2000(size=4096) memory:91400000-915fffff ioport:91600000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:10 memory:91000000-910fffff
           *-network
                description: Wireless interface
                product: Wireless 3160
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 83
                serial: 34:de:1a:8f:88:88
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-21-generic firmware=16.242414.0 ip=10.59.27.173 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:21 memory:91000000-91001fff
        *-generic:4
             description: DMA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm eisa_dma bus_master cap_list
             configuration: driver=dw_dmac_pci latency=0
             resources: irq:10 memory:91314000-91317fff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1e.4
             bus info: pci@0000:00:1e.4
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:10 memory:9131e000-9131efff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-serial:1 UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:9131d000-9131d01f ioport:1040(size=32)
```

---

### Post by timothy13 on 2016-05-23
Another piece of possibly useful information is, it also takes 10-15 minutes to load in gparted and other partition editors. including terminal.

---

### Post by QDR06VV9 on 2016-05-23
@timothy Please use code tags for posting long string returns it help make it a little easier to read for potential users to help you!
See my Signature for using Code Tags.
Thanks and Good Luck.
Kind Regards

---

