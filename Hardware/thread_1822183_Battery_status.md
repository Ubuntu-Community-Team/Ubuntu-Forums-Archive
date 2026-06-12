---
title: "Battery status"
date: 2011-08-10
forum: Hardware
---

### Post by Blancpain on 2011-08-10
Hello,

I have an Acer Aspire one 521 netbook running ubuntu 11.04. Everything is great but the battery status is not working - it does not show battery life or whether it's on battery or power. I tried a lot of things but with no success. If anyone knows a solution for this please reply :)

---

### Post by Basher101 on 2011-08-10
Did you try the settings in the power manager? You could have it set to not show the battery. Try setting it to show the battery when its (de)charging

---

### Post by Blancpain on 2011-08-10
Yes, I tried but it always shows a lightning in the notification area and doesn't say anything when you hover over it.

---

### Post by Basher101 on 2011-08-10
Just a mouseover like in windows wont work. Click on it and it should display your remaining time. Also clicking on the time that is displayed will open a widnows that shows alot of information about your battery (i wish windows did this...but its windows so :lolflag: ). Here is a screen:

---

### Post by seicean on 2011-08-10
See in "battery settings" under the "details" tab... paste the manufacturer and the model number here (if available). 

Ex: SONY MMX65875-3455

---

### Post by Blancpain on 2011-08-10
@Basher101 I don't see a time, all I see is "preferences" when I click on it. 

@seicean How can I access these battery settings from elsewhere?

---

### Post by Basher101 on 2011-08-10
To display your whole hardware type in terminal:```
sudo lshw
``` type your password and paste the output here

---

### Post by Blancpain on 2011-08-10
```
 description: Notebook
    version: Not Applicable
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1 uuid=A7B92989-E419-4709-811D-C80AA9A15083
  *-core
       description: Motherboard
       product: JV01-NL
       vendor: Acer
       physical id: 0
       version: Not Applicable
       serial: 020JC1MBQTF0220B
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V1.11
          date: 04/25/2011
          size: 118KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD V105 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.6.3
          slot: Socket S1G4
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc up nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=1 enabledcores=1 threads=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 2GiB
        *-bank
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: 99U5428-014.A00G
             vendor: AMD
             physical id: 0
             serial: 4F31707B
             slot: S1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (int gfx)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:d0000000-d01fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M880G [Mobility Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:18 memory:c0000000-cfffffff ioport:9000(size=256) memory:d0100000-d010ffff memory:d0000000-d00fffff
           *-multimedia
                description: Audio device
                product: RS880 Audio Device [Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:d0110000-d0113fff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:a000(size=4096) memory:d0200000-d02fffff
           *-network
                description: Ethernet interface
                product: AR8152 v1.1 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c1
                serial: c8:0a:a9:a1:50:83
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:43 memory:d0200000-d023ffff ioport:a000(size=128)
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:d0300000-d03fffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 78:e4:00:9d:d3:0c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.11.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:d0300000-d030ffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:42 ioport:8440(size=8) ioport:8430(size=4) ioport:8420(size=8) ioport:8410(size=4) ioport:8400(size=16) memory:d0606800-d0606bff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVT-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX71A30W7706
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c5c5c04e
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 7460-641d
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-07-28 20:32:51 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 24b72cbe-1eed-6748-b712-3256f30c8c2f
                   size: 58GiB
                   capacity: 58GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-07-28 20:33:13 filesystem=ntfs state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 8a561c4b-a3d9-7944-886a-68dd999c4b77
                   size: 46GiB
                   capacity: 46GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-08-01 00:16:01 filesystem=ntfs state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 126GiB
                   capacity: 126GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /boot
                      capacity: 100MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 19GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 102GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 4771MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d0404000-d0404fff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:d0606000-d06060ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d0405000-d0405fff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:d0606400-d06064ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 41
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:d0400000-d0403fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

```

---

### Post by Basher101 on 2011-08-10
Hm your battery is not in the hardware listing...mine is. Thats odd..but now i really do not know how to proceed. Someone else with more knowledge must help. 

Regards

---

### Post by Blancpain on 2011-08-10
Thanks for your time anyway, hope someone else knows how to fix this.

---

### Post by Blancpain on 2011-08-10
anyone?

---

