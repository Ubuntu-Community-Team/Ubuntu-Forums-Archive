---
title: "Boot Hangs With New Ram 8GB (2x4gb) But Works Fine With 4gb (2x2gb)"
date: 2019-12-27
forum: Hardware
---

### Post by soundchaser59 on 2019-12-27
[SIZE=1]***EDIT: Note that there is no real resolution to this thread, the only fix was to revert back to 2x2gb memory that is known to work fine. There are 2x4gb sticks available that would probably work in this mobo, but I'm not willing to pay over $100 bucks to get them just to doctor up this old hardware a little bit. I would delete the thread if I could, but maybe that's not necessary. - sc***[/SIZE]


I just got two 4gb sticks of non-ECC ram, total supposed to be 8gb. 

This is the exact ram I just put in..... [https://www.electrobyt.com/index.php?main_page=product_info&products_id=5261](https://www.electrobyt.com/index.php?main_page=product_info&products_id=5261)  

Power on I get a single short beep, bios recognizes 8gb memory, post displays 8gb ddr2 800mhz running dual channel 128 bit, which I believe is what it should say. When I had 4gb (two 2gb sticks) it said 4gb ddr2 800mhz dual channel 128 bit and that configuration had been running fine. 

I rebooted and selected memtest this time, and I estimate the test will  take almost 2 hours to complete. So far is says 0 errors and it's about  85% finished. EDIT: Memtest finished 100% with 0 errors. 

Reboot and then Ubuntu appears to start and the grub menu appears. I hit enter on the default to run Ubuntu 64 bit. After several seconds I see the all purple screen and a small line that says Ubuntu 18.04 with the four or five small colored dots (depends on which version of Ubuntu I select in the grub menu apparently) that change color. The first dot changes color and then it hangs there. Subsequent reboots it will count more dots, usually 20 or so, but it will again hang. This last time it said.... 

OK] Started session c1 of user gdm 
OK] Started User Manager for UID 121 

and that's where it stops every time. Note that the machine will not boot to Mint either. If I select the Mint ssd it will boot to the log in screen but with no mouse and no keyboard. 

The farthest I can get is if I disable HPET in bios, then boot to grub and select advanced options, then choose Ubuntu 4.15.0 72 - generic. 
That gets me all the way to the log in screen, but with no mouse and no keyboard. 

If I select a newer version 5.0.0 23  or  5.0.0 37 it goes back to this...... 

OK] Started session c1 of user gdm 
OK] Started User Manager for UID 121

and hangs. 

Here is my hardware spec from when I booted with the old ram a single 2gb stick. Also works fine if I put the 2x2gb (4gb total) back in. 

```
rootbeer@SC59:~$ uname -a
Linux SC59 5.0.0-32-generic #34~18.04.2-Ubuntu SMP Thu Oct 10 10:36:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
rootbeer@SC59:~$ sudo lshw
[sudo] password for rootbeer:            
sc59                        
    description: Desktop Computer
    product: M61PME-S2P
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 smp vsyscall32
    configuration: boot=normal chassis=desktop uuid=30303234-3144-3032-4636-3835FFFFFFFF
  *-core
       description: Motherboard
       product: M61PME-S2P
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2
          date: 12/30/2008
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          slot: Socket M2
          size: 2600MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl cpuid extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
             configuration: level=2
     *-cache
          description: L1 cache
          physical id: 4
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
          configuration: level=1
     *-memory:0
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:7 ioport:e000(size=64) ioport:1c00(size=64) ioport:c400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fa007000-fa007fff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 5.0.0-32-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 5.00
             capabilities: usb-1.10
             configuration: driver=hub slots=10 speed=12Mbit/s
           *-usb:0
                description: Keyboard
                product: USB Keyboard
                vendor: SIGMACHIP
                physical id: 2
                bus info: usb@2:2
                version: 1.10
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
           *-usb:1
                description: Mouse
                product: USB Receiver
                vendor: Logitech
                physical id: 4
                bus info: usb@2:4
                version: 30.00
                capabilities: usb-2.00
                configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fa006000-fa0060ff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 5.0.0-32-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 5.00
             capabilities: usb-2.00
             configuration: driver=hub slots=10 speed=480Mbit/s
           *-usb
                description: Generic USB device
                product: 802.11ac WLAN Adapter
                vendor: Realtek
                physical id: 1
                bus info: usb@1:1
                version: 2.00
                serial: 00e04c000001
                capabilities: usb-2.10
                configuration: driver=rtl8812au maxpower=500mA speed=480Mbit/s
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:a000(size=4096)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:fa000000-fa003fff
     *-ide
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm isa_compatibility_mode_controller__supports_both_channels_switched_to_pci_native_mode__supports_bus_mastering bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: enp0s7
          version: a2       
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.5 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:25 memory:fa004000-fa004fff ioport:c800(size=8)
     *-storage
          description: RAID bus controller
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: storage pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fa005000-fa005fff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 101
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0 ioport:b000(size=4096) memory:f8000000-f9ffffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: Redwood XT [Radeon HD 5670/5690/5730]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0
             bus info: pci@0000:02:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:24 memory:e0000000-efffffff memory:f9000000-f901ffff ioport:b000(size=256) memory:c0000-dffff
        *-multimedia
             description: Audio device
             product: Redwood HDMI Audio [Radeon HD 5000 Series]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:26 memory:f9020000-f9023fff
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: a
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-4120B
             vendor: HL-DT-ST
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: A102
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: b
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: CT500MX500SSD1
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 023
             serial: 1846E1D7E1B6
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=16e20f2f
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 8f7ebbfc-72ef-44ef-97d1-efdb30244c19
                size: 465GiB
                capacity: 465GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-12-21 02:22:47 filesystem=ext4 lastmountpoint=/ modified=2019-12-21 22:48:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-12-21 22:48:25 state=mounted
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au ip=192.168.1.11 multicast=yes wireless=IEEE 802.11bgn
rootbeer@SC59:~$



```

---

### Post by soundchaser59 on 2019-12-27
I tried with just one 4gb stick and with HPET disabled the machine would get thru the post, the Ubuntu with counting dots would appear briefly, then it would hang on a black screen. With HPET enabled it would boot to Ubuntu with counting dots, then reboot over and over, endless reboots. 

When I revert back to the 2x2gb ram everything boots up and runs fine. I guess I am resigned to only having 4gb ram. There is other 2x4gb ram available, but at prices I am not willing to pay for this old machine. I hoped 8gb ram would make a noticeable difference in overall response time, but 4gb ram is sufficient, it is certainly not what I would call slow or sluggish.

---

### Post by CatKiller on 2019-12-27
> **soundchaser59 said:**
> I hoped 8gb ram would make a noticeable difference in overall response time, but 4gb ram is sufficient, it is certainly not what I would call slow or sluggish.

More RAM doesn't make things quicker: running out of RAM makes things terribly slow. If you aren't running out of RAM then more RAM will make no difference to performance.

---

### Post by soundchaser59 on 2019-12-27
> **CatKiller said:**
> More RAM doesn't make things quicker: running out of RAM makes things terribly slow. If you aren't running out of RAM then more RAM will make no difference to performance.Depends what I'm trying to run all at the same time I suppose.

---

### Post by kurt18947 on 2019-12-28
> **soundchaser59 said:**
> Depends what I'm trying to run all at the same time I suppose.

That's the way I understand it. I installed HTOP, it runs in a terminal and will tell you how much RAM you have free. As CatKiller said, if you run out of DRAM and start using swap things will slow down. 

Some machines are fussy about the order in which DRAM slots are populated. If you have a book for your motherboard you could see if that may be an issue. It doesn't really sound like it to me but something you could check.

---

