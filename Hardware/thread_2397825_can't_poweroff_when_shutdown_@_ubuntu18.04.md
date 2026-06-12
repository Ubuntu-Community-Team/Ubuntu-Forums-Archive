---
title: "can't poweroff when shutdown @ ubuntu18.04"
date: 2018-08-03
forum: Hardware
---

### Post by astrorobot-110 on 2018-08-03
In shutdown process, My PC stucks without poweroff.
When stucks, message displays "reboot: shutdown".

I found some guide that configure acpi args to "force", "noirq" in /boot/grub/grub.cfg, but not work for me.

what shuld I do? I got first time about such trouble, so I have no idea how I found a cause.

---

### Post by astrorobot-110 on 2018-09-27
A long time, no one support to me...help!!!

---

### Post by mastablasta on 2018-09-27
open the terminal (or drop to console via ctrl+alt+F1, login) and then run

```
sudo shutdown -h now
```

then watch for any error messages. they should also be in the logs. a system log viewer is available in Ubuntu. check the lines on shutdown and post them here. 

it might be also good to post your hardware specs in case there are known hardware driver issues.

```
lshw -sanitize 
```

should give you the hardware list that you can post here.

---

### Post by astrorobot-110 on 2018-09-27
Thanks your help, mastablasta. But sorry, I stack with which log I can found about this. ;(
If this is acpi trouble, I found in kern.log
```

Sep 27 19:15:47 xxxxxxxxx kernel: ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x000000000000050E-0x000000000000050E (\_SB.PCI0.SBRG.GIO) (20170831/utaddress-247)
Sep 27 19:15:47 xxxxxxxxx kernel: ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

```


Also I get H/W list
```

computer
    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7959MiB
     *-cpu
          product: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2339MHz
          capacity: 3100MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer xsave avx lahf_lm epb pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm arat pln pts flush_l1d cpufreq
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=snb_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:fa000000-fb0fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GM107 [GeForce GTX 750 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:31 memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:fb080000-fb083fff
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:30 memory:fb204000-fb20400f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:fb203000-fb2033ff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) ioport:d2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 06
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:17 ioport:d000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:c000(size=4096) memory:fb100000-fb1fffff
           *-pci
                description: PCI bridge
                product: IT8893E PCIe to PCI Bridge
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pci normal_decode bus_master cap_list
                resources: iomemory:2220c1c10-2220c1c0f ioport:c000(size=4096) memory:fb100000-fb1fffff
              *-firewire
                   description: FireWire (IEEE 1394)
                   product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                   vendor: VIA Technologies, Inc.
                   physical id: 0
                   bus info: pci@0000:05:00.0
                   version: 46
                   width: 32 bits
                   clock: 33MHz
                   capabilities: ohci bus_master cap_list
                   configuration: driver=firewire_ohci latency=32 maxlatency=32
                   resources: irq:18 memory:fb100000-fb1007ff ioport:c080(size=128)
              *-multimedia
                   description: Multimedia audio controller
                   product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
                   vendor: VIA Technologies Inc.
                   physical id: 1
                   bus info: pci@0000:05:01.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: bus_master cap_list
                   configuration: driver=snd_ice1724 latency=32
                   resources: irq:19 ioport:c100(size=32) ioport:c000(size=128)
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fb202000-fb2023ff
        *-isa
             description: ISA bridge
             product: H61 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:fb201000-fb2017ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fb200000-fb2000ff ioport:f000(size=32)
     *-scsi
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: BD-RE  BH14NS48
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-scsi:0
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage

```
I know in some occation, nVidia driver tickles in shutdown. But I don't know how it fix.

---

### Post by mastablasta on 2018-09-28
are you using a proprietary GPU driver? is there a newer driver available for the chip?

are intel drivers patched (the "microcode")?

yes, it is likely ACPI issue, but not sure what is causing it. i think ACPI can be disable, but i am not sure yet if that is a such a good idea. if you shut it off with a button does it then report any errors on new boot?

what happens if you try to shut it down with command? does it freeze as well?

---

### Post by astrorobot-110 on 2018-09-28
> **mastablasta said:**
> are you using a proprietary GPU driver? is there a newer driver available for the chip?

are intel drivers patched (the "microcode")?


Both packages are installed from Ubuntu repository, and seems no problems. Are there newest stable release?

> **mastablasta said:**
> 
yes, it is likely ACPI issue, but not sure what is causing it. i think ACPI can be disable, but i am not sure yet if that is a such a good idea. if you shut it off with a button does it then report any errors on new boot?

what happens if you try to shut it down with command? does it freeze as well?

Sometimes, It displays "... reboot: shutdown" and hear HDD stop sound...just HDD motor stops.
I consider just fails power off process, and it outs no error messages...so I don't check reports.
In fact, I don't know how I get errorlog in last shutdown process...

---

