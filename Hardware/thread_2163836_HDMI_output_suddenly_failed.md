---
title: "HDMI output suddenly failed"
date: 2013-07-19
forum: Hardware
---

### Post by gbooty on 2013-07-19
All I've done is a some software updates (automatic updates), nothing else happened to my laptop. I've looked online, most people with HDMI problems at least show that HDMI exists in xrandr.  From my understanding, my video drivers came with the fresh 13.04 install I did. I've never had any problems with HDMI output until today. Any ideas on what it could be? There are 3 "unclamied" items from lshw output. Don't know if one of the is HDMI?    /br    xrandr output    Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767 LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm    1366x768       60.0*+    1360x768       59.8     60.0      1024x768       60.0      800x600        60.3     56.2      640x480        59.9    VGA1 disconnected (normal left inverted right x axis y axis)     lshw output     d  description: Computer     width: 64 bits     capabilities: vsyscall32   *-core        description: Motherboard        physical id: 0      *-memory           description: System memory           physical id: 0           size: 3772MiB      *-cpu           product: Intel(R) Pentium(R) CPU B960 @ 2.20GHz           vendor: Intel Corp.           physical id: 1           bus info: cpu@0           size: 800MHz           capacity: 800MHz           width: 64 bits           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave lahf_lm arat epb xsaveopt pln pts dtherm cpufreq      *-pci           description: Host bridge           product: 2nd Generation Core Processor Family DRAM Controller           vendor: Intel Corporation           physical id: 100           bus info: pci@0000:00:00.0           version: 09           width: 32 bits           clock: 33MHz         *-display              description: VGA compatible controller              product: 2nd Generation Core Processor Family Integrated Graphics Controller              vendor: Intel Corporation              physical id: 2              bus info: pci@0000:00:02.0              version: 09              width: 64 bits              clock: 33MHz              capabilities: vga_controller bus_master cap_list rom              configuration: driver=i915 latency=0              resources: irq:41 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:2000(size=64)         *-communication              description: Communication controller              product: 7 Series/C210 Series Chipset Family MEI Controller #1              vendor: Intel Corporation              physical id: 16              bus info: pci@0000:00:16.0              version: 04              width: 64 bits              clock: 33MHz              capabilities: bus_master cap_list              configuration: driver=mei latency=0              resources: irq:42 memory:c0604000-c060400f         *-usb:0              description: USB controller              product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2              vendor: Intel Corporation              physical id: 1a              bus info: pci@0000:00:1a.0              version: 04              width: 32 bits              clock: 33MHz              capabilities: ehci bus_master cap_list              configuration: driver=ehci-pci latency=0              resources: irq:16 memory:c0609000-c06093ff         *-multimedia              description: Audio device              product: 7 Series/C210 Series Chipset Family High Definition Audio Controller              vendor: Intel Corporation              physical id: 1b              bus info: pci@0000:00:1b.0              version: 04              width: 64 bits              clock: 33MHz              capabilities: bus_master cap_list              configuration: driver=snd_hda_intel latency=0              resources: irq:43 memory:c0600000-c0603fff         *-pci:0              description: PCI bridge              product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1              vendor: Intel Corporation              physical id: 1c              bus info: pci@0000:00:1c.0              version: c4              width: 32 bits              clock: 33MHz              capabilities: pci normal_decode bus_master cap_list              configuration: driver=pcieport              resources: irq:17 memory:afb00000-afbfffff ioport:c0400000(size=1048576)            *-network                 description: Ethernet interface                 product: NetLink BCM57785 Gigabit Ethernet PCIe                 vendor: Broadcom Corporation                 physical id: 0                 bus info: pci@0000:02:00.0                 logical name: eth0                 version: 10                 serial: a5:12:c7:ed:22:21                 capacity: 1Gbit/s                 width: 64 bits                 clock: 33MHz                 capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                 configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=sb latency=0 link=no multicast=yes port=twisted pair                 resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff            *-generic:0                 description: SD Host controller                 product: NetXtreme BCM57765 Memory Card Reader                 vendor: Broadcom Corporation                 physical id: 0.1                 bus info: pci@0000:02:00.1                 version: 10                 width: 64 bits                 clock: 33MHz                 capabilities: bus_master cap_list                 configuration: driver=sdhci-pci latency=0                 resources: irq:17 memory:c0400000-c040ffff            *-generic:1 UNCLAIMED                 description: System peripheral                 product: Broadcom Corporation                 vendor: Broadcom Corporation                 physical id: 0.2                 bus info: pci@0000:02:00.2                 version: 10                 width: 64 bits                 clock: 33MHz                 capabilities: bus_master cap_list                 configuration: latency=0                 resources: memory:c0410000-c041ffff            *-generic:2 UNCLAIMED                 description: System peripheral                 product: Broadcom Corporation                 vendor: Broadcom Corporation                 physical id: 0.3                 bus info: pci@0000:02:00.3                 version: 10                 width: 64 bits                 clock: 33MHz                 capabilities: bus_master cap_list                 configuration: latency=0                 resources: memory:c0420000-c042ffff         *-pci:1              description: PCI bridge              product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2              vendor: Intel Corporation              physical id: 1c.1              bus info: pci@0000:00:1c.1              version: c4              width: 32 bits              clock: 33MHz              capabilities: pci normal_decode bus_master cap_list              configuration: driver=pcieport              resources: irq:16 memory:c0500000-c05fffff            *-network                 description: Network controller                 product: BCM4313 802.11b/g/n Wireless LAN Controller                 vendor: Broadcom Corporation                 physical id: 0                 bus info: pci@0000:02:00.0                 version: 01                 width: 64 bits                 clock: 33MHz                 capabilities: bus_master cap_list                 configuration: driver=bcma-pci-bridge latency=0                 resources: irq:17 memory:c0500000-c0503fff         *-usb:1              description: USB controller              product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1              vendor: Intel Corporation              physical id: 1d              bus info: pci@0000:00:1d.0              version: 04              width: 32 bits              clock: 33MHz              capabilities: ehci bus_master cap_list              configuration: driver=ehci-pci latency=0              resources: irq:23 memory:c0608000-c06083ff         *-isa              description: ISA bridge              product: 7 Series Chipset Family LPC Controller              vendor: Intel Corporation              physical id: 1f              bus info: pci@0000:00:1f.0              version: 04              width: 32 bits              clock: 33MHz              capabilities: isa bus_master cap_list              configuration: driver=lpc_ich latency=0              resources: irq:0         *-storage              description: SATA controller              product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]              vendor: Intel Corporation              physical id: 1f.2              bus info: pci@0000:00:1f.2              version: 04              width: 32 bits              clock: 66MHz              capabilities: storage ahci_1.0 bus_master cap_list              configuration: driver=ahci latency=0              resources: irq:40 ioport:2088(size=8) ioport:2094(size=4) ioport:2080(size=8) ioport:2090(size=4) ioport:2060(size=32) memory:c0607000-c06077ff         *-serial UNCLAIMED              description: SMBus              product: 7 Series/C210 Series Chipset Family SMBus Controller              vendor: Intel Corporation              physical id: 1f.3              bus info: pci@0000:00:1f.3              version: 04              width: 64 bits              clock: 33MHz              configuration: latency=0              resources: memory:c0605000-c06050ff ioport:2040(size=32)

---

### Post by gbooty on 2013-07-19
Do I have to use /br or something? Is no-script making my post look insane? no script also makes the ctrl+f feature fail in mozilla.....

---

### Post by Boab1993 on 2013-07-19
This might take a bit of reading haha

But as far as i can tell the first UNCLAIMED broadcom item looks like a card 

Second a PCI Slot

Third has something to do with SMBuses (system management buses), they take data like clock data etc.

As for where you HDMI is in all that, gonna need to get my glasses out first.

---

### Post by gbooty on 2013-07-19
All I've done is a some software updates (automatic updates), nothing else happened to my laptop. I've looked online, most people with HDMI problems at least show that HDMI exists in xrandr. From my understanding, my video drivers came with the fresh 13.04 install I did. I've never had any problems with HDMI output until today. Any ideas on what it could be? There are 3 "unclamied" items from lshw output. Don't know if one of the is HDMI?
```
<br><br>
<b>
[B]xrandr output
<br>


Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)[/B]

</b>
<br><br>
sudo lshw output
<br>
     *-firmware
          description: BIOS
          vendor: Gateway
          physical id: 0
          version: V2.04
          date: 09/14/2012
          size: 128KiB
          capacity: 3520KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU B960 @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU B960 @ 2.20GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave lahf_lm arat epb xsaveopt pln pts dtherm cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: d
             slot: L3 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
     *-cache
          description: L1 cache
          physical id: a
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-04-18 12:23+0000X-Generator: Launchpad (build 16567) [empty]
             product: Empty
             vendor: Empty
             physical id: 0
             serial: Empty
             slot: DIMM0
        *-bank:1
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-04-18 12:23+0000X-Generator: Launchpad (build 16567) [empty]
             product: Empty
             vendor: Empty
             physical id: 1
             serial: Empty
             slot: DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT451S6MFR8C-PB
             vendor: Unknown
             physical id: 2
             serial: 324865BE
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-04-18 12:23+0000X-Generator: Launchpad (build 16567) [empty]
             product: Empty
             vendor: Empty
             physical id: 3
             serial: Empty
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
<b>
        [B]*-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:2000(size=64)[/B]
</b>
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:42 memory:c0604000-c060400f
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:c0609000-c06093ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:c0600000-c0603fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:afb00000-afbfffff ioport:c0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: NetLink BCM57785 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: f1:11:c5:82:d2:12
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=sb latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
[B]<b>
<br><br><br><br>
           *-generic:0
                description: SD Host controller
                product: NetXtreme BCM57765 Memory Card Reader
                vendor: Broadcom Corporation
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:c0400000-c040ffff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:c0410000-c041ffff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:c0420000-c042ffff
</b>[/B]
<br><br><br><br><br>
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:c0500000-c05fffff
           *-network
                description: Network controller
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=bcma-pci-bridge latency=0
                resources: irq:17 memory:c0500000-c0503fff
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:c0608000-c06083ff
        *-isa
             description: ISA bridge
             product: 7 Series Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:2088(size=8) ioport:2094(size=4) ioport:2080(size=8) ioport:2090(size=4) ioport:2060(size=32) memory:c0607000-c06077ff
[B]<b>
<br><br><br>
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0605000-c06050ff ioport:2040(size=32)
</b>[/B]
<br><br><br><br>
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ8C0
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 29:19:83:21:80:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.8.0-26-generic firmware=N/A ip=10.219.22.195 link=yes multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by gbooty on 2013-07-19
I'm sorry about the post with no breaks, I think it was because of no-script.

My ethernet, wireless, SD memory card reader, dvd (had some problems with linux before, reading cd/dvds, but fixed it), vga, and usb works. Basically everything except the HDMI all of the sudden. I ask about the unclaimed report from lshw because I'm hoping it's the HDMI. 

The only problem I've had continually with ubuntu is a system error whenever I close the lid and go into hibernate mode. It's never actually bothered me though so I've ignored it. All of the other problems I ran into I was able to resolve myself after reading through these forums. I'm stumped so far though, it's annoying that the HDMI failed out of no where. My desktop motherboard just broke, and my xbox, so, with all this luck is it possible the hdmi on board my laptop broke? I could install a dual boot of windows if any of you guys thinks it's a possibility.

EDIT:
[http://ubuntuforums.org/showthread.php?t=2145343](http://ubuntuforums.org/showthread.php?t=2145343)
This guy had a similar problem (he upgraded versions of ubuntu, I on the other hand, have always had 13.04, never changed it), but no solution, just luck after a reboot (which I did several times)

"My laptop crashed today, and when I rebooted the HDMI was working again.  I had tried to swap intel_drv.so for the one from 12.04 but that hadn't  worked, so swapped it back. But that was a few hours before the crash  and rebooted a couple of times in that period. The only sane thing that I  can think happened between the last boot and the crash that "fixed" me  was that I used usb-creator-gtk to burn a recovery usb stick in case my  messing with intel_drv.so ended in disaster. 

I'm not happy that this is an explanation, and I've no idea why HDMI  went away, and then came back again. Ah well, there are more things in  heaven and earth."

---

### Post by gbooty on 2013-07-19
I read xorg.log and xorg.conf might have something to do with it, but primarily for people with nvidia cards (I have Intel HD Graphics).


[    30.218] (II) No input driver specified, ignoring this device.
[    30.219] (II) This device may have been added with another device file.
[    30.219] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    30.219] (II) No input driver specified, ignoring this device.
[    30.219] (II) This device may have been added with another device file.
**[    30.219] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)**
[    30.219] (II) No input driver specified, ignoring this device.
[    30.219] (II) This device may have been added with another device file.


I feel like I'm slowly getting on the right track

---

### Post by gbooty on 2013-07-19
Well, after another reboot, this time, everything works now, just like with the guy before (link provided in previous post). Solved but not understood.

```
xrandr output

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
[B]HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)[/B]

:popcorn:


I'm one of the few idiots I've come across on here and google who have had this problem. I've noticed a difference in the xorg.log file (xorg.conf is defualt, I never tried changing it). For future reference I'll post both logs (recognized hdmi and the older unrecognized)

Here is the working xorg.log

[    30.520] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    30.520] X Protocol Version 11, Revision 0
[    30.520] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    30.520] Current Operating System: Linux j-NE56R 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64
[    30.520] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=f2b6583a-8aa1-46fc-aa0d-6cb0e0f02ea5 ro quiet splash vt.handoff=7
[    30.520] Build Date: 17 April 2013  10:43:13PM
[    30.520] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    30.520] Current version of pixman: 0.28.2
[    30.520]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    30.520] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.520] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 19 20:47:47 2013
[    30.535] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.535] (==) No Layout section.  Using the first Screen section.
[    30.535] (==) No screen section available. Using defaults.
[    30.535] (**) |-->Screen "Default Screen Section" (0)
[    30.535] (**) |   |-->Monitor "<default monitor>"
[    30.535] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    30.535] (==) Automatically adding devices
[    30.535] (==) Automatically enabling devices
[    30.535] (==) Automatically adding GPU devices
[    30.535] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.535]     Entry deleted from font path.
[    30.535] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    30.535]     Entry deleted from font path.
[    30.535] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    30.535]     Entry deleted from font path.
[    30.535] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    30.535]     Entry deleted from font path.
[    30.535] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    30.535]     Entry deleted from font path.
[    30.535] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    30.535]     Entry deleted from font path.
[    30.535] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    30.535] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.535] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.535] (II) Loader magic: 0x7fbeef11cd20
[    30.535] (II) Module ABI versions:
[    30.535]     X.Org ANSI C Emulation: 0.4
[    30.535]     X.Org Video Driver: 13.1
[    30.535]     X.Org XInput driver : 18.0
[    30.535]     X.Org Server Extension : 7.0
[    30.535] (II) config/udev: Adding drm device (/dev/dri/card0)
[    30.537] (--) PCI:*(0:0:2:0) 8086:0106:1025:0649 rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00002000/64
[    30.537] (II) Open ACPI successful (/var/run/acpid.socket)
[    30.537] Initializing built-in extension Generic Event Extension
[    30.537] Initializing built-in extension SHAPE
[    30.537] Initializing built-in extension MIT-SHM
[    30.537] Initializing built-in extension XInputExtension
[    30.537] Initializing built-in extension XTEST
[    30.537] Initializing built-in extension BIG-REQUESTS
[    30.537] Initializing built-in extension SYNC
[    30.537] Initializing built-in extension XKEYBOARD
[    30.537] Initializing built-in extension XC-MISC
[    30.537] Initializing built-in extension SECURITY
[    30.537] Initializing built-in extension XINERAMA
[    30.537] Initializing built-in extension XFIXES
[    30.537] Initializing built-in extension RENDER
[    30.537] Initializing built-in extension RANDR
[    30.537] Initializing built-in extension COMPOSITE
[    30.537] Initializing built-in extension DAMAGE
[    30.537] Initializing built-in extension MIT-SCREEN-SAVER
[    30.537] Initializing built-in extension DOUBLE-BUFFER
[    30.537] Initializing built-in extension RECORD
[    30.537] Initializing built-in extension DPMS
[    30.537] Initializing built-in extension X-Resource
[    30.537] Initializing built-in extension XVideo
[    30.537] Initializing built-in extension XVideo-MotionCompensation
[    30.537] Initializing built-in extension SELinux
[    30.537] Initializing built-in extension XFree86-VidModeExtension
[    30.537] Initializing built-in extension XFree86-DGA
[    30.537] Initializing built-in extension XFree86-DRI
[    30.537] Initializing built-in extension DRI2
[    30.537] (II) LoadModule: "glx"
[    31.283] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    31.283] (II) Module glx: vendor="X.Org Foundation"
[    31.283]     compiled for 1.13.3, module version = 1.0.0
[    31.283]     ABI class: X.Org Server Extension, version 7.0
[    31.283] (==) AIGLX enabled
[    31.283] Loading extension GLX
[    31.283] (==) Matched intel as autoconfigured driver 0
[    31.283] (==) Matched intel as autoconfigured driver 1
[    31.283] (==) Matched vesa as autoconfigured driver 2
[    31.283] (==) Matched modesetting as autoconfigured driver 3
[    31.283] (==) Matched fbdev as autoconfigured driver 4
[    31.283] (==) Assigned the driver to the xf86ConfigLayout
[    31.283] (II) LoadModule: "intel"
[    31.283] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    31.372] (II) Module intel: vendor="X.Org Foundation"
[    31.372]     compiled for 1.13.3, module version = 2.21.6
[    31.372]     Module class: X.Org Video Driver
[    31.372]     ABI class: X.Org Video Driver, version 13.1
[    31.372] (II) LoadModule: "vesa"
[    31.373] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.373] (II) Module vesa: vendor="X.Org Foundation"
[    31.373]     compiled for 1.12.99.902, module version = 2.3.2
[    31.373]     Module class: X.Org Video Driver
[    31.373]     ABI class: X.Org Video Driver, version 13.0
[    31.373] (II) LoadModule: "modesetting"
[    31.373] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    31.373] (II) Module modesetting: vendor="X.Org Foundation"
[    31.373]     compiled for 1.13.3, module version = 0.7.0
[    31.373]     Module class: X.Org Video Driver
[    31.373]     ABI class: X.Org Video Driver, version 13.1
[    31.373] (II) LoadModule: "fbdev"
[    31.373] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    31.373] (II) Module fbdev: vendor="X.Org Foundation"
[    31.373]     compiled for 1.12.99.902, module version = 0.4.3
[    31.373]     Module class: X.Org Video Driver
[    31.373]     ABI class: X.Org Video Driver, version 13.0
[    31.373] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    31.374] (II) VESA: driver for VESA chipsets: vesa
[    31.374] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    31.374] (II) FBDEV: driver for framebuffer: fbdev
[    31.374] (++) using VT number 7

[    31.374] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.6-0ubuntu4 (Bryce Harrington <bryce@ubuntu.com>)
[    31.374] (WW) Falling back to old probe method for vesa
[    31.374] (WW) Falling back to old probe method for modesetting
[    31.374] (WW) Falling back to old probe method for fbdev
[    31.374] (II) Loading sub module "fbdevhw"
[    31.374] (II) LoadModule: "fbdevhw"
[    31.374] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    31.374] (II) Module fbdevhw: vendor="X.Org Foundation"
[    31.374]     compiled for 1.13.3, module version = 0.0.2
[    31.374]     ABI class: X.Org Video Driver, version 13.1
[    31.374] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    31.374] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    31.374] (==) intel(0): RGB weight 888
[    31.374] (==) intel(0): Default visual is TrueColor
[    31.374] (--) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT1)
[    31.375] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[    31.375] (**) intel(0): Framebuffer tiled
[    31.375] (**) intel(0): Pixmaps tiled
[    31.375] (**) intel(0): "Tear free" disabled
[    31.375] (**) intel(0): Forcing per-crtc-pixmaps? no
[    31.375] (II) intel(0): Output LVDS1 has no monitor section
[    31.472] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    31.488] (II) intel(0): Output VGA1 has no monitor section
[    31.504] (II) intel(0): Output HDMI1 has no monitor section
[    31.552] (II) intel(0): Output DP1 has no monitor section
[    31.552] (II) intel(0): EDID for output LVDS1
[    31.552] (II) intel(0): Manufacturer: AUO  Model: 26ec  Serial#: 0
[    31.552] (II) intel(0): Year: 2009  Week: 1
[    31.552] (II) intel(0): EDID Version: 1.3
[    31.552] (II) intel(0): Digital Display Input
[    31.552] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    31.552] (II) intel(0): Gamma: 2.20
[    31.552] (II) intel(0): No DPMS capabilities specified
[    31.552] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    31.552] (II) intel(0): First detailed timing is preferred mode
[    31.552] (II) intel(0): redX: 0.577 redY: 0.333   greenX: 0.333 greenY: 0.554
[    31.552] (II) intel(0): blueX: 0.161 blueY: 0.144   whiteX: 0.313 whiteY: 0.329
[    31.552] (II) intel(0): Manufacturer's mask: 0
[    31.552] (II) intel(0): Supported detailed timing:
[    31.552] (II) intel(0): clock: 71.8 MHz   Image Size:  344 x 193 mm
[    31.552] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    31.552] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 784 v_border: 0
[    31.552] (II) intel(0): Unknown vendor-specific block f
[    31.552] (II) intel(0):  AUO
[    31.552] (II) intel(0):  B156XW02 V6
[    31.552] (II) intel(0): EDID (in hex):
[    31.552] (II) intel(0):     00ffffffffffff0006afec2600000000
[    31.552] (II) intel(0):     01130103802213780ad7759355558d29
[    31.552] (II) intel(0):     24505400000001010101010101010101
[    31.552] (II) intel(0):     0101010101010c1c56a0500010303020
[    31.552] (II) intel(0):     360058c1100000180000000f00000000
[    31.552] (II) intel(0):     00000000000000000020000000fe0041
[    31.552] (II) intel(0):     554f0a202020202020202020000000fe
[    31.552] (II) intel(0):     004231353658573032205636200a0065
[    31.552] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    31.552] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    31.552] (II) intel(0): Printing probed modes for output LVDS1
[    31.552] (II) intel(0): Modeline "1366x768"x60.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    31.552] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    31.552] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    31.552] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    31.552] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    31.552] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    31.552] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    31.568] (II) intel(0): EDID for output VGA1
[    31.584] (II) intel(0): EDID for output HDMI1
[    31.632] (II) intel(0): EDID for output DP1
[    31.632] (II) intel(0): Output LVDS1 connected
[    31.632] (II) intel(0): Output VGA1 disconnected
[    31.632] (II) intel(0): Output HDMI1 disconnected
[    31.632] (II) intel(0): Output DP1 disconnected
[    31.632] (II) intel(0): Using exact sizes for initial modes
[    31.632] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    31.632] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    31.632] (==) intel(0): DPI set to (96, 96)
[    31.632] (II) Loading sub module "dri2"
[    31.632] (II) LoadModule: "dri2"
[    31.632] (II) Module "dri2" already built-in
[    31.632] (II) UnloadModule: "vesa"
[    31.632] (II) Unloading vesa
[    31.632] (II) UnloadModule: "modesetting"
[    31.632] (II) Unloading modesetting
[    31.632] (II) UnloadModule: "fbdev"
[    31.632] (II) Unloading fbdev
[    31.632] (II) UnloadSubModule: "fbdevhw"
[    31.632] (II) Unloading fbdevhw
[    31.632] (==) Depth 24 pixmap format is 32 bpp
[    31.632] (II) intel(0): SNA initialized with SandyBridge backend
[    31.632] (==) intel(0): Backing store disabled
[    31.632] (==) intel(0): Silken mouse enabled
[    31.632] (II) intel(0): HW Cursor enabled
[    31.632] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    31.633] (==) intel(0): DPMS enabled
[    31.633] (II) intel(0): [DRI2] Setup complete
[    31.633] (II) intel(0): [DRI2]   DRI driver: i965
[    31.633] (II) intel(0): direct rendering: DRI2 Enabled
[    31.633] (==) intel(0): hotplug detection: "enabled"
[    31.633] (--) RandR disabled
[    31.637] (II) SELinux: Disabled on system
[    32.043] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    32.043] (II) AIGLX: enabled GLX_INTEL_swap_event
[    32.043] (II) AIGLX: enabled GLX_ARB_create_context
[    32.043] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    32.043] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    32.043] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    32.043] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    32.043] (II) AIGLX: Loaded and initialized i965
[    32.043] (II) GLX: Initialized DRI2 GL provider for screen 0
[    32.043] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[    32.056] (II) intel(0): Setting screen physical size to 361 x 203
[    32.063] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    32.065] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    32.065] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.065] (II) LoadModule: "evdev"
[    32.065] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.101] (II) Module evdev: vendor="X.Org Foundation"
[    32.101]     compiled for 1.13.3, module version = 2.7.3
[    32.101]     Module class: X.Org XInput Driver
[    32.101]     ABI class: X.Org XInput driver, version 18.0
[    32.101] (II) Using input driver 'evdev' for 'Power Button'
[    32.101] (**) Power Button: always reports core events
[    32.101] (**) evdev: Power Button: Device: "/dev/input/event3"
[    32.101] (--) evdev: Power Button: Vendor 0 Product 0x1
[    32.101] (--) evdev: Power Button: Found keys
[    32.101] (II) evdev: Power Button: Configuring as keyboard
[    32.101] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    32.101] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    32.101] (**) Option "xkb_rules" "evdev"
[    32.101] (**) Option "xkb_model" "pc105"
[    32.101] (**) Option "xkb_layout" "us"
[    32.101] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    32.101] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    32.101] (II) Using input driver 'evdev' for 'Video Bus'
[    32.101] (**) Video Bus: always reports core events
[    32.101] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    32.101] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    32.101] (--) evdev: Video Bus: Found keys
[    32.101] (II) evdev: Video Bus: Configuring as keyboard
[    32.101] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    32.101] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    32.101] (**) Option "xkb_rules" "evdev"
[    32.101] (**) Option "xkb_model" "pc105"
[    32.101] (**) Option "xkb_layout" "us"
[    32.102] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    32.102] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.102] (II) Using input driver 'evdev' for 'Power Button'
[    32.102] (**) Power Button: always reports core events
[    32.102] (**) evdev: Power Button: Device: "/dev/input/event0"
[    32.102] (--) evdev: Power Button: Vendor 0 Product 0x1
[    32.102] (--) evdev: Power Button: Found keys
[    32.102] (II) evdev: Power Button: Configuring as keyboard
[    32.102] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    32.102] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    32.102] (**) Option "xkb_rules" "evdev"
[    32.102] (**) Option "xkb_model" "pc105"
[    32.102] (**) Option "xkb_layout" "us"
[    32.102] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    32.102] (II) No input driver specified, ignoring this device.
[    32.102] (II) This device may have been added with another device file.
[    32.102] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    32.102] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    32.103] (II) Using input driver 'evdev' for 'Sleep Button'
[    32.103] (**) Sleep Button: always reports core events
[    32.103] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    32.103] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    32.103] (--) evdev: Sleep Button: Found keys
[    32.103] (II) evdev: Sleep Button: Configuring as keyboard
[    32.103] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input2/event2"
[    32.103] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    32.103] (**) Option "xkb_rules" "evdev"
[    32.103] (**) Option "xkb_model" "pc105"
[    32.103] (**) Option "xkb_layout" "us"
[    32.103] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    32.103] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    32.103] (II) config/udev: Adding input device HD WebCam (/dev/input/event8)
[    32.103] (**) HD WebCam: Applying InputClass "evdev keyboard catchall"
[    32.103] (II) Using input driver 'evdev' for 'HD WebCam'
[    32.103] (**) HD WebCam: always reports core events
[    32.103] (**) evdev: HD WebCam: Device: "/dev/input/event8"
[    32.103] (--) evdev: HD WebCam: Vendor 0x4f2 Product 0xb374
[    32.103] (--) evdev: HD WebCam: Found keys
[    32.103] (II) evdev: HD WebCam: Configuring as keyboard
[    32.103] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input8/event8"
[    32.103] (II) XINPUT: Adding extended input device "HD WebCam" (type: KEYBOARD, id 10)
[    32.103] (**) Option "xkb_rules" "evdev"
[    32.103] (**) Option "xkb_model" "pc105"
[    32.103] (**) Option "xkb_layout" "us"
[    32.104] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    32.104] (II) No input driver specified, ignoring this device.
[    32.104] (II) This device may have been added with another device file.
[    32.104] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    32.104] (II) No input driver specified, ignoring this device.
[    32.104] (II) This device may have been added with another device file.
[    32.104] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    32.104] (II) No input driver specified, ignoring this device.
[    32.104] (II) This device may have been added with another device file.
[    32.104] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    32.104] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    32.104] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    32.104] (**) AT Translated Set 2 keyboard: always reports core events
[    32.104] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    32.104] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    32.104] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    32.104] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    32.104] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    32.104] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    32.104] (**) Option "xkb_rules" "evdev"
[    32.104] (**) Option "xkb_model" "pc105"
[    32.104] (**) Option "xkb_layout" "us"
[    32.105] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event12)
[    32.105] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    32.105] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    32.105] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    32.105] (II) LoadModule: "synaptics"
[    32.105] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    32.105] (II) Module synaptics: vendor="X.Org Foundation"
[    32.105]     compiled for 1.13.1.901, module version = 1.6.2
[    32.105]     Module class: X.Org XInput Driver
[    32.105]     ABI class: X.Org XInput driver, version 18.0
[    32.105] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    32.105] (**) ETPS/2 Elantech Touchpad: always reports core events
[    32.105] (**) Option "Device" "/dev/input/event12"
[    32.105] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2508
[    32.105] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1056
[    32.105] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    32.105] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    32.105] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    32.105] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    32.105] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    32.105] (**) ETPS/2 Elantech Touchpad: always reports core events
[    32.105] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input12/event12"
[    32.105] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[    32.106] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    32.106] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    32.106] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.074
[    32.106] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    32.106] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    32.106] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    32.106] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    32.106] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    32.106] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    32.106] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    32.107] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event6)
[    32.107] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    32.107] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    32.107] (**) Acer WMI hotkeys: always reports core events
[    32.107] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event6"
[    32.107] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    32.108] (--) evdev: Acer WMI hotkeys: Found keys
[    32.108] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    32.108] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    32.108] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 13)
[    32.108] (**) Option "xkb_rules" "evdev"
[    32.108] (**) Option "xkb_model" "pc105"
[    32.108] (**) Option "xkb_layout" "us"
[    32.108] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event7)
[    32.108] (II) No input driver specified, ignoring this device.
[    32.108] (II) This device may have been added with another device file.
[    32.108] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[    32.108] (II) No input driver specified, ignoring this device.
[    32.108] (II) This device may have been added with another device file.
[    36.797] (II) intel(0): EDID vendor "AUO", prod id 9964
[    36.797] (II) intel(0): Printing DDC gathered Modelines:
[    36.797] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    38.866] (II) intel(0): EDID vendor "AUO", prod id 9964
[    38.866] (II) intel(0): Printing DDC gathered Modelines:
[    38.866] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    49.743] (II) intel(0): EDID vendor "AUO", prod id 9964
[    49.743] (II) intel(0): Printing DDC gathered Modelines:
[    49.743] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    50.858] (II) intel(0): EDID vendor "AUO", prod id 9964
[    50.858] (II) intel(0): Printing DDC gathered Modelines:
[    50.858] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    51.256] (II) intel(0): EDID vendor "AUO", prod id 9964
[    51.256] (II) intel(0): Printing DDC gathered Modelines:
[    51.256] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    51.535] (II) intel(0): EDID vendor "AUO", prod id 9964
[    51.535] (II) intel(0): Printing DDC gathered Modelines:
[    51.535] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    54.055] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    71.902] (II) intel(0): EDID vendor "AUO", prod id 9964
[    71.903] (II) intel(0): Printing DDC gathered Modelines:
[    71.903] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   132.796] (II) PM Event received: Capability Changed
[   132.809] (II) intel(0): EDID vendor "AUO", prod id 9964
[   132.809] (II) intel(0): Printing DDC gathered Modelines:
[   132.809] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   132.929] (II) intel(0): EDID vendor "AUO", prod id 9964
[   132.929] (II) intel(0): Printing DDC gathered Modelines:
[   132.929] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   133.309] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[   135.428] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[   135.656] (II) AIGLX: Suspending AIGLX clients for VT switch
[   140.156] (II) Open ACPI successful (/var/run/acpid.socket)
[   140.156] (II) AIGLX: Resuming AIGLX clients after VT switch
[   140.156] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[   140.172] (II) intel(0): EDID vendor "AUO", prod id 9964
[   140.172] (II) intel(0): Printing DDC gathered Modelines:
[   140.172] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   140.260] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   140.262] (II) intel(0): EDID vendor "AUO", prod id 9964
[   140.262] (II) intel(0): Printing DDC gathered Modelines:
[   140.262] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   141.938] (II) intel(0): EDID vendor "AUO", prod id 9964
[   141.938] (II) intel(0): Printing DDC gathered Modelines:
[   141.938] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   350.618] (II) intel(0): EDID vendor "AUO", prod id 9964
[   350.619] (II) intel(0): Printing DDC gathered Modelines:
[   350.619] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)



FAILED log

[    29.357] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    29.357] X Protocol Version 11, Revision 0
[    29.357] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    29.357] Current Operating System: Linux j-NE56R 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64
[    29.357] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=f2b6583a-8aa1-46fc-aa0d-6cb0e0f02ea5 ro quiet splash vt.handoff=7
[    29.357] Build Date: 17 April 2013  10:43:13PM
[    29.357] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    29.357] Current version of pixman: 0.28.2
[    29.357]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    29.357] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.357] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 19 18:18:35 2013
[    29.393] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.393] (==) No Layout section.  Using the first Screen section.
[    29.393] (==) No screen section available. Using defaults.
[    29.393] (**) |-->Screen "Default Screen Section" (0)
[    29.393] (**) |   |-->Monitor "<default monitor>"
[    29.393] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.393] (==) Automatically adding devices
[    29.393] (==) Automatically enabling devices
[    29.393] (==) Automatically adding GPU devices
[    29.393] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.393]     Entry deleted from font path.
[    29.393] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.393]     Entry deleted from font path.
[    29.393] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.393]     Entry deleted from font path.
[    29.393] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.393]     Entry deleted from font path.
[    29.393] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.393]     Entry deleted from font path.
[    29.393] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    29.393]     Entry deleted from font path.
[    29.393] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.393] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.393] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.393] (II) Loader magic: 0x7f2a7fcf1d20
[    29.393] (II) Module ABI versions:
[    29.393]     X.Org ANSI C Emulation: 0.4
[    29.393]     X.Org Video Driver: 13.1
[    29.393]     X.Org XInput driver : 18.0
[    29.393]     X.Org Server Extension : 7.0
[    29.393] (II) config/udev: Adding drm device (/dev/dri/card0)
[    29.395] (--) PCI:*(0:0:2:0) 8086:0106:1025:0649 rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00002000/64
[    29.395] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.395] Initializing built-in extension Generic Event Extension
[    29.395] Initializing built-in extension SHAPE
[    29.395] Initializing built-in extension MIT-SHM
[    29.395] Initializing built-in extension XInputExtension
[    29.395] Initializing built-in extension XTEST
[    29.395] Initializing built-in extension BIG-REQUESTS
[    29.395] Initializing built-in extension SYNC
[    29.395] Initializing built-in extension XKEYBOARD
[    29.395] Initializing built-in extension XC-MISC
[    29.395] Initializing built-in extension SECURITY
[    29.395] Initializing built-in extension XINERAMA
[    29.395] Initializing built-in extension XFIXES
[    29.395] Initializing built-in extension RENDER
[    29.395] Initializing built-in extension RANDR
[    29.395] Initializing built-in extension COMPOSITE
[    29.395] Initializing built-in extension DAMAGE
[    29.395] Initializing built-in extension MIT-SCREEN-SAVER
[    29.395] Initializing built-in extension DOUBLE-BUFFER
[    29.395] Initializing built-in extension RECORD
[    29.395] Initializing built-in extension DPMS
[    29.395] Initializing built-in extension X-Resource
[    29.395] Initializing built-in extension XVideo
[    29.395] Initializing built-in extension XVideo-MotionCompensation
[    29.395] Initializing built-in extension SELinux
[    29.395] Initializing built-in extension XFree86-VidModeExtension
[    29.395] Initializing built-in extension XFree86-DGA
[    29.395] Initializing built-in extension XFree86-DRI
[    29.395] Initializing built-in extension DRI2
[    29.395] (II) LoadModule: "glx"
[    29.580] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.581] (II) Module glx: vendor="X.Org Foundation"
[    29.581]     compiled for 1.13.3, module version = 1.0.0
[    29.581]     ABI class: X.Org Server Extension, version 7.0
[    29.581] (==) AIGLX enabled
[    29.581] Loading extension GLX
[    29.581] (==) Matched intel as autoconfigured driver 0
[    29.581] (==) Matched intel as autoconfigured driver 1
[    29.581] (==) Matched vesa as autoconfigured driver 2
[    29.581] (==) Matched modesetting as autoconfigured driver 3
[    29.581] (==) Matched fbdev as autoconfigured driver 4
[    29.581] (==) Assigned the driver to the xf86ConfigLayout
[    29.581] (II) LoadModule: "intel"
[    29.581] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.619] (II) Module intel: vendor="X.Org Foundation"
[    29.619]     compiled for 1.13.3, module version = 2.21.6
[    29.619]     Module class: X.Org Video Driver
[    29.619]     ABI class: X.Org Video Driver, version 13.1
[    29.619] (II) LoadModule: "vesa"
[    29.619] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.619] (II) Module vesa: vendor="X.Org Foundation"
[    29.619]     compiled for 1.12.99.902, module version = 2.3.2
[    29.619]     Module class: X.Org Video Driver
[    29.619]     ABI class: X.Org Video Driver, version 13.0
[    29.619] (II) LoadModule: "modesetting"
[    29.619] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.619] (II) Module modesetting: vendor="X.Org Foundation"
[    29.619]     compiled for 1.13.3, module version = 0.7.0
[    29.619]     Module class: X.Org Video Driver
[    29.619]     ABI class: X.Org Video Driver, version 13.1
[    29.619] (II) LoadModule: "fbdev"
[    29.620] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.620] (II) Module fbdev: vendor="X.Org Foundation"
[    29.620]     compiled for 1.12.99.902, module version = 0.4.3
[    29.620]     Module class: X.Org Video Driver
[    29.620]     ABI class: X.Org Video Driver, version 13.0
[    29.620] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    29.620] (II) VESA: driver for VESA chipsets: vesa
[    29.620] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    29.620] (II) FBDEV: driver for framebuffer: fbdev
[    29.620] (++) using VT number 7

[    29.620] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.6-0ubuntu4 (Bryce Harrington <bryce@ubuntu.com>)
[    29.621] (WW) Falling back to old probe method for vesa
[    29.621] (WW) Falling back to old probe method for modesetting
[    29.621] (WW) Falling back to old probe method for fbdev
[    29.621] (II) Loading sub module "fbdevhw"
[    29.621] (II) LoadModule: "fbdevhw"
[    29.621] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.621] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.621]     compiled for 1.13.3, module version = 0.0.2
[    29.621]     ABI class: X.Org Video Driver, version 13.1
[    29.621] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    29.621] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    29.621] (==) intel(0): RGB weight 888
[    29.621] (==) intel(0): Default visual is TrueColor
[    29.621] (--) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT1)
[    29.621] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[    29.621] (**) intel(0): Framebuffer tiled
[    29.621] (**) intel(0): Pixmaps tiled
[    29.621] (**) intel(0): "Tear free" disabled
[    29.621] (**) intel(0): Forcing per-crtc-pixmaps? no
[    29.621] (II) intel(0): Output LVDS1 has no monitor section
[    29.720] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    29.737] (II) intel(0): Output VGA1 has no monitor section
[    29.738] (II) intel(0): EDID for output LVDS1
[    29.738] (II) intel(0): Manufacturer: AUO  Model: 26ec  Serial#: 0
[    29.738] (II) intel(0): Year: 2009  Week: 1
[    29.738] (II) intel(0): EDID Version: 1.3
[    29.738] (II) intel(0): Digital Display Input
[    29.738] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    29.738] (II) intel(0): Gamma: 2.20
[    29.738] (II) intel(0): No DPMS capabilities specified
[    29.738] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.738] (II) intel(0): First detailed timing is preferred mode
[    29.738] (II) intel(0): redX: 0.577 redY: 0.333   greenX: 0.333 greenY: 0.554
[    29.738] (II) intel(0): blueX: 0.161 blueY: 0.144   whiteX: 0.313 whiteY: 0.329
[    29.738] (II) intel(0): Manufacturer's mask: 0
[    29.738] (II) intel(0): Supported detailed timing:
[    29.738] (II) intel(0): clock: 71.8 MHz   Image Size:  344 x 193 mm
[    29.738] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    29.738] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 784 v_border: 0
[    29.738] (II) intel(0): Unknown vendor-specific block f
[    29.738] (II) intel(0):  AUO
[    29.738] (II) intel(0):  B156XW02 V6
[    29.738] (II) intel(0): EDID (in hex):
[    29.738] (II) intel(0):     00ffffffffffff0006afec2600000000
[    29.738] (II) intel(0):     01130103802213780ad7759355558d29
[    29.738] (II) intel(0):     24505400000001010101010101010101
[    29.738] (II) intel(0):     0101010101010c1c56a0500010303020
[    29.738] (II) intel(0):     360058c1100000180000000f00000000
[    29.738] (II) intel(0):     00000000000000000020000000fe0041
[    29.738] (II) intel(0):     554f0a202020202020202020000000fe
[    29.738] (II) intel(0):     004231353658573032205636200a0065
[    29.738] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    29.738] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    29.738] (II) intel(0): Printing probed modes for output LVDS1
[    29.738] (II) intel(0): Modeline "1366x768"x60.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    29.738] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    29.738] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    29.738] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    29.738] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    29.738] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    29.738] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    29.753] (II) intel(0): EDID for output VGA1
[    29.753] (II) intel(0): Output LVDS1 connected
[    29.753] (II) intel(0): Output VGA1 disconnected
[    29.753] (II) intel(0): Using exact sizes for initial modes
[    29.753] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    29.753] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.753] (==) intel(0): DPI set to (96, 96)
[    29.753] (II) Loading sub module "dri2"
[    29.753] (II) LoadModule: "dri2"
[    29.753] (II) Module "dri2" already built-in
[    29.753] (II) UnloadModule: "vesa"
[    29.753] (II) Unloading vesa
[    29.753] (II) UnloadModule: "modesetting"
[    29.753] (II) Unloading modesetting
[    29.753] (II) UnloadModule: "fbdev"
[    29.753] (II) Unloading fbdev
[    29.753] (II) UnloadSubModule: "fbdevhw"
[    29.753] (II) Unloading fbdevhw
[    29.753] (==) Depth 24 pixmap format is 32 bpp
[    29.753] (II) intel(0): SNA initialized with SandyBridge backend
[    29.753] (==) intel(0): Backing store disabled
[    29.753] (==) intel(0): Silken mouse enabled
[    29.754] (II) intel(0): HW Cursor enabled
[    29.754] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.755] (==) intel(0): DPMS enabled
[    29.755] (II) intel(0): [DRI2] Setup complete
[    29.755] (II) intel(0): [DRI2]   DRI driver: i965
[    29.755] (II) intel(0): direct rendering: DRI2 Enabled
[    29.755] (==) intel(0): hotplug detection: "enabled"
[    29.755] (--) RandR disabled
[    29.761] (II) SELinux: Disabled on system
[    30.155] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    30.155] (II) AIGLX: enabled GLX_INTEL_swap_event
[    30.155] (II) AIGLX: enabled GLX_ARB_create_context
[    30.155] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    30.155] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    30.155] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    30.155] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    30.155] (II) AIGLX: Loaded and initialized i965
[    30.155] (II) GLX: Initialized DRI2 GL provider for screen 0
[    30.156] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[    30.168] (II) intel(0): Setting screen physical size to 361 x 203
[    30.175] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.177] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    30.177] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.177] (II) LoadModule: "evdev"
[    30.177] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.215] (II) Module evdev: vendor="X.Org Foundation"
[    30.215]     compiled for 1.13.3, module version = 2.7.3
[    30.215]     Module class: X.Org XInput Driver
[    30.215]     ABI class: X.Org XInput driver, version 18.0
[    30.215] (II) Using input driver 'evdev' for 'Power Button'
[    30.215] (**) Power Button: always reports core events
[    30.215] (**) evdev: Power Button: Device: "/dev/input/event3"
[    30.216] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.216] (--) evdev: Power Button: Found keys
[    30.216] (II) evdev: Power Button: Configuring as keyboard
[    30.216] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    30.216] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.216] (**) Option "xkb_rules" "evdev"
[    30.216] (**) Option "xkb_model" "pc105"
[    30.216] (**) Option "xkb_layout" "us"
[    30.216] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    30.216] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.216] (II) Using input driver 'evdev' for 'Video Bus'
[    30.216] (**) Video Bus: always reports core events
[    30.216] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    30.216] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    30.216] (--) evdev: Video Bus: Found keys
[    30.216] (II) evdev: Video Bus: Configuring as keyboard
[    30.216] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    30.216] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    30.216] (**) Option "xkb_rules" "evdev"
[    30.216] (**) Option "xkb_model" "pc105"
[    30.216] (**) Option "xkb_layout" "us"
[    30.217] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.217] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.217] (II) Using input driver 'evdev' for 'Power Button'
[    30.217] (**) Power Button: always reports core events
[    30.217] (**) evdev: Power Button: Device: "/dev/input/event0"
[    30.217] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.217] (--) evdev: Power Button: Found keys
[    30.217] (II) evdev: Power Button: Configuring as keyboard
[    30.217] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    30.217] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    30.217] (**) Option "xkb_rules" "evdev"
[    30.217] (**) Option "xkb_model" "pc105"
[    30.217] (**) Option "xkb_layout" "us"
[    30.217] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    30.217] (II) No input driver specified, ignoring this device.
[    30.217] (II) This device may have been added with another device file.
[    30.217] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    30.217] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    30.217] (II) Using input driver 'evdev' for 'Sleep Button'
[    30.217] (**) Sleep Button: always reports core events
[    30.217] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    30.217] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    30.217] (--) evdev: Sleep Button: Found keys
[    30.217] (II) evdev: Sleep Button: Configuring as keyboard
[    30.217] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input2/event2"
[    30.217] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    30.217] (**) Option "xkb_rules" "evdev"
[    30.217] (**) Option "xkb_model" "pc105"
[    30.217] (**) Option "xkb_layout" "us"
[    30.218] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    30.218] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    30.218] (II) config/udev: Adding input device HD WebCam (/dev/input/event12)
[    30.218] (**) HD WebCam: Applying InputClass "evdev keyboard catchall"
[    30.218] (II) Using input driver 'evdev' for 'HD WebCam'
[    30.218] (**) HD WebCam: always reports core events
[    30.218] (**) evdev: HD WebCam: Device: "/dev/input/event12"
[    30.218] (--) evdev: HD WebCam: Vendor 0x4f2 Product 0xb374
[    30.218] (--) evdev: HD WebCam: Found keys
[    30.218] (II) evdev: HD WebCam: Configuring as keyboard
[    30.218] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input12/event12"
[    30.218] (II) XINPUT: Adding extended input device "HD WebCam" (type: KEYBOARD, id 10)
[    30.218] (**) Option "xkb_rules" "evdev"
[    30.218] (**) Option "xkb_model" "pc105"
[    30.218] (**) Option "xkb_layout" "us"
[    30.218] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    30.218] (II) No input driver specified, ignoring this device.
[    30.219] (II) This device may have been added with another device file.
[    30.219] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    30.219] (II) No input driver specified, ignoring this device.
[    30.219] (II) This device may have been added with another device file.
[    30.219] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    30.219] (II) No input driver specified, ignoring this device.
[    30.219] (II) This device may have been added with another device file.
[    30.219] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    30.219] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.219] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    30.219] (**) AT Translated Set 2 keyboard: always reports core events
[    30.219] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    30.219] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    30.219] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    30.219] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    30.219] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    30.219] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    30.219] (**) Option "xkb_rules" "evdev"
[    30.219] (**) Option "xkb_model" "pc105"
[    30.219] (**) Option "xkb_layout" "us"
[    30.220] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event8)
[    30.220] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    30.220] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    30.220] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    30.220] (II) LoadModule: "synaptics"
[    30.220] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.220] (II) Module synaptics: vendor="X.Org Foundation"
[    30.220]     compiled for 1.13.1.901, module version = 1.6.2
[    30.220]     Module class: X.Org XInput Driver
[    30.220]     ABI class: X.Org XInput driver, version 18.0
[    30.220] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    30.220] (**) ETPS/2 Elantech Touchpad: always reports core events
[    30.220] (**) Option "Device" "/dev/input/event8"
[    30.232] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2508
[    30.232] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1056
[    30.232] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    30.232] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    30.232] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    30.232] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    30.232] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    30.232] (**) ETPS/2 Elantech Touchpad: always reports core events
[    30.232] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    30.232] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[    30.232] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    30.232] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    30.232] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.074
[    30.232] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    30.232] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    30.232] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    30.232] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    30.232] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    30.232] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    30.232] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    30.234] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event6)
[    30.234] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    30.234] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    30.234] (**) Acer WMI hotkeys: always reports core events
[    30.234] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event6"
[    30.234] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    30.234] (--) evdev: Acer WMI hotkeys: Found keys
[    30.234] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    30.234] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    30.234] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 13)
[    30.234] (**) Option "xkb_rules" "evdev"
[    30.234] (**) Option "xkb_model" "pc105"
[    30.234] (**) Option "xkb_layout" "us"
[    30.234] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event7)
[    30.234] (II) No input driver specified, ignoring this device.
[    30.234] (II) This device may have been added with another device file.
[    30.234] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[    30.234] (II) No input driver specified, ignoring this device.
[    30.234] (II) This device may have been added with another device file.
[    30.237] (WW) config/udev: device HD WebCam already added. Ignoring.
[    34.798] (II) intel(0): EDID vendor "AUO", prod id 9964
[    34.798] (II) intel(0): Printing DDC gathered Modelines:
[    34.798] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    37.093] (II) intel(0): EDID vendor "AUO", prod id 9964
[    37.093] (II) intel(0): Printing DDC gathered Modelines:
[    37.093] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    48.777] (II) intel(0): EDID vendor "AUO", prod id 9964
[    48.777] (II) intel(0): Printing DDC gathered Modelines:
[    48.777] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    49.294] (II) intel(0): EDID vendor "AUO", prod id 9964
[    49.294] (II) intel(0): Printing DDC gathered Modelines:
[    49.294] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    49.935] (II) intel(0): EDID vendor "AUO", prod id 9964
[    49.935] (II) intel(0): Printing DDC gathered Modelines:
[    49.935] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    51.031] (II) intel(0): EDID vendor "AUO", prod id 9964
[    51.031] (II) intel(0): Printing DDC gathered Modelines:
[    51.031] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    53.177] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    69.849] (II) intel(0): EDID vendor "AUO", prod id 9964
[    69.849] (II) intel(0): Printing DDC gathered Modelines:
[    69.849] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[    70.837] (II) intel(0): EDID vendor "AUO", prod id 9964
[    70.837] (II) intel(0): Printing DDC gathered Modelines:
[    70.837] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[   168.800] (II) intel(0): EDID vendor "AUO", prod id 9964
[   168.800] (II) intel(0): Printing DDC gathered Modelines:
[   168.800] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  1472.273] (II) PM Event received: Capability Changed
[  1472.283] (II) intel(0): EDID vendor "AUO", prod id 9964
[  1472.283] (II) intel(0): Printing DDC gathered Modelines:
[  1472.283] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  1472.382] (II) intel(0): EDID vendor "AUO", prod id 9964
[  1472.382] (II) intel(0): Printing DDC gathered Modelines:
[  1472.382] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  1472.684] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[  1473.308] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[  1474.808] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1479.188] (II) Open ACPI successful (/var/run/acpid.socket)
[  1479.188] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1479.189] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[  1479.196] (II) intel(0): EDID vendor "AUO", prod id 9964
[  1479.196] (II) intel(0): Printing DDC gathered Modelines:
[  1479.196] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  1479.213] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  1479.213] (II) intel(0): EDID vendor "AUO", prod id 9964
[  1479.214] (II) intel(0): Printing DDC gathered Modelines:
[  1479.214] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  1480.956] (II) intel(0): EDID vendor "AUO", prod id 9964
[  1480.956] (II) intel(0): Printing DDC gathered Modelines:
[  1480.956] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  1973.997] (II) intel(0): EDID vendor "AUO", prod id 9964
[  1973.997] (II) intel(0): Printing DDC gathered Modelines:
[  1973.997] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  4718.801] (II) intel(0): EDID vendor "AUO", prod id 9964
[  4718.801] (II) intel(0): Printing DDC gathered Modelines:
[  4718.801] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  6181.735] (II) intel(0): EDID vendor "AUO", prod id 9964
[  6181.735] (II) intel(0): Printing DDC gathered Modelines:
[  6181.735] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  6319.152] (II) intel(0): EDID vendor "AUO", prod id 9964
[  6319.152] (II) intel(0): Printing DDC gathered Modelines:
[  6319.152] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  6326.470] (II) intel(0): EDID vendor "AUO", prod id 9964
[  6326.470] (II) intel(0): Printing DDC gathered Modelines:
[  6326.470] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  6333.613] (II) intel(0): EDID vendor "AUO", prod id 9964
[  6333.613] (II) intel(0): Printing DDC gathered Modelines:
[  6333.613] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  6335.258] (II) intel(0): EDID vendor "AUO", prod id 9964
[  6335.258] (II) intel(0): Printing DDC gathered Modelines:
[  6335.258] (II) intel(0): Modeline "1366x768"x0.0   71.80  1366 1414 1446 1526  768 771 777 784 -hsync -vsync (47.1 kHz eP)
[  6454.668] (II) evdev: Acer WMI hotkeys: Close
[  6454.668] (II) UnloadModule: "evdev"
[  6454.668] (II) UnloadModule: "synaptics"
[  6454.668] (II) evdev: AT Translated Set 2 keyboard: Close
[  6454.668] (II) UnloadModule: "evdev"
[  6454.668] (II) evdev: HD WebCam: Close
[  6454.668] (II) UnloadModule: "evdev"
[  6454.668] (II) evdev: Sleep Button: Close
[  6454.668] (II) UnloadModule: "evdev"
[  6454.668] (II) evdev: Power Button: Close
[  6454.668] (II) UnloadModule: "evdev"
[  6454.668] (II) evdev: Video Bus: Close
[  6454.669] (II) UnloadModule: "evdev"
[  6454.669] (II) evdev: Power Button: Close
[  6454.669] (II) UnloadModule: "evdev"
[  6454.687] Server terminated successfully (0). Closing log file.
```

---

### Post by gbooty on 2013-07-19
My lshw output looks the same too, just the xorg.log changed... looking at the log though, I don't know why now it's reading the HDMI output, each log looks almost identical. Anyway if another person has this problem, just be patient and keep rebooting.

---

### Post by wildmanne39 on 2013-07-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

