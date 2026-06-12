---
title: "Intel i5 NUC randomly rebooting"
date: 2019-11-25
forum: Hardware
---

### Post by vin944 on 2019-11-25
My NUC has been rebooting randomly across 2 installs of Ubuntu 19.04 and then 18.04.  Sometimes it reboots couple times a day and sometimes every couple days.  It's been happening for months now.  There is no pattern to the rebooting that I can notice however I have recognized a couple of events that are suspicious.  The NUC will never reboot while I'm using it.  Also if the monitor is actually powered off, instead of the NUC rebooting, it will just crash and I have to hard start it.  Those are the only two anomalies that I notice.  I'm very good on the command line but awful when it comes to going thru the logs.  Any ideas?  Thanks.

---

### Post by mörgæs on 2019-11-26
Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags. It will tell us more about the hardware.

---

### Post by vin944 on 2019-11-26
The resulting file was very large so I just included it here as an attachment.  Thanks.

---

### Post by mörgæs on 2019-11-27
An attached file is only visible to users who are logged in. To make it visible to all it must be posted directly.

```
computer
    description: Desktop Computer
    product: NUC8i5BEH (BOXNUC8i5BEH)
    vendor: Intel(R) Client Systems
    version: J72747-302
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.1 dmi-3.1 smp vsyscall32
    configuration: boot=normal chassis=desktop family=Intel NUC sku=BOXNUC8i5BEH uuid=[REMOVED]
  *-core
       description: Motherboard
       product: NUC8BEB
       vendor: Intel Corporation
       physical id: 0
       version: J72692-303
       serial: [REMOVED]
       slot: Default string
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: BECFL357.86A.0041.2018.0719.1931
          date: 07/19/2018
          size: 64KiB
          capacity: 15MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 3b
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2400 MHz (0.4 ns)
             product: CT8G4SFD824A.C16FF
             vendor: 859B
             physical id: 0
             serial: [REMOVED]
             slot: SODIMM1
             size: 8GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous 2400 MHz (0.4 ns)
             product: CT8G4SFD824A.C16FF
             vendor: 859B
             physical id: 1
             serial: [REMOVED]
             slot: SODIMM2
             size: 8GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
     *-cache:0
          description: L1 cache
          physical id: 44
          slot: L1 Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 45
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 46
          slot: L3 Cache
          size: 6MiB
          capacity: 6MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-8259U CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 47
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-8259U CPU @ 2.30GHz
          serial: [REMOVED]
          slot: U3E1
          size: 3539MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          product: 8th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:141 memory:bf000000-bfffffff memory:80000000-8fffffff ioport:4000(size=64) memory:c0000-dffff
        *-generic:0
             description: System peripheral
             product: Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: /dev/fb0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list fb
             configuration: depth=32 latency=0 mode=1920x1200 visual=truecolor xres=1920 yres=1200
             resources: iomemory:400-3ff memory:404ac1a000-404ac1afff
        *-generic:1
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 30
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: iomemory:400-3ff irq:16 memory:404ac19000-404ac19fff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 30
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: iomemory:400-3ff irq:126 memory:404ac00000-404ac0ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.0.0-29-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 3
                   bus info: usb@1:3
                   version: 32.98
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: USB-compliant keyboard
                      vendor: Plus More Enterprise LTD.
                      physical id: 3
                      bus info: usb@1:3.3
                      version: 1.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
                 *-usb:1
                      description: Mouse
                      product: USB Receiver
                      vendor: Logitech
                      physical id: 4
                      bus info: usb@1:3.4
                      version: 30.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: a
                   bus info: usb@1:a
                   version: 0.02
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.0.0-29-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-3.10
                configuration: driver=hub slots=6 speed=10000Mbit/s
        *-memory UNCLAIMED
             description: RAM memory
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 30
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: iomemory:400-3ff iomemory:400-3ff memory:404ac14000-404ac15fff memory:404ac18000-404ac18fff
        *-network:0 DISABLED
             description: Wireless interface
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             logical name: wlp0s20f3
             version: 30
             serial: [REMOVED]
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=iwlwifi driverversion=5.0.0-29-generic firmware=43.95eb4e97.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
             resources: iomemory:400-3ff irq:16 memory:404ac10000-404ac13fff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 30
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: iomemory:400-3ff irq:130 memory:404ac17000-404ac17fff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 30
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:128 memory:c0a24000-c0a25fff memory:c0a27000-c0a270ff ioport:4090(size=8) ioport:4080(size=4) ioport:4060(size=32) memory:c0a26000-c0a267ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:5000(size=12288) memory:90000000-be0fffff ioport:4000000000(size=1241513984)
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124
        *-pci:3
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.6
             bus info: pci@0000:00:1d.6
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 ioport:3000(size=4096) memory:c0000000-c09fffff ioport:404a100000(size=10485760)
           *-generic
                description: Unassigned class
                product: RTS522A PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:6e:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:127 memory:c0000000-c0000fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 30
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: iomemory:400-3ff irq:142 memory:c0a20000-c0a23fff memory:404ab00000-404abfffff
        *-serial:0 UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 30
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:400-3ff memory:404ac16000-404ac160ff ioport:efa0(size=32)
        *-serial:1 UNCLAIMED
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 30
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe010000-fe010fff
        *-network:1
             description: Ethernet interface
             product: Ethernet Connection (6) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: eno1
             version: 30
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.4-4 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:129 memory:c0a00000-c0a1ffff
     *-scsi:0
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SanDisk SD8SN8U-
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 0006
             serial: [REMOVED]
             size: 119GiB (128GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=6294ff42
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 119GiB
                capacity: 119GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2019-09-24 18:51:30 filesystem=ext4 lastmountpoint=/ modified=2019-11-26 03:49:13 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-11-25 13:18:36 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: INTEL SSDSC2BB01
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 0023
             serial: [REMOVED]
             size: 1490GiB (1600GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=daa3ea1a
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: [REMOVED]
                size: 1490GiB
                capacity: 1490GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2019-08-09 13:57:16 filesystem=ntfs label=1.5TB state=clean
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: [REMOVED]
       capacity: 32768mWh
```

I suggest a fresh install of 19.10 and/or a [BIOS]("https://downloadcenter.intel.com/product/126148/Intel-NUC-Kit-NUC8i5BEH") upgrade.

---

### Post by mastablasta on 2019-11-27
also check the logs (in /var/log or with log viewer) to see if what are the last things the NUC did before rebooting

---

### Post by vin944 on 2019-11-28
I will put an echo 'date' line in the rc.local so that when it reboots I can at least have a timestamp.  I will use that to go into the logs and see what I can get there.  

Yes there is a BIOS update available for the NUC.  I will do that also and report back.  Thanks to all!  Happy Thanksgiving.

---

### Post by vin944 on 2019-12-11
> **mörgæs said:**
> 
I suggest a fresh install of 19.10 and/or a [BIOS]("https://downloadcenter.intel.com/product/126148/Intel-NUC-Kit-NUC8i5BEH") upgrade.

On Dec 4th I used the F7 BIOS upgrade util to flash the newest firmware.  I am knocking on wood, there have been no more reboots.  It has never gone this long without rebooting so I'm keeping my fingers crossed that the BIOS upgrade did the trick.  Thanks very much for the help.  I will continue  knocking on wood right now but I have a good feeling this issue is solved.  :cool:

---

### Post by VMC on 2019-12-11
I don't see a nvme storage. Mine use to reboot, but only while using, and first time return for repair, they only updated BIOS (which, I already did). Obviously he still rebooted on its own. Second time for repair they replaced the mainboard. Its been working perfectly since. The hidden secret was that while I used the installed HD, no reboot. It was only after using nvme [and also I found, installing a SSD],  did it reboot. Weird as hell. While HD installed, no issue.

I reseated CPU, memory, etc. Nothing effected it. I thought maybe psu was the culprit. I I'm certain its was the mainboard. These types of issues can be very time consuming. I even thought Chrome was at fault, since it didn't fail using Firefox, but that didn't pan out. Even Windows Edge failed.

---

### Post by mörgæs on 2019-12-12
Good that the problem is solved. Please mark the thread so.

Should the problem reappear you can always unmark the thread and post again.

---

### Post by vin944 on 2019-12-14
> **VMC said:**
> I don't see a nvme storage. Mine use to reboot, but only while using, and first time return for repair, they only updated BIOS (which, I already did). Obviously he still rebooted on its own. Second time for repair they replaced the mainboard. Its been working perfectly since. The hidden secret was that while I used the installed HD, no reboot. It was only after using nvme [and also I found, installing a SSD],  did it reboot. Weird as hell. While HD installed, no issue.

I reseated CPU, memory, etc. Nothing effected it. I thought maybe psu was the culprit. I I'm certain its was the mainboard. These types of issues can be very time consuming. I even thought Chrome was at fault, since it didn't fail using Firefox, but that didn't pan out. Even Windows Edge failed.

Yes this type of problem is as weird as it gets.  I purposely did not install chrome until I bottomed out on the reboot issue.  As of today the 14th of Dec.  there have still been no reboots and it is a little bit shocking, lol.  I never turn my desktops off and no other ubuntu installation has ever reboot on me.  Even my raspberry Pi has an uptime over 1.5 yrs, lol.  Thanks for everyone's help and I'll mark this thread solved.

---

### Post by mörgæs on 2019-12-14
I hope you reboot every time you update the kernel, else the new one will not be activated.

---

