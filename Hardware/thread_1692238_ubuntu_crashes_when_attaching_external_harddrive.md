---
title: "ubuntu crashes when attaching external harddrive"
date: 2011-02-21
forum: Hardware
---

### Post by senca on 2011-02-21
hey,
I'm working on a ubuntu for a couple of weeks now. Today I wanted to put something an my external harddrive but when plugging it in and waiting for 5 secodns...suddenly the screen turns black with only my cursor visible (but not usable) and I can only turn off the laptop by pressing the startbutton on the laptop. Thats the only thing I can do, nothing else works anymore from the moment the screen turns black :s.
Does ny one know why?
I am using ubuntu 10.10 64-bit on a Dell XPS laptop.
Everything on the external hard disk is what I saved in the past from the windows laptop.

greetzzz

---

### Post by senca on 2011-02-23
No one with a clue?

---

### Post by senca on 2011-02-27
Update: yesterday I imported some pictures form a digital camera and worked perfectly. Today I wanted to import some more pictures but now the laptop 'hangs' again :s. 
I had some music playing and it kept replaying the last 5 seconds while the screen was black and the cursor was again unmovable on screen :s. This is really annoying and I have no idea why this is happening :s.
Do I have to install extra drivers or something? This is really bugging me :s

edit:
sometimes the external hard drive doesn't give a crash but is the also 'not found' on the laptop. When rebooting and attaching again...FREEZE!

next edit: When rebooting sometimes the digital camera is "accepted". At this point the system doesn't freeze on anything but the ext. hard drive is never accepted when attached before the digicam and the digicam is not always accepted :s. This is a very very annoying bug :s

---

### Post by senca on 2011-02-28
Hasn't anyone had this bug on 10.10 ? :s

---

### Post by Hedgehog1 on 2011-02-28
Senca,

Is you external hard drive connected by USB, or by eSata? Without basic info like this, most folks will skip over the post.

Giving the basic information about the hardware helps.

---

### Post by senca on 2011-02-28
What I know is that the connection on the laptop are labelled SS. Every hard drive (or digicam for that matter) is with a USB plug. If there are some steps I need too follow too give more info about my hardware, I am listening :).

---

### Post by senca on 2011-03-02
Underneath I pasted (which is an awefull big list) my hardware devices:

  serial: 95CH7P1
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=portable frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=44454C4C-3500-1043-8048-B9C04F375031
  *-core
       description: Motherboard
       product: 00CKNG
       vendor: Dell Inc.
       physical id: 0
       version: A04
       serial: .95CH7P1.CN4864312B0992.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 1
          version: A04 (11/26/2010)
          size: 123KiB
          capacity: 1984KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 560  @ 2.67GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: CPU Version
          slot: U2E1
          size: 1199MHz
          capacity: 4096MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: asynchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: burst internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 8
             slot: L3 Cache
             size: 3MiB
             capacity: 8MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: M471B5273CH0-CH9
             vendor: 80CE
             physical id: 0
             serial: 950623F4
             slot: DIMM_A
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: NT2GC64B88B0NS-CG
             vendor: 830B
             physical id: 1
             serial: 76E62415
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 18
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 18
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:ac000000-adefffff ioport:ae000000(size=301989888)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller cap_list
                configuration: latency=0
                resources: memory:ac000000-acffffff memory:b0000000-bfffffff memory:ae000000-afffffff ioport:2000(size=128) memory:ad000000-ad07ffff
           *-multimedia
                description: Audio device
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:adefc000-adefffff
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 18
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:48 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f0906800-f090680f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f0907000-f09073ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:50 memory:f0900000-f0903fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:6000(size=4096) memory:a0000000-a01fffff ioport:a0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:7000(size=4096) memory:f0400000-f04fffff ioport:a0400000(size=2097152)
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1000
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 00
                serial: 8c:a9:82:0c:47:7c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-25-generic firmware=128.50.3.1 build 13488 ip=192.168.0.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:49 memory:f0400000-f0401fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:3000(size=4096) memory:f0500000-f05fffff ioport:f0c00000(size=2097152)
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:f0500000-f0501fff
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:4000(size=4096) memory:f0600000-f06fffff ioport:f0e00000(size=2097152)
        *-pci:5
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:5000(size=4096) memory:a0600000-a09fffff ioport:f0a00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 06
                serial: f0:4d:a2:6b:fe:97
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:46 ioport:5000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0907400-f09077ff
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:47 ioport:1840(size=8) ioport:1814(size=4) ioport:1818(size=8) ioport:1810(size=4) ioport:1820(size=32) memory:f0906000-f09067ff
           *-disk
                description: ATA Disk
                product: ST9500420AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: D005
                serial: 5VJALEAQ
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00021520
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 861f114d-229f-48bd-9402-0d4034bba14b
                   size: 449GiB
                   capacity: 449GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-02-15 22:45:04 filesystem=ext4 lastmountpoint=/&#65533;<&#65533;&#1288;&#65533;&#65533;)&#65533;&#65533;&#65533;)&#65533;&#904;&#65533;&#65533;)&#1160;&#65533;&#65533;y&#65533;&#1736;&#65533;&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=&#65533;&#1288;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-02-25 17:05:11 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-03-01 18:34:54 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 16GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW AD-7717H
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 101A
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f0907800-f09078ff ioport:1860(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel ips latency=0
             resources: irq:18 memory:f0905000-f0905fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 05
          width: 32 bits
          clock: 33MHz
  *-battery
       product: SIMPLO
       vendor: SIMPLO
       physical id: 1
       slot: System Battery Bay
       capacity: 52000mWh
       configuration: voltage=11.1V
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 2
       capabilities: outbound
  *-power UNCLAIMED
       description: To Be Defined By O.E.M
       product: To Be Defined By O.E.M
       vendor: To Be Defined By O.E.M
       physical id: 3
       version: 2.50
       serial: To Be Defined By O.E.M
       capacity: 32768mWh

---

### Post by senca on 2011-03-04
Guess that was unusefull information?

---

### Post by Darque1137 on 2011-03-17
Same bug, same problem: new Dell XPS 15, running Ubuntu 10.10 64-bit.   About fifteen seconds after plugging in the external (Western Digital WD  Elements 500 GB) via USB 2.0, the screen goes black except for an  unresponsive mouse icon, and I have to reboot to do anything.

Any thoughts?  The external was supposed to make migrating files to the new laptop easier, not harder...

---

