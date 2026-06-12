---
title: "Unable to activate Bluetooth on Clevo W860CU on 9.10"
date: 2009-11-23
forum: Hardware
---

### Post by shredwheat on 2009-11-23
I've got a W860CU that I am extremely impressed with. But I am unable to activate the bluetooth adapter.

The Fn-F12 key is clearly labeled as the bluetooth toggle hotkey. When the computer is booting up, the LED for bluetooth is lit. Early in the boot process that LED is disabled, and I cannot get it to activate. The computer claims that there is no bluetooth adapter on the computer.

I'm not even sure what package to file a bug against. I'd take a rough guess and say it is something to do with ACPI?

Does anyone know of a tool I can use to monitor the special Fn keys on this laptop? I'd be very happy with a way to activate bluetooth manually, without the special keypress.

---

### Post by sloik on 2009-11-23
I've got the same issue... moreover, Ubuntu is not detecting laptop lid closures, pressing of the power button, or pressing of the sleep button in addition to the Bluetooth toggle button. This results in being unable to suspend via closing the lid, and when suspended by other means, the laptop cannot be powered back on without holding the power button and shutting down first.

acpi_listen returns absolutely nothing when pressing these keys.

Any help would be much appreciated.

---

### Post by shredwheat on 2009-11-24
I've filed a bug against acpi-support. Bug #487436. Hopefully with some "Me too" and further reporting this can get pushed to the right folk?
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/487436](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/487436)

---

### Post by pmeves on 2009-12-10
Got a clevo W860CU and have the same problem... Bluetooth, wifi and others, everything off and cannot turn it on.

Please some help would be appreciated

---

### Post by shredwheat on 2009-12-11
The wifi comes on automatically for me. The only thing I can see missing is the Bluetooth. It sounds like this is a hardware/firmware problem with the ACPI, but I don't have the technical chops to dig in.

---

### Post by pmeves on 2010-02-22
I'm sorry but I really can't turn on Wifi. Bluetooth is not that important regarding the Wireless Lan, for my needs.

I get installation problems in dual-boot also. It messes with my windows boot files... or can't find windows at all.

If someone have news about this I would apreciate to have some answers around here and in other w860cu forums.

I'm in informatic engeneering and working without linux it's impossible.

---

### Post by AndyC_772 on 2010-02-25
Which wireless card do you have fitted?

(Thinking about getting a machine based on the W860CU myself... but not if it doesn't work properly with Ubuntu!)

---

### Post by pmeves on 2010-03-20
> **AndyC_772 said:**
> Which wireless card do you have fitted?

(Thinking about getting a machine based on the W860CU myself... but not if it doesn't work properly with Ubuntu!)

checking in device manager i have:

Realteck RTL8191SE Wireless LAN 802.11n PCI-E NIC 
=
Intel WiFi Link 5100 300Mbps module (802.11 a/b/g/n)

---

### Post by vetrun on 2010-03-27
Hi,

I was thinking of getting one of these notebooks so I'm wondering what is the overall status of running ubuntu on it?

Is there anything major that doesn't work?

Cheers

Steve

---

### Post by AndyC_772 on 2010-03-27
I'm told it all works fine, with the possible exception of Bluetooth - in which case I'd probably just try an external Bluetooth dongle rather than spending too much time worrying about getting the internal one working.

I'd hoped to have my Kobalt G860 by now, which is a W860CU system. Once it arrives, installing Ubuntu is one of the first things I'll do. Fingers crossed it'll be this week.

However, since the W860CU is a modular chassis, with the final choice of components down to the system builder rather than always being the same, it's as well to check that your particular set of components will work. Not all W860CU's are the same.

---

### Post by vetrun on 2010-03-29
I'm giving it a go.

I ordered a W860CU with the ATI 5870HD graphics card so I will let you all know how it goes once it is built/delivered and I have messed with it.

I don't really care about bluetooth and if the wifi has problems I have an old M570U that I can salvage a linux compatible wifi card out of if they haven't changed the specs of the wireless cards in the clevos.

I think these will be the only really different things in builds that could cause issues.

Wish me luck :)


Steve

---

### Post by AndyC_772 on 2010-04-03
I have my Kobalt G860 now (W80CU) and have installed 9.10 on it.

I can confirm that I can't activate Bluetooth either, and nor does the power button do anything. The touch-sensitive email and web buttons do work, though, and so do the volume and brightness Fn-keys.

My wireless card is an Intel 5300 AGN, and it only works on the 2.4 GHz band, not the 5 GHz band. (dmesg shows an error "No TX rate available" after connecting to a 5 GHz network).

Will try the Lucid beta later on and see if that's any better.

---

### Post by vetrun on 2010-04-05
Cheers for that.

Did you go for the ATI Radeon 5870 or the Nvidia? I haven't seen any reports of the ATI and linux yet which I ordered and is currently in the process of being built so I will let you all know once I have it.


Steve

---

### Post by sloik on 2010-04-07
Update: running 10.04 beta 1, hibernating now works properly, when it previously did not.

Suspending can also be achieved by first suspending the laptop by any available means, and then turning the machine back on via the Suspend function key. This hadn't really occurred to me before, so it may very well work using a previous version of Ubuntu.

Lid-closure and power button detection would still be nice, but this still makes my life a whole lot easier.

---

### Post by AndyC_772 on 2010-04-11
I've now tried 10.04 betas 1 and 2.

However, neither was terribly useful as neither will boot beyond the Ubuntu splash screen. They just hang.

Since my PC works fine with both 9.10 and Win7 I'm guessing it must be some difference in our respective hardware configs that's causing the problem.

I have the Nvidia 285M GTX and the 1920x1080 panel - maybe that's the crucial difference? Here's my lspci:

```
lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation Device 060f (rev a2)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
09:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
09:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
09:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
09:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

---

### Post by vetrun on 2010-04-21
Ok, got my W860CU with the ATI 5870HD last night and I installed lucid beta2. 

The basics seemed ok, install went fine and the open source driver was enabled by default running at 1920x1080 so that was good. Wireless and ethernet worked fine. Then I installed the restricted driver and once that was installed advanced desktop effects etc... worked fine.

One thing I noticed was after I did an update a new kernel was installed and if you boot this kernel the screen just stays blank but booting the old kernel on the grub menu still worked fine. I'm guessing this is an issue with the restricted driver not being compatible with the new kernel.

No idea about bluetooth but I'm guessing it doesn't work as nothing popped up about it. Haven't tested the power button and hotkeys yet so I will keep you posted if they work or not.

Overall the important things run fine if anybody is thinking of purchasing one of these for running Ubuntu. I'm overall very impressed with this notebook.


Steve

---

### Post by vetrun on 2010-04-22
Update:

Power button works and brings up the shutdown/logout etc... dialogue.
Suspend works when you close the lid (haven't tested hibernate etc... yet)
Bluetooth seems to be working as the logo comes up in the panel and says that it's activated but I haven't tested it with anything.
The splash screen on booting doesn't work but it still boots up fine.


Steve

---

### Post by fvdnabee on 2010-05-16
My G860 from kobalt-computers.co.uk (W860CU) is arriving tomorrow, I plan installing Ubuntu Lucid Lynx on it.
It's got the following specs : 
CPU:  Intel® Core™ i7-720QM 1.60 -2.80GHz Quad Core-   (45nm, 8MB L2 Cache)
GPU: ATI Mobility Radeon™ 5870 1GB GDDR5
Chipset: Intel PM55
Wifi : 1 x Intel WiFi Link Mini PCI Wireless AGN  (Intel WiFi Link 6300) adapter

I'll post my experiences with installing&running lucid lynx here.

---

### Post by vetrun on 2010-05-16
@fvdnabee

It should be fine as I'm running the x64 version of Lucid and I haven't had any problems. I did have a few problems with the i386 version as it sometimes wouldn't boot but this could be due to installing it when it was in beta and doing updates from then.

---

### Post by fvdnabee on 2010-05-18
I just installed ubuntu 64-bit(10.04 lucid lynx) and wifi, bluetooth, hotkeys are all working fine. I tested the BT by sending files to my phone and receiving and it's working fine. All this out of the box, without any additional configuration whatsoever!
Also installed the ati drivers and those are also working.

Suspend to ram by closing the lid or pressing fn+f4 is working properly,  suspend to disc by using the gnome power manager(upper right corner) is  also working fine.

I must say I'm impressed how much just works out of the box.
I only had to install the ati drivers, which isn't such a big deal.

sudo lshw output:
> 
floris-laptop
    description: Laptop
    product: W860CU
    vendor: CLEVO CO.
    version: Not Applicable
    serial: Not Applicable
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=laptop frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=0090F59F-C45D-0000-0000-000000000000
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: CALPELLACRB.86C.0000.X.0000000000 (05/04/2010)
          size: 117KiB
          capacity: 4032KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-board UNCLAIMED
          description: Mother Board
          product: W860CU
          vendor: CLEVO CO.
          physical id: 2
          version: Not Applicable
          serial: Not Applicable
          slot: Not Applicable
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Genuine Intel(R) CPU
          slot: CPU 1
          size: 933MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: burst internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             size: 6MiB
             capacity: 8MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: CMSO2GX3M1A1333C9
             vendor: 029E
             physical id: 0
             serial: 00000000
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: CMSO2GX3M1A1333C9
             vendor: 029E
             physical id: 1
             serial: 00000000
             slot: M2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: SODIMM Synchronous [empty]
             physical id: 2
             slot: M3
        *-bank:3
             description: SODIMM Synchronous [empty]
             physical id: 3
             slot: M4
     *-pci:0
          description: Host bridge
          product: Core Processor DMI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:2000(size=4096) memory:cfe00000-cfefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:38 memory:d0000000-dfffffff(prefetchable) memory:cfee0000-cfefffff ioport:2000(size=256) memory:cfe00000-cfe1ffff(prefetchable)
           *-multimedia
                description: Audio device
                product: Juniper HDMI Audio [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:cfedc000-cfedffff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f1606000-f16063ff
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
             resources: irq:22 memory:f1600000-f1603fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:3000(size=4096) memory:f0a00000-f0bfffff ioport:f0000000(size=2097152)
           *-network
                description: Wireless interface
                product: WiFi Link 6000 Series
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 35
                serial: 00:24:d7:1c:97:88
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:37 memory:f0a00000-f0a01fff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:4000(size=4096) memory:f0c00000-f0dfffff ioport:f0200000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:32 ioport:5000(size=4096) memory:f0e00000-f0ffffff ioport:f0400000(size=2097152)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 03
                serial: 00:90:f5:9f:c4:5d
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.15 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:36 ioport:5000(size=256) memory:f0504000-f0504fff(prefetchable) memory:f0400000-f0403fff(prefetchable) memory:f0420000-f043ffff(prefetchable)
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:33 ioport:6000(size=4096) memory:f1000000-f11fffff ioport:f0600000(size=2097152)
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:09:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=ohci1394 latency=0
                resources: irq:16 memory:f1100800-f1100fff memory:f1101000-f110107f memory:f1100400-f110047f memory:f1000000-f100007f
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:09:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f1101400-f11014ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:09:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f1101800-f11018ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:09:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:f1101c00-f1101cff
        *-pci:5
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:34 ioport:7000(size=4096) memory:f1200000-f13fffff ioport:f0800000(size=2097152)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f1606400-f16067ff
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
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
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:35 ioport:1830(size=8) ioport:1824(size=4) ioport:1828(size=8) ioport:1820(size=4) ioport:1800(size=32) memory:f1605000-f16057ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEKT-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXJ1A1018454
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=bf2cb228
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/Door systeem gereserveerd
                   version: 3.1
                   serial: 8a2d-9fe6
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-05-17 18:51:21 filesystem=ntfs label=Door systeem gereserveerd mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/6ECA34E1CA34A76D
                   version: 3.1
                   serial: bc6dc384-5d9b-3d40-907a-72854fbca083
                   size: 99GiB
                   capacity: 100GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-05-17 18:51:32 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 20GiB
                   capacity: 20GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1906MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 9536MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 9536MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7580S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: FX04
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
             resources: memory:f1606800-f16068ff ioport:1840(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:03.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:03.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Core Processor Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:ff:03.4
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:ff:04.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:ff:04.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:ff:04.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:ff:04.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:ff:05.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:ff:05.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:ff:05.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:ff:05.3
          version: 04
          width: 32 bits
          clock: 33MHz
  *-battery
       description: Lithium Ion Battery
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1
       slot: Rear
       capacity: 1000mWh
       configuration: voltage=0.0V
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

### Post by fvdnabee on 2010-05-18
Suspend to ram by closing the lid or pressing fn+f4 is working properly, suspend to disc by using the gnome power manager(upper right corner) is also working fine.
I must say I'm impressed how much just works out of the box.
I only had to install the ati drivers, which isn't such a big deal.

---

### Post by fvdnabee on 2010-05-19
Has anyone been able to lower the cpu/gpu fan speed. I ask this beause I find them way to loud when I'm  doing some surfing and nothing else.
You wouldn't expect it needs alot of cooling when you're only surfing, would you?

---

### Post by delbyblue on 2010-05-26
I have a Clevo W860CU with Kubuntu 10.04, but some of my hotkeys (bluetooth, wi-fi, ecc.) does not work at all. Can anybody point me to some doc on how to enable/help implement those keys support?
Thx in advance.

---

### Post by fvdnabee on 2010-06-04
> **delbyblue said:**
> I have a Clevo W860CU with Kubuntu 10.04, but some of my hotkeys (bluetooth, wi-fi, ecc.) does not work at all. Can anybody point me to some doc on how to enable/help implement those keys support?
Thx in advance.
Can't help you, here everything worked out of the box. Allthough I've switched to gnome from XFCE now(not using KDE either), maybe there is a package that comes with gnome that enables hotkey support?

Quick question of mine: is there anyone using the 5870m graphics card?
I can't seem to find any drivers on the ati website for this(only for 4000m), so what are you guys using? For the moment I'm using FGLRX which I got from the wizard in ubuntu. I do wonder how this is possible because the 5870m isn't supported on the ati drivers page.

---

### Post by vetrun on 2010-06-04
The official ati driver packages are already in ubuntu and should popup in hardware/restricted drivers. Then just click install and away you go. They work fine on my 5870 :)

Steve

---

### Post by fvdnabee on 2010-06-04
They work fine indeed, but officialy the 5870m is not supported for linux.
It's also a rather old version.

Do you know if it's possible to downclock the 5780m under ubuntu, vetrun?
In windows i have it running on 200/300 instead of 700/100, it runs cooler(GPU fan doesn't make any noise).

---

### Post by fvdnabee on 2010-08-04
Still using ubuntu lucid lynx as my daily OS on my clevo W860CU. I'm using gnome and all in all i'm rather happy. Allmost everything works.

The reason why i'm making this post however is the release of the linux 2.6.35 kernel that enables support for ati graphics card powersaving options. Because my w860cu has an 5870m this could be quite usefull to quiet down the cooling.
Has anyone tried out this kernel with the w860cu? I've read that you can use new kernels in lucid lynx by installing the maverick-linux package from a 3rd party PPA but haven't tried it yet myself.

---

### Post by fvdnabee on 2010-10-17
Switched to maverick on my w860cu, running the 2.6.35 kernel but I haven't noticed any difference in power usage.
Occasionally waking up from suspend to RAM fails and I have to reboot with the power button, this is the only issue I've come across thus far.

---

### Post by shredwheat on 2010-10-17
I had the same problem with the Bluetooth and Wireless kill switches not working. The problem is due to ACPI mistakes on the system, so there were no keyboard configuration tools that would fix it.

Fortunately, upgrading to the 1.01.11s firmware took care of the hotkey problem. Unfortunately the built in camera no longer works, which it used to. The camera doesn't work in Windows or Linux, so it seems like a problem with the new firmware.

You can find the firmware vendors websites that sell the laptop, but not from Clevo's website. I grabbed Sager's version of the firmware, [http://74.212.252.103/Sagernotebook/misc/869bv111s.zip](http://74.212.252.103/Sagernotebook/misc/869bv111s.zip)

---

### Post by fvdnabee on 2011-01-23
Today I have stumbled upon an awesome application that everyone who is running an ati 5870m should have, it's called [AMDOverdriveCtrl]("https://sourceforge.net/projects/amdovdrvctrl/"). The application only works with the proprietary ATI drivers but I'm using those anyways.
Basically what AMDOverdriveCtrl allows you to do is to underclock your 5870m card.

My experience:
The application has allowed me to lower my core and memory speed to  350/500Mhz and my voltage to 0.850V. This has lowered my idle  temperatures from 55C to 45C and has reduced fan noise considerably-it  even runs quieter than under windows after underclocking with the AMD  GPU Tool.  My notebook is much much much quieter now, it's really a huge improvement that I'm very happy with. 
I'm actually quite surprised it worked because I can't control the ATI Overdrive functionality using aticontrol binary that is provided with the fglrx drivers. With AMDOverdriveCTRL it does work however :)
Offcourse YMMV but when you're experiencing a lot of fan noise(like me) I suggest you try this out!

I'm running ubuntu maverick(10.10, 2.6.35 kernel) with ATI catalyst 10.12 drivers on my Clevo W860CU.

---

