---
title: "How to make the Dell Optiplex graphics compatable?"
date: 2016-10-10
forum: Hardware
---

### Post by iain4626 on 2016-10-10
Hello there - 
I'm wondering if someone can help me get my good hi-res graphics back on my desktop Optiplex Dell 745.
It went haywire with (I imagine) some upgrade on my 12.04 Ubuntu. Funnily enough it will still work
if everything is freshly loaded (with Windows XP as a previous preparation) but then after some days it goes back to a blank screen. I know how to load simple low-res graphics but I can't boost it back to hi-res. 

My OS is 64 bit and according to my graphics overview, my graphics is apparently 'VESA: Intel(r)Broadwater-G Graphics'.

Is there a simple list of commands to fix this on the terminal? 
Better still, is there a simple, cheap graphics board I could install which would solve the problem and let me enjoy my computer on hi-res again?
Lastly, is there any chance there will be a built in fix for this problem in future versions of Ubuntu?

I've only just found a long list of machines which are perfect for running Linux on. I'll likely refer to it in future when I buy a new machine.

Thanks all,

Iain

---

### Post by mörgæs on 2016-10-12
Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by iain4626 on 2016-10-12
Hello there,
I'm now getting ready to buy a compatable video card to hopefully fix the problem.
I've found an interesting list here:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

Thank you for your help...
Here's my hardware details.
Iain (Who used to listen to KUKL in the 1980s : )

```
computer
    description: Mini Tower Computer
    product: OptiPlex 745 ()
    vendor: Winbond Electronics
    serial: [REMOVED]
    width: 64 bits
    capabilities: vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=mini-tower power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0HR330
       vendor: Winbond Electronics
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: 2.3.1
          date: 05/21/2007
          size: 64KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: KX8388-ELG
             vendor: Kingston
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: 4HTF6464AZ-667H1
             vendor: Micron Technology
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_3
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: KX8388-ELG
             vendor: Kingston
             physical id: 2
             serial: [REMOVED]
             slot: DIMM_2
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: 4HTF6464AZ-667H1
             vendor: Micron Technology
             physical id: 3
             serial: [REMOVED]
             slot: DIMM_4
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: 82Q963/Q965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82Q963/Q965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:dfc00000-dfcfffff
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: 82Q963/Q965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:dfe00000-dfefffff memory:c0000000-cfffffff ioport:ecb8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82Q963/Q965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:dff00000-dfffffff
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff00(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:22 memory:dfdfbc00-dfdfbfff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:dfdfc000-dfdfffff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:dfb00000-dfbfffff ioport:80000000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:dfa00000-dfafffff ioport:80200000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=5754-v3.15 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:45 memory:dfaf0000-dfafffff
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff80(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff60(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ff980800-ff980bff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:df900000-df9fffff
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant Systems, Inc.
                physical id: 2
                bus info: pci@0000:04:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:df9f0000-df9fffff ioport:dcf8(size=8)
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fec0(size=16) ioport:ecc0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:dfdfbb00-dfdfbbff ioport:ece0(size=32)
        *-ide:1
             description: IDE interface
             product: 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe40(size=8) ioport:fe50(size=4) ioport:fe60(size=8) ioport:fe70(size=4) ioport:fed0(size=16) ioport:ecd0(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3160815AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000f0c67
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 147GiB
                capacity: 147GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-09-21 14:51:16 filesystem=ext4 lastmountpoint=/ modified=2016-10-11 19:33:46 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-10-12 14:48:25 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2036MiB
                capacity: 2036MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2036MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: CDRWDVD DH-48C2S
             vendor: PBDS
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: ND12
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
```

---

### Post by iain4626 on 2016-10-12
Good heavens - what a giant list of stuff. 
I may have made a mistake there - too late...

---

### Post by QIII on 2016-10-12
Hello!

Please use code tags when you paste results from the terminal.  It preserves formatting and makes your posts much easier to read.

To use code tags you may:

1.  Click the # button above the text input box, place your cursor between the two code tags created and paste you text.

2.  Paste your text, highlight it and then click the # button.

3   Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after it.  The square brackets are required.

Thanks!

---

### Post by mörgæs on 2016-10-12
Before buying more stuff I suggest that you click the old hardware link in my signature. Search the guide for **uxa** and apply the changes described. Does it help?

---

### Post by iain4626 on 2016-10-14
[SIZE=2]Thank you all for your help. I did try with your advice but I got a bit stuck on how to run the commands.
I pasted on the:

[/SIZE]Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection

...into Leafpad and then ran 'sudo <leafpad> /etc/X11/xorg.conf' but nothing much was recognised.

Alas you're dealing here with a naive user. To make matters worse my computer now goes blank on start up
with no recognition that the monitor is even there. After several attempts I get a scrambled screen. I'm 
going to order a new short monitor lead and continue using this computer here (It's an Optimplex 755 on Ubuntu 14.04.5).
So far it's working like a dream on high res. 
I use the the same monitor, so the monitor's working okay.

Thank you both once again for your help,
I'll pray this Trusty 14.04.5 & Opti 755 will not suddenly flip out on me,
Bye now,

Iain

PS - Just realised I might have typed in Leafpad with a capital L. Maybe it needs to be lowercase.

---

### Post by mörgæs on 2016-10-14
Correct, leafpad should be in lowercase and there should not be < > around it.

---

