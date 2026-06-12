---
title: "A problem with NVidia driver after updating KUbuntu 14.04"
date: 2017-07-18
forum: Hardware
---

### Post by dmitriano on 2017-07-18
Hello!
After I updated my KUbuntu 14.04.5 LTS with 'aptitude safe-upgrade' and restarted my machine I did not see the graphical login screen. Console login screen appeared for a shot time period and then the screen became completely black.
I am not expert in Ubuntu, so I googled a bit and did all the steps of the instruction on how to [repair the machine after installing some restricted NVidia drivers]("https://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver"). Fortunately it helped, and now I am able to log in and looks like all the UI functionality works, but at the same time UI is significantly slowed down, and I have an impression that some kind of hardware acceleration is switched off. If I run an application that renders real-time data with OpenGL, all the applications start to work very slow. Also I noticed that there is a process 'compiz' that consumes 5 - 50% CPU depending on how many UI applications are started.

my system information:
lspci | grep VGA:
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 745] (rev a2)

lshw -c video  
*-display UNCLAIMED     
       description: VGA compatible controller
       product: GM107 [GeForce GTX 745]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff

xdpyinfo | grep dimensions
  dimensions:    2560x1440 pixels (677x381 millimeters)

CPU: Intel(R) Core(TM) i5-4460  CPU @ 3.20GHz

---

### Post by Autodave on 2017-07-18
First off, I have never had any luck doing an upgrade from one version to another. 13 machines, one worked, 12 did not.

That said, what Nvidia driver are you using and where did you get it from?  What are the specs of your machine?

---

### Post by deadflowr on 2017-07-18
> **Autodave said:**
> First off, I have never had any luck doing an upgrade from one version to another. 13 machines, one worked, 12 did not.

Seems like this was a same system update, not a release upgrade.

But my question is why is compiz outputting anything if your using Kubuntu?
There shouldn't be any compiz running.
That's just my own curiosity though.

Did you remove the xorg.conf file, if it ever existed?
Sometimes if those linger after removing drivers it can cause issues.
To remove simple run
```
sudo rm /etc/X11/xorg.conf
```
it the file exists it will be removed. If it did not exist, then no harm no foul.

---

### Post by dmitriano on 2017-07-19
Hello! There is no file /etc/X11/xorg.conf on my machine, and I did not remove it manually before. I do no[s]w[/s]t know exactly what the previous user of my machine did and what he installed, so I do no[s]w[/s]t know where 'compiz' goes from. My colleagues do not have 'compiz' running on their KUbuntu machnes, so probably I can uninstall it?

---

### Post by dmitriano on 2017-07-19
Hello! I am not sure how go get the exact information on Nvidia driver, but at least the command 'dpkg -l nvidia*' shows the following:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version             Architecture        Description
+++-=============================-===================-===================-================================================================
ii  nvidia-common                 1:0.2.91.12         amd64               transitional package for ubuntu-drivers-common
un  nvidia-libopencl1-dev         <none>              <none>              (no description available)
un  nvidia-prime                  <none>              <none>              (no description available)
un  nvidia-vdpau-driver           <none>              <none>              (no description available)
```

I do not know what are the machine specs, but 'lshw' shows the following:
```
asus                      
    description: Desktop Computer
    product: Vostro 3900 (Vostro 3900)
    vendor: Dell Inc.
    serial: D5ZXQ52
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=Vostro 3900 uuid=44454C4C-3500-105A-8058-C4C04F513532
  *-core
       description: Motherboard
       product: 0T1D10
       vendor: Dell Inc.
       physical id: 0
       version: A01
       serial: .D5ZXQ52.CN7016358C04O0.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 1
          version: A09
          date: 05/08/2015
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache
          description: L1 cache
          physical id: b
          slot: CPU Internal L1
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-back
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-4460  CPU @ 3.20GHz
          vendor: Intel Corp.
          physical id: d
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-4460 CPU @ 3.20GHz
          slot: CPU 1
          size: 3201MHz
          capacity: 3201MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L2 cache
             physical id: e
             slot: CPU Internal L2
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
        *-cache:1
             description: L3 cache
             physical id: f
             slot: CPU Internal L3
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: M378B5173EB0-YK0
             vendor: Samsung
             physical id: 0
             serial: 19793111
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: CT51264BA160B.C16F
             vendor: Conexant (Rockwell)
             physical id: 1
             serial: 23171358
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=301989888)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GM107 [GeForce GTX 745]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
           *-multimedia
                description: Audio device
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:29 memory:f7200000-f720ffff
        *-communication
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:32 memory:f721a000-f721a00f
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7218000-f72183ff
        *-multimedia
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:33 memory:f7210000-f7213fff
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:f2200000-f23fffff ioport:f2400000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:d000(size=4096) memory:f7100000-f71fffff ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 0c
                serial: 64:00:6a:16:ec:b6
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.19.144 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:31 ioport:d000(size=256) memory:f7100000-f7100fff memory:f2100000-f2103fff
        *-pci:3
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28
           *-pci
                description: PCI bridge
                product: IT8893E PCIe to PCI Bridge
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 41
                width: 64 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
                resources: iomemory:222001f10-222001f0f
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7217000-f72173ff
        *-isa
             description: ISA bridge
             product: C220 Series Chipset Family H81 Express LPC Controller
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
             product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7216000-f72167ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7215000-f72150ff ioport:f000(size=32)
     *-scsi:0
          physical id: 0
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000DM003-1ER1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CC45
             serial: W4Y4J265
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=000e77aa
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: eb102b53-579c-40c1-9cf0-f3db735993dc
                size: 923GiB
                capacity: 923GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-12-26 00:47:11 filesystem=ext4 lastmountpoint=/ modified=2017-07-18 18:48:50 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-07-18 18:48:50 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 8063MiB
                capacity: 8063MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8063MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW SH-216DB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: F100
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@3:9
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@5:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@5:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             product: M.S./M.S.Pro/HG
             vendor: Generic-
             physical id: 0.0.3
             bus info: scsi@5:0.0.3
             logical name: /dev/sde
             version: 1.00
             serial: 3
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sde
```

---

### Post by efflandt on 2017-07-19
For anything long, to maintain formatting, or sometimes easier to read certain characters (like double dash), you should highlight and use the "#" icon in top of message composing screen or wrap with code tags (brackets [] around **code** at beginning and **/code** at end). I am just not sure how to show code tags without them actually being code tags.

From what you presented I cannot tell if you have any nvidia package installed. What displays for the section about your graphics in the following, particularly modules near the end of that section.```
sudo lspci -v
```The link you included reference the x-swat ppa, not sure if that is still active, but the official ppa for lastest nvidia drivers is graphics-drivers ppa. Even without any ppa nvidia-331 worked for my GTX 750 Ti in 14.04 (nvidia-current a 304 version did not) and I believe the 750's were newer than any of the other 7xx cards (750's along with 9xx series were first to use new efficient Maxwell chip).

See if **Additional Drivers** shows which nvidia driver packages are available or if you have any active.

I usually use the following to tell which nvidia drivers are installed:```
dpkg-query -l nvidia* | grep ii
```

---

### Post by dmitriano on 2017-07-20
Hello! Probably it is something specific to the default desktop. When I switch to KDE Plasma desktop (without compiz) the UI works fast enough. The only thing I can say for sure, is that if I install Nvidia 340 driver I get the black screen after reboot, but [the link I provided above]("https://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver") makes my machine work. So, as far as I see, some third-party driver works on my machine, but native Nvidia driver does not.

dpkg-query -l nvidia* | grep ii
ii  nvidia-common                                         1:0.2.91.12                                amd64        transitional package for ubuntu-drivers-common


sudo lspci -v
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
    Subsystem: Dell Device 061c
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: hsw_uncore

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core  Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal  decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
    Capabilities: [88] Subsystem: Dell Device 061c
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])
    Subsystem: Dell Device 061c
    Flags: bus master, medium devsel, latency 0, IRQ 29
    Memory at f7200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Dell Device 061c
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f721a000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me

00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Device 061c
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7218000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
    Subsystem: Dell Device 061c
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at f7210000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset  Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f2200000-f23fffff
    Prefetchable memory behind bridge: 00000000f2400000-00000000f25fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device 061c
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset  Family PCI Express Root Port #4 (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7100000-f71fffff
    Prefetchable memory behind bridge: 00000000f2100000-00000000f21fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device 061c
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset  Family PCI Express Root Port #6 (rev d5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Dell Device 061c
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Dell Device 061c
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7217000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
    Subsystem: Dell Device 061c
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset  Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI  1.0])
    Subsystem: Dell Device 061c
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 30
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f020 [size=32]
    Memory at f7216000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Dell Device 061c
    Flags: medium devsel, IRQ 11
    Memory at f7215000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]

01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 745] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device 1065
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [250] Latency Tolerance Reporting
    Capabilities: [258] L1 PM Substates
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19

01:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)
    Subsystem: NVIDIA Corporation Device 1065
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
    Subsystem: Dell Device 061c
    Flags: bus master, fast devsel, latency 0, IRQ 31
    I/O ports at d000 [size=256]
    Memory at f7100000 (64-bit, non-prefetchable) [size=4K]
    Memory at f2100000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Capabilities: [170] Latency Tolerance Reporting
    Kernel driver in use: r8169

04:00.0 PCI bridge: Integrated Technology Express, Inc. IT8893E PCIe to PCI Bridge (rev 41) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=04, secondary=05, subordinate=05, sec-latency=32
    Capabilities: [90] Power Management version 2
    Capabilities: [a0] Subsystem: Dell Device 061c

```

---

### Post by vasa1 on 2017-07-20
> **dmitriano said:**
> Hello! There is no file /etc/X11/xorg.conf on my machine, and I did not remove it manually before. **I do now know** exactly what the previous user of my machine did and what he installed, so I do now know where 'compiz' goes from. My colleagues do not have 'compiz' running on their KUbuntu machnes, so probably I can uninstall it?

Do you mean "I do no_t_ know" instead of "I do no_w_ know"?

Can you please post the output of the following commands?
```
lsb_release -a
cat /etc/*-release
cat /var/log/installer/media-info
```
Also, install *inxi* and then post the output of *inxi -F*.

In any case, you clearly have more than one desktop environment installed. Why you see any compiz-related process when running the KDE environment is unclear.

---

### Post by dmitriano on 2017-07-20
Yes, I meant 'not', just mistyped.
lsb_release -a
```

LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

```

cat /etc/*-release
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
NAME="Ubuntu"
VERSION="14.04.5 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.5 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

```

cat /var/log/installer/media-info
```

Ubuntu 14.04.3 LTS "Trusty Tahr" - Beta amd64 (20150805)

```

inxi -F
```

System:    Host: Asus Kernel: 3.19.0-80-generic x86_64 (64 bit) Desktop: N/A Distro: Ubuntu 14.04 trusty
Machine:   System: Dell product: Vostro 3900 serial: D5ZXQ52 
           Mobo: Dell model: 0T1D10 version: A01 serial: .D5ZXQ52.CN7016358C04O0. Bios: Dell version: A09 date: 05/08/2015
CPU:       Quad core Intel Core i5-4460 CPU (-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) 
           Clock Speeds: 1: 3185.625 MHz 2: 3200.00 MHz 3: 3270.750 MHz 4: 3224.00 MHz
Graphics:  Card: NVIDIA GM107 [GeForce GTX 745] 
           X.org: 1.15.1 drivers: fbdev (unloaded: vesa) FAILED: nouveau tty size: 141x56 Advanced Data: N/A for root 
Audio:     Card-1: Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel 
           Card-2: NVIDIA Device 0fbc driver: snd_hda_intel 
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-80-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
           IF: eth1 state: up speed: 1000 Mbps duplex: full mac: 64:00:6a:16:ec:b6
Drives:    HDD Total Size: 1000.2GB (22.1% used) 1: id: /dev/sda model: ST1000DM003 size: 1000.2GB 
Partition: ID: / size: 910G used: 206G (24%) fs: ext4 ID: swap-1 size: 8.45GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 39.0C mobo: 39.0C 
           Fan Speeds (in rpm): cpu: 25050 mobo: 15060 
Info:      Processes: 208 Uptime: 2:36 Memory: 2049.6/7935.7MB Client: Shell (bash) inxi: 1.9.17 

```

Yesterday I had a less experience in Lunix than today, so looks like I mixed my desktop environments. 'compiz' runs and slows down my machine with ubuntu-desktop (Unity as far as I see). KDE plasma works fast enough, GNOME works slower, but with it my machine is still usable in opposite to Unity that make the machine unusable. The other question is that if I install Nvidia 340 driver I get the black screen after reboot, but [the link I provided above]("https://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver") makes the machine UI work. So, as far as I see, some third-party driver works on my machine, but native Nvidia driver does not.

'inxi -F' command reports that something is wrong with graphics: 
Graphics:  Card: NVIDIA GM107 [GeForce GTX 745] X.org: 1.15.1 drivers: [COLOR=#b22222]**fbdev (unloaded: vesa) FAILED:**[/COLOR] nouveau tty size: 141x56 Advanced Data: N/A for root

---

### Post by vasa1 on 2017-07-20
When you're in a KDE environment, could you post the output of *ps axjf*?

And I hope someone who knows better can explain```
Graphics:  Card: NVIDIA GM107 [GeForce GTX 745] 
           X.org: 1.15.1 drivers: fbdev (unloaded: vesa) FAILED: nouveau tty size: 141x56 Advanced Data: N/A for root 
```

---

### Post by dmitriano on 2017-07-20
the output of 'ps axjf':
KDE Plasma: [https://slogpost.ru/wp-content/uploads/2017/05/ps-kde.txt](https://slogpost.ru/wp-content/uploads/2017/05/ps-kde.txt)
GNOME: [https://slogpost.ru/wp-content/uploads/2017/05/ps-gnome.txt](https://slogpost.ru/wp-content/uploads/2017/05/ps-gnome.txt)

---

### Post by #&amp;thj^% on 2017-07-20
This with multiple DE's installed is a mess. Looks to me you have KDE Unity and Gnome installed, is this correct?
Also see what is listed here with:
```
cd /etc/X11
ls
```
run one line at a time, and paste back if you would.

---

### Post by dmitriano on 2017-07-20
Yes, correct, 
$ls /usr/share/xsessions/
gnome-classic.desktop  gnome.desktop  kde-plasma.desktop  ubuntu.desktop

$ls /etc/X11
app-defaults  default-display-manager  rgb.txt    xinit  xorg.conf.failsafe  Xreset.d    Xsession    Xsession.options  Xwrapper.config
cursors       fonts               X    xkb    Xreset           Xresources  Xsession.d  xsm

---

### Post by #&amp;thj^% on 2017-07-20
Ok Thanks please run this to see if this can be salvaged:
```
sudo apt-get remove --purge nvidia*
```
And to help not to confuse the Driver:
```
sudo rm -rf /etc/X11/xorg.conf.failsafe
```
Now see if things are any better with a complete power down waiting 30 to 40 seconds to power back up instead of a reboot.

---

### Post by dmitriano on 2017-07-20
I an not an expert in Linux, please clarify what effect this should take when I boot?

---

### Post by #&amp;thj^% on 2017-07-20
It will bring you back to a near stock Driver using the nouveau opensource for the time being.
Then we will see if we can get the Nvidia driver installed and loaded properly.

---

### Post by #&amp;thj^% on 2017-07-20
I have an appointment so I will be offline for a couple of hours.
I will check back to see how you are getting on,

---

### Post by dmitriano on 2017-07-20
Thank you very much for your help, I'll try this on the next week because, I am a bit scared with this driver installations and I need to finish some urgent job on this machine (that at least works somehow with this wrong driver). After that I'll post the results here.

---

### Post by dmitriano on 2017-07-26
I did 

```

sudo apt-get remove --purge nvidia*
sudo rm -rf /etc/X11/xorg.conf.failsafe
```
after power down/up I have the following packages:
$ dpkg -l nvidia
dpkg-query: no packages found matching nvidia
dmitry@Asus:~$ dpkg -l nvidia*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-=================================================================
un  nvidia-common                  <none>               <none>               (no description available)
un  nvidia-libopencl1-dev          <none>               <none>               (no description available)
un  nvidia-prime                   <none>               <none>               (no description available)
un  nvidia-vdpau-driver            <none>               <none>               (no description available)

---

### Post by #&amp;thj^% on 2017-07-26
> **dmitriano said:**
> I did 

```

sudo apt-get remove --purge nvidia*
sudo rm -rf /etc/X11/xorg.conf.failsafe
```
after power down/up I have the following packages:
$ dpkg -l nvidia
dpkg-query: no packages found matching nvidia
dmitry@Asus:~$ dpkg -l nvidia*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-=================================================================
un  nvidia-common                  <none>               <none>               (no description available)
un  nvidia-libopencl1-dev          <none>               <none>               (no description available)
un  nvidia-prime                   <none>               <none>               (no description available)
un  nvidia-vdpau-driver            <none>               <none>               (no description available)
Any improvement seen?

---

### Post by dmitriano on 2017-07-27
I did not notice any performance improvements. The machine is slowed down, but GNOME desktop is still usable. KDE Plasma works faster, but I cannot work with it, because I do not know how to configure Copy/Paste with Ctrl+Ins/Shift+Ins with it. When I log in to a desktop environment a message reporting a system problem appears with 'Send Report...' button. 

'inxi -F' shows the same info as before:

```

inxi -F

```

Graphics:  Card: NVIDIA GM107 [GeForce GTX 745] 
           X.Org: 1.15.1 drivers: fbdev (unloaded: vesa) FAILED: nouveau Resolution: 2560x1440@93.0hz

---

### Post by #&amp;thj^% on 2017-07-27
The thing with multiple DE environments is they may work hand in hand nicely, for a short while until upgrades can/will break things.
I find it best to use different partitions to play with or use different  DE environments.
There is something wrong on your system as you have noticed, but this could be very time consuming to track down.
Our time difference's are kind of a burden for me. I like to have people respond a lot faster && I have a lot of personal issues going on at the moment that command my time all most daily.
This is not your problem and I'm, not trying to sound cruft here, but it is what it is.
You can now try if you wish to run this:
```
sudo apt-get install nouveau-firmware
```
Which is the default driver used when installed. And it will probably show as already installed.
The next you could also try is to see if you can reset X via:
```
sudo X -configure
```
I think installing the Nvidia Drivers now at this point is useless.
But really to have a nice working system back I highly recommend/suggest another install with one DE only.

---

### Post by dmitriano on 2017-07-28
Thank you very much!
Today I found out [how configure my keyboard shortcuts in KDE]("https://developernote.com/2017/07/how-to-make-shift-numpad-keys-select-text-in-kde-like-as-in-ms-windows/"), and KDE is the only desktop environment that works fast enough on my machine. So I can work with QT Creator in KDE without reinstalling the system.

---

