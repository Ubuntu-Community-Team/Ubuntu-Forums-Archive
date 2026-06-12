---
title: "Limited resolution with Sandybridge with 14.04 LTS"
date: 2015-07-16
forum: Hardware
---

### Post by tom195 on 2015-07-16
I just installed 14.04 and have a limited number of options for resolution in my display settings. I did some research and the best I found others with similar problems, but with older versions of Ubuntu. I tried the solutions that worked for them, but nothing worked. The most promising sounding solution was to go to the Linux Intel graphics driver download at 01.org/linuxgraphics, but this website is not loading. Any help to get my resolution up to where it should be would be much appreciated. Its the only problem I've had with the switch to Ubuntu

---

### Post by weatherman2 on 2015-07-16
Can you be a little more specific?  What resolution do you seek?  What resolutions are available?  What kind of monitor have you plugged in?  (Make/model of monitor and its native resolution?)

What kind of computer?

Please open a terminal and type these commands, then paste the output into a reply here (but please use code tags):

```

lspci
sudo lshw

```

---

### Post by tom195 on 2015-07-16
Sorry, I am new to this asking for help thing, i usually am able to figure stuff otu on my own with hunting around the internet.

```
tom@Evermind:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
```

and

```
tom@Evermind:~$ sudo lshw
[sudo] password for tom: 
evermind                  
    description: Desktop Computer
    product: ()
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop uuid=9E46DD96-A438-11E1-A005-001217576F5B
  *-core
       description: Motherboard
       product: DH67BL
       vendor: Intel Corporation
       physical id: 0
       version: AAG10189-211
       serial: BTBL22100H6T
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: BLH6710H.86A.0146.2011.1222.1415
          date: 12/22/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          description: L1 cache
          physical id: 4
          size: 128KiB
          capacity: 128KiB
          capabilities: internal varies
     *-cache:1
          description: L2 cache
          physical id: 5
          size: 512KiB
          capacity: 512KiB
          capabilities: internal varies unified
     *-cache:2
          description: L3 cache
          physical id: 6
          size: 3MiB
          capacity: 3MiB
          capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: DIMM3
             width: 64 bits
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-4GBNT
             vendor: Undefined
             physical id: 1
             serial: 00000000
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber2
             vendor: A1_Manufacturer2
             physical id: 2
             serial: A1_SerNum2
             slot: DIMM4
             width: 64 bits
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-4GBNT
             vendor: Undefined
             physical id: 3
             serial: 00000000
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-2120 CPU @ 3.30GHz
          vendor: Intel Corp.
          physical id: 3c
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-2120 CPU @ 3.30GHz
          slot: SOCKET 0
          size: 2020MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer xsave avx lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
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
        *-display
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
             resources: irq:50 memory:fe000000-fe3fffff memory:e0000000-efffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:49 memory:fe529000-fe52900f
        *-network
             description: Ethernet interface
             product: 82579V Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 05
             serial: 00:1e:8c:f2:71:80
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:48 memory:fe500000-fe51ffff memory:fe528000-fe528fff ioport:f080(size=32)
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:fe527000-fe5273ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:51 memory:fe520000-fe523fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40
           *-pci
                description: PCI bridge
                product: Integrated Technology Express, Inc.
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:fe400000-fe4fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:fe400000-fe401fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fe526000-fe5263ff
        *-isa
             description: ISA bridge
             product: H67 Express Chipset Family LPC Controller
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
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:47 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f060(size=32) memory:fe525000-fe5257ff
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
             resources: memory:fe524000-fe5240ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1002FAEX-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1D05
             serial: WD-WCATRA264307
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000aff9a
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 41b7b3ca-0d8f-4a06-83f4-1fc4d1f5d967
                size: 923GiB
                capacity: 923GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-07-16 18:17:03 filesystem=ext4 lastmountpoint=/ modified=2015-07-16 19:23:38 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-07-16 19:23:38 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 8090MiB
                capacity: 8090MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8090MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH24NS90
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: IN01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@4:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: My Book 1130
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 1008
             serial: WCAV5L433535
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=6 sectorsize=512 signature=6cad7497
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/tom/Orb
                version: 3.1
                serial: 1af183cc-94d1-cd49-93ca-39ac593dd047
                size: 931GiB
                capacity: 931GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-10-02 20:40:48 filesystem=ntfs label=Orb mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-enclosure UNCLAIMED
             description: SCSI Enclosure
             product: SES Device
             vendor: WD
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             version: 1008
             serial: WCAV5L433535
             configuration: ansiversion=6
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:2
       logical name: wlan0
       serial: 14:d6:4d:16:4b:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.1.253 multicast=yes wireless=IEEE 802.11bgn
```

Thanks

---

### Post by tom195 on 2015-07-16
The only resolutions available are 1024x768 and 800x600.
I'm not sure what res I am going for but I am certain there is a higher one possible.
My monitor is  MAG LT776s. The recommended resolution is 1280x1024, so i guess if I can get it that high I would be very pleased.

Thanks again

---

### Post by weatherman2 on 2015-07-16
A quick google shows that that's an ancient monitor. Almost for sure, the reason you aren't able to get a higher resolution is that the video card isn't able to read the monitor information correctly.  If you have access to any other sort of monitor (flat screen TV?) to try with your Ubuntu computer, you should be able to confirm fairly easily that your integrated video card is able to display much higher resolutions than you are seeing now - and that this isn't a "Sandy Bridge" problem.

There's probably a way to muck up an xorg.conf file or something to fool the video card into displaying 1280x1024.  I haven't done that in a long time - you can either wait for someone else to respond here, start a new thread based on that approach ("How do I get my ancient monitor to display at 1280x1024 in Ubuntu 14.04?"), or buy a new monitor.  I've purchased newer monitors than yours for under $10 at the local Goodwill thrift store.

---

### Post by tom195 on 2015-07-17
> [COLOR=#000000]A quick google shows that that's an ancient monitor.[/COLOR]
[COLOR=#000000]Ha! Ancient would be an understatement. I believe Methuselah used this monitor when he was young. I guess its finally time for me to upgrade. Thanks weatherman[/COLOR]

---

