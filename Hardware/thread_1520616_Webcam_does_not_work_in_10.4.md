---
title: "Webcam does not work in 10.4"
date: 2010-06-29
forum: Hardware
---

### Post by Brii on 2010-06-29
The webcam on my aspire one doesn't work. I've been to the Webcam community page and couldn't really find anything that would help me, mainly because I'm not sure what type of webcam I have on this netbook.

Any help? Thanks.

---

### Post by nixscripter on 2010-06-29
What it is connected with, PCI, USB, etc.?

Try **lspci -nn** for PCI, and **lsusb** to took at devices in those busses. If that doesn't work, try **sudo lshw**.

---

### Post by Brii on 2010-06-29
> **nixscripter said:**
> What it is connected with, PCI, USB, etc.?

Try **lspci -nn** for PCI, and **lsusb** to took at devices in those busses. If that doesn't work, try **sudo lshw**.

00:00.0 Host bridge [0600]: Intel Corporation System Controller Hub (SCH Poulsbo) [8086:8100] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108] (rev 07)
00:1b.0 Audio device [0403]: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller [8086:811b] (rev 07)
00:1c.0 PCI bridge [0604]: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 [8086:8110] (rev 07)
00:1c.1 PCI bridge [0604]: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 [8086:8112] (rev 07)
00:1d.0 USB Controller [0c03]: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 [8086:8114] (rev 07)
00:1d.1 USB Controller [0c03]: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 [8086:8115] (rev 07)
00:1d.2 USB Controller [0c03]: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 [8086:8116] (rev 07)
00:1d.7 USB Controller [0c03]: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 [8086:8117] (rev 07)
00:1f.0 ISA bridge [0601]: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge [8086:8119] (rev 07)
00:1f.1 IDE interface [0101]: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller [8086:811a] (rev 07)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

and the bus's

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 020: ID 064e:a102 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I can't find it there, but I might not be looking right.

I'm going to try that command, thanks.

---

### Post by Brii on 2010-06-29
> **nixscripter said:**
> What it is connected with, PCI, USB, etc.?

Try **lspci -nn** for PCI, and **lsusb** to took at devices in those busses. If that doesn't work, try **sudo lshw**.

Not sure what I'm suppose to look for, so here =P


brian-laptop              
    description: Computer
    product: AO751h
    vendor: Acer
    version: Not Applicable
    serial: LUS810B1819231D2802500
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=C0093DB2-3F2C-DE11-8300-00238BD97145
  *-core
       description: Motherboard
       product: JV11-ML
       vendor: Acer
       physical id: 0
       version: Not Applicable
       serial: 922JVJMBQTF0D73C
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V0.3210 (09/22/2009)
          size: 100KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: U3E1
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 xtpr pdcm movbe lahf_lm tpr_shadow vnmi flexpriority pse cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: DIMM0 J6D1
             size: 1GiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: System Controller Hub (SCH Poulsbo)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: System Controller Hub (SCH Poulsbo) Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list rom
             configuration: driver=psb latency=0
             resources: irq:16 memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff memory:b0000000-b003ffff
        *-multimedia
             description: Audio device
             product: System Controller Hub (SCH Poulsbo) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:b0050000-b0053fff
        *-pci:0
             description: PCI bridge
             product: System Controller Hub (SCH Poulsbo) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:40000000-403fffff memory:d0100000-d01fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:23:8b:d9:71:45
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:24 ioport:2000(size=256) memory:d0110000-d0110fff(prefetchable) memory:d0100000-d010ffff(prefetchable) memory:d0120000-d012ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: System Controller Hub (SCH Poulsbo) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:d0000000-d00fffff memory:40400000-405fffff(prefetchable)
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 00:24:2c:95:fd:ec
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k ip=192.168.0.133 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:d0000000-d000ffff
        *-usb:0
             description: USB Controller
             product: System Controller Hub (SCH Poulsbo) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: System Controller Hub (SCH Poulsbo) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: System Controller Hub (SCH Poulsbo) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: System Controller Hub (SCH Poulsbo) USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:b0054000-b00543ff
        *-isa
             description: ISA bridge
             product: System Controller Hub (SCH Poulsbo) LPC Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: isa
             configuration: driver=isch_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: System Controller Hub (SCH Poulsbo) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sch latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-disk
                description: ATA Disk
                product: ST9160310AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0303
                serial: 5SV78LEH
                size: 149GiB (160GB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=d45da909-a6d7-4d34-86f4-d972a33aa3ae
              *-volume:0
                   description: Windows FAT volume
                   vendor: BSD  4.4
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 70d6-1701
                   size: 199MiB
                   capacity: 199MiB
                   capabilities: boot fat initialized
                   configuration: FATs=2 filesystem=fat label=EFI name=EFI System Partition
              *-volume:1
                   description: Apple HFS partition
                   vendor: Mac OS X (journaled)
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 4
                   serial: f5616aaf-6389-73f6-0000-0000002a7000
                   size: 84GiB
                   capabilities: journaled hfsplus initialized
                   configuration: checked=2010-04-15 10:43:39 created=2010-04-15 10:43:39 filesystem=hfsplus lastmountedby=HFSJ modified=2010-04-29 16:21:58 name=MAC state=unclean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 30d23fd4-75c6-a545-90f4-5dd033d4b01c
                   size: 43GiB
                   capacity: 43GiB
                   capabilities: ntfs initialized
                   configuration: clustersize=4096 created=2010-04-30 01:21:22 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true name=WIN resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:3
                   description: EFI partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   serial: 3df60eae-e188-4b2a-9ad8-e71c760bc685
                   capacity: 1023KiB
              *-volume:4
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 5
                   bus info: scsi@0:0.0.0,5
                   logical name: /dev/sda5
                   logical name: /
                   version: 1.0
                   serial: 7105162d-1f90-48f2-89c2-932815f34a83
                   size: 19GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-06-20 16:38:20 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;p&#65533;&#65533;5&#65533;&#65533;&#65533;&#65533;&#65533;p>&#65533;&#65533;u^ &#65533;U/&#65533;d>&#65533;&#65533;~!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;>&#65533;&#65533;>&#65533;&#65533;a modified=2010-06-29 18:28:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-06-29 18:28:44 state=mounted
              *-volume:5
                   description: Linux swap volume
                   physical id: 6
                   bus info: scsi@0:0.0.0,6
                   logical name: /dev/sda6
                   version: 1
                   serial: d4735586-c449-4368-91ef-705d8b55e8ed
                   size: 932MiB
                   capacity: 932MiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4095
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound

---

### Post by Brii on 2010-06-29
I apologizes for the large copypasta's

---

### Post by Brii on 2010-06-29
> **nixscripter said:**
> What it is connected with, PCI, USB, etc.?

Try **lspci -nn** for PCI, and **lsusb** to took at devices in those busses. If that doesn't work, try **sudo lshw**.

Oh, it's not USB.

---

### Post by hackerseraph on 2010-06-29
acer laptops use USB protocol for the built in webcam. What program have you installed to view your webcam? you might want to try cheese.

```
sudo apt-get install cheese
```

---

### Post by Brii on 2010-06-29
> **hackerseraph said:**
> acer laptops use USB protocol for the built in webcam. What program have you installed to view your webcam? you might want to try cheese.

```
sudo apt-get install cheese
```

Well, I tested it on ChatRoullette and Omegle. And it said, "You need a webcam to play"

*Installing cheese now

---

### Post by Brii on 2010-06-29
I got "No device found" in cheese.

---

### Post by Brii on 2010-06-30
I'm starting to think my webcam wasn't recognized at all by Ubuntu and therefore didn't install any drivers for it.

Any ideas?

---

### Post by okplayer02 on 2010-06-30
under the lsusb command that line is your web cam so it is detected. 

```
Bus 001 Device 020: ID 064e:a102 Suyin Corp.
```


seems as though its not supported as of yet but again you can search with google and i see some information in regards to possible patch for the 2.6.33 kernel. Again though just do not rely upon ubuntuforums to get an answer you can always look to other distros about a particular piece of hardware.

---

### Post by hackerseraph on 2010-06-30
did you say its an acer one netbook? You might want to try installing the ubuntu netbook remix. I personally dont use it on my asus netbook, but a buddy of mine used it because its optimized for netbooks and he said it enabled a bunch of things on his acer.

---

### Post by hackerseraph on 2010-06-30
> **hackerseraph said:**
> did you say its an acer one netbook? You might want to try installing the ubuntu netbook remix. I personally dont use it on my asus netbook, but a buddy of mine used it because its optimized for netbooks and he said it enabled a bunch of things on his acer.

and you could always run it live to test the webcam.

---

### Post by Brii on 2010-06-30
> **okplayer02 said:**
> under the lsusb command that line is your web cam so it is detected. 

```
Bus 001 Device 020: ID 064e:a102 Suyin Corp.
```


seems as though its not supported as of yet but again you can search with google and i see some information in regards to possible patch for the 2.6.33 kernel. Again though just do not rely upon ubuntuforums to get an answer you can always look to other distros about a particular piece of hardware.

All right thanks. I'll google it and see what I find. If I find a solution I'll mark the thread as solved.

---

### Post by Brii on 2010-06-30
> **hackerseraph said:**
> and you could always run it live to test the webcam.

I'm way too settled into this install to ever make another OS switch. But I'll keep that in mind as an option if I ever need to reinstall. Thanks I didn't know about UNB till now. =D

---

### Post by Brii on 2010-06-30
This is probably a stupid question, but I found this site 

[http://www.gossamer-threads.com/lists/linux/kernel/1241857?do=post_view_flat](http://www.gossamer-threads.com/lists/linux/kernel/1241857?do=post_view_flat)

and they talk about "this" patch that allows the webcam to work, but they never link to it or anything. What patch are they talking about? Is there a link or something that I can't see?
:confused::confused::confused::confused::confused:

---

### Post by bford16 on 2010-07-02
I have the same webcam on my HP dv7-1232NR laptop.  It never worked.  Then, just this week, my wife plugged in an external webcam.  Suddenly the Suyin webcam started working, and now it works fairly reliably.  Sometimes it will shut off though (I think this is because of Flash), and then I have to reboot to get it working again.

I currently have the 2.6.32-23-generic kernel.

---

