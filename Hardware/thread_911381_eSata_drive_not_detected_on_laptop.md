---
title: "eSata drive not detected on laptop"
date: 2008-09-05
forum: Hardware
---

### Post by hoisin on 2008-09-05
Hello folks --

I've been trying for the better part of two days now to get to the bottom of why my eSata drive (Nexstar3 enclosure with WD 500 GB sata2 drive) won't get picked up.  By that, I mean that there's no entry in /dev/disk subdirectories, /dev/sdb, or anywhere else, for that matter.  This is making it impossible to make a manual entry in fstab and mtab, of course.

Boot-up takes a significant amount of time before the progress bar goes anywhere (I get that Knight Rider strobing for quite some time first).  I've ran lshal, lsmod, lspci, and dmesg, but I don't know what to make of it.  Do I look for more than one sata module loaded (there are, btw), or see if the drive falls in the realm of scsi?  I'm not sure.

I have had some interesting realtime results looking at System Log.  Under messages, when I turn on the eSata drive - just to see what's happening, mind you - I get the following:

```
Sep  5 14:57:33 serenity kernel: [ 1294.473347] ata4: hard resetting link
Sep  5 14:57:41 serenity kernel: [ 1302.947013] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  5 14:58:11 serenity kernel: [ 1332.894881] ata4.00: qc timeout (cmd 0xec)
Sep  5 14:58:11 serenity kernel: [ 1332.894908] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep  5 14:58:11 serenity kernel: [ 1332.894913] ata4: failed to recover some devices, retrying in 5 secs
Sep  5 14:58:16 serenity kernel: [ 1337.890201] ata4: hard resetting link
Sep  5 14:58:17 serenity kernel: [ 1338.530105] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  5 14:58:17 serenity kernel: [ 1338.530195] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
Sep  5 14:58:17 serenity kernel: [ 1338.530200] ata4: failed to recover some devices, retrying in 5 secs
Sep  5 14:58:22 serenity kernel: [ 1343.524421] ata4: hard resetting link
Sep  5 14:58:22 serenity kernel: [ 1344.163321] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  5 14:58:52 serenity kernel: [ 1374.111294] ata4.00: qc timeout (cmd 0xec)
Sep  5 14:58:52 serenity kernel: [ 1374.111315] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep  5 14:58:52 serenity kernel: [ 1374.111321] ata4: failed to recover some devices, retrying in 5 secs
Sep  5 14:58:57 serenity kernel: [ 1379.106616] ata4: hard resetting link
Sep  5 14:58:58 serenity kernel: [ 1379.745521] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep  5 14:58:58 serenity kernel: [ 1379.745560] ata4: EH complete
```

Looks like it's trying to link up, but times out for whatever reason.

If you need to see more results of commands, like the aforementioned, or copies of log segments, I'll gladly provide them if it'll help solve this problem.  I know I'm not the only one with this issue, but I thought I'd start of new and - if possible - more thorough thread on the subject.

My laptop, btw, is an ASUS G1S-A1.

---

### Post by mumurlen on 2009-01-21
Hi 

I have the same problem when I connect my eSATA HDD.

I have a ASUS G1S-B1 with a 320 GB SATA HDD in a Smart-drive Enclosure that supports eSATA.

This is what I am getting:

Jan 21 19:03:50 g1s kernel: [19513.268235] ata4: hard resetting link
Jan 21 19:03:52 g1s kernel: [19515.164224] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jan 21 19:03:52 g1s kernel: [19515.164243] ata4: link online but device misclassified, device detection might fail
Jan 21 19:03:52 g1s kernel: [19515.164254] ata4: EH complete


Let me know if you found a way to fix it.

Best regards

Mihai

---

### Post by duhd on 2009-09-13
I have the same issue.
Does not matter if i have drive attached at boot or not.

The disk is in a Thecus N2050 enclosure that has a Silicon Image 4723 Steel Vine RAID-Controller onboard supporting Raid0 and 1. It does not matter if i use raid0 or 1. Still no change. 

I have searched all forums and i am completely lost. I have tried different boot-params, vanilla kernel (2.6.31) and have now reverted back to Ubuntu Server 9.04 with 2.6.28-15 kernel on it.

Any help would be highly appreciated.

dmesg:
```

[  905.750155] ata3: exception Emask 0x10 SAct 0x0 SErr 0x4150000 action 0xe frozen
[  905.750193] ata3: irq_stat 0x00000040, connection status changed
[  905.750217] ata3: SError: { PHYRdyChg CommWake Dispar DevExch }
[  905.750245] ata3: hard resetting link
[  915.800023] ata3: softreset failed (device not ready)
[  915.800072] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  915.800078] ata3: link online but device misclassified, retrying
[  915.800084] ata3: hard resetting link
[  916.730034] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  916.730082] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  921.730026] ata3: hard resetting link
[  922.260034] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  922.260083] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  922.260092] ata3: limiting SATA link speed to 1.5 Gbps
[  927.260030] ata3: hard resetting link
[  927.790028] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  927.790075] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  932.790025] ata3: hard resetting link
[  933.320029] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  933.320052] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[  933.320079] ata3: irq_stat 0x08000000, interface fatal error
[  933.320106] ata3: hard resetting link
[  934.250026] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  934.250068] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  939.250026] ata3: hard resetting link
[  939.780026] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  939.780068] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  939.780074] ata3: limiting SATA link speed to 1.5 Gbps
[  944.780025] ata3: hard resetting link
[  945.310029] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  945.310069] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  950.310027] ata3: hard resetting link
[  950.840027] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  950.840048] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t3
[  950.840076] ata3: irq_stat 0x08000000, interface fatal error
[  950.840102] ata3: EH complete

```

lspci:
```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation Device 087d (rev b1)

```

lshw:
```
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: To be filled by O.E.M.
       vendor: To be filled by O.E.M.
       physical id: 0
       version: To be filled by O.E.M.
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080015 (05/08/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU  230   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU 1
          size: 1600MHz
          capacity: 1666MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 2048 MHz (0.5 ns)
             product: CM2X1024-6400
             vendor: Corsair
             physical id: 0
             serial: 20202020
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 2048MHz (0.5ns)
        *-bank:1
             description: [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM Synchronous 2048 MHz (0.5 ns)
             product: CM2X1024-6400
             vendor: Corsair
             physical id: 2
             serial: 20202020
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 2048MHz (0.5ns)
        *-bank:3
             description: [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: MCP79 SMBus
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor UNCLAIMED
             description: Co-processor
             product: MCP79 Co-processor
             vendor: nVidia Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: latency=0 maxlatency=1 mingnt=3
        *-usb:0
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
        *-usb:1
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-usb:2
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
        *-usb:3
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:01:2e:27:3c:19
             size: 1GB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.2.10 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=1GB/s
        *-ide
             description: IDE interface
             product: MCP79 SATA Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: scsi3
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
           *-disk
                description: ATA Disk
                product: ST3320620AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9RV012NT
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e29c5
              *-volume:0
                   description: Linux LVM Physical Volume partition
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sda1
                   serial: naJAh6-LApQ-cBid-6PuB-RyJJ-0jzs-c46Pyq
                   size: 297GiB
                   capacity: 297GiB
                   capabilities: primary bootable multi lvm2
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sda2
                   size: 243MiB
                   capacity: 243MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /boot
                      capacity: 243MiB
                      configuration: mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:5
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:6
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver

```

---

### Post by saratoga on 2009-10-26
I also have this problem using my nvidia chipset with an eSATA drive.

---

### Post by nburns on 2009-11-17
bump.. looks like several people are having this problem. Anyone know an answer?

---

### Post by killabee44 on 2009-11-29
Same problem here... Jaunty will not detect my external esata enclosure. Not even when I boot with the drive turned on. 

This is on a desktop.

I will keep looking for an answer.

---

### Post by HaZee on 2010-02-07
Anyone found a solution yet? I'm on Karmic, still the same problem, while the disk is working perfect in M$ Windows7 (dualboot default Ubuntu ofcourse ;)) and it's working on USB also .....
 
Do I miss a driver or something ?
 
Also good to know:
- internal HDD is sata
- kernel version is 2.6.31-17

---

### Post by killabee44 on 2010-02-07
> **HaZee said:**
> Anyone found a solution yet? I'm on Karmic, still the same problem, while the disk is working perfect in M$ Windows7 (dualboot default Ubuntu ofcourse ;)) and it's working on USB also .....
 
Do I miss a driver or something ?
 
Also good to know:
- internal HDD is sata
- kernel version is 2.6.31-17

I'm a newbie, but was able to get Jaunty to see my drive. The way I found to do it takes some research and reading. First I read this post:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

In it you will find info on the fstab file: 

"/etc/fstab is a system configuration file and is used to tell the Linux kernel which partitions (file systems) to mount and where on the file system tree."

There are really good procedures listed in that thread that you need to follow. Including commands like: 

```
sudo fdisk -l
```

and

```
ls /dev/disk/by-uuid -alh
```

It will take you some reading, but after you figure out the procedure to enter the drive partitions you need mounted in your fstab, they will always work (at least they did for me).

I hope that helps.

---

### Post by HaZee on 2010-02-12
Hi Killabee44,
 
fstab is not realy the problem I think. To mount the external drive, it has to appear first in /dev (like /dev/sd* or so) ....
 
Problem is it's giving errors in both messages:
ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
ata4: limiting SATA link speed to 1.5 Gbps
ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)

and dmesg:
[    7.404026] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    7.404071] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[    7.404079] ata4: limiting SATA link speed to 1.5 Gbps
[   12.888024] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   12.888058] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[   18.372023] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   18.372044] ata4: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t4
[   18.372050] ata4: irq_stat 0x08000000, interface fatal error

When opening the bios-page it's showing "Harddisk".
When booting to windows it's working flawless (and fast!)
When I disconnect the esata and connect the USB it's working but it's much slower (to slow for bluray bitrates!)
When connecting the external drive with an sata-esata cable at the internal sata-connector, it's giving exactily the same errors / output (except ata4 > ata3).
 
My guess: it's a problem with the Ubuntu drivers which probably do not support the chipset in the external exclosure (BTW it's an Vantac MX-400-SR), but who am I? (well let me answer that myself: I'm quite new to Ubuntu/linux ;)).

---

### Post by gramoun_kal on 2012-04-27
I had the same symptoms, and fixed it. It turned out to be a bios issue. Go to your bios and find where the sata settings are. I had to switch the sata mode from "IDE" which was default to "AHCI". Then, disk recognised, mountable, and fast fast fast.

---

