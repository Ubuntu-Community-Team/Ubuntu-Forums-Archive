---
title: "How do you get a full hardware audit"
date: 2011-10-10
forum: Hardware
---

### Post by Jonners59 on 2011-10-10
I need to do some upgrading, but before I do I need to know exactly what is currently installed hardware wise on my machine.  How do I run a scan or is their an app that creates a list, please?

---

### Post by SuperFreak on 2011-10-10
Device Manager which is available in Ubuntu Software Center may help you. It works much like the Windows version.
This is a GNOME program to manage devices and device drivers. It's inspired by hal-device-manager, from the HAL project, but rewritten in C for efficiency and an outlook to actually make it manage devices rather than just show information.

---

### Post by jocko on 2011-10-10
To get a complete list of all hardware:
```
sudo lshw -html > ~/hardware.html
```
It will make a nice html file in your home directory.

---

### Post by Jonners59 on 2011-10-11
Excellent.  Thanks guys.

The cmd line was more what I was after as it gave more detail, though it was unable to recognise the version of my Motherboard, which is a shame because that is what I was after.
[HTML]
id:core          
description: Motherboard        
product: nForce        
vendor: Gigabyte Technology Co., Ltd.        
physical id: 0        
version: x.x
[/HTML]

A question for "Jocko" or anyone else who can answer this for me, please

It lists the RAM slots, but I am not sure what it is saying.

I have 4 slots of which two are used.  It states that, BUT it says that the capacity is 8Gb e.g. 2 of the 4 slots are listed below by way of examples of used and empty:
[HTML]id:bank:0                
description: DIMM              
physical id: 0              
slot: A0              
size: 8GiB              
width: 64 bits[/HTML]

and empty slot example

[HTML]id:bank:2                
description: DIMM [empty]              
physical id: 2              
slot: A2              
width: 64 bits[/HTML]

All good stuff, BUT is it saying that:
a. the RAM in that slot is 8Gb or 
b. the capacity of the slot is 8Gb or 
c. that TOTAL capacity of all filled slots is 8Gb

I believe that the RAM cards I have are no more than 2Gb each, so confused by the figure. ??????? :confused:
 Do you or anyone know?

In essence the issue I have that shall require upgrades is:
The CPU is a 64bit so needs at least 12Gb of RAM to work properly
The CPU has failed, so I am only getting one channel working.

I need a new CPU and more RAM.  Can the mother board take the additional RAM.

---

### Post by matt_symes on 2011-10-11
Hi

> All good stuff, BUT is it saying the RAM in that slot is 8Gb or the  capacity of the slot is 8Gb or that TOTAL capacity of all filled slots  is 8Gb??????? It's saying that the stick in that RAM slot is an 8G memory module.

Do you want to post the whole of the lshw report ?

This may give you more information on your motherboard...

```
sudo dmidecode -t 2
```You can always open the case to find the motherboard information

Kind regards

---

### Post by Jonners59 on 2011-10-11
> **matt_symes said:**
> You can always open the case to find the motherboard information


Cheeky :D
Actually, it isn't that clear inside...  there is no label visible.

RAM:  Mmm  according to System Monitor it only has 2Gb total...  I do NOT recall putting in such a large amount of RAM.  I thought I had put in either 2 x 1Gb or 2 x 2Gb of RAM... even more confused.

The new cmd line gave no more infor:

[HTML]# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: nForce
    Version: x.x
    Serial Number:  
[/HTML]

The last report is pasted below.

[HTML]    id:baronipc       description: Desktop Computer     width: 64 bits     capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32      configuration: boot=normal chassis=desktop                   id:core          description: Motherboard        product: nForce        vendor: Gigabyte Technology Co., Ltd.        physical id: 0        version: x.x                                id:firmware             description: BIOS           vendor: Award Software International, Inc.           physical id: 0           version: F6           date: 08/22/2005           size: 128KiB           capacity: 192KiB           capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification                                            id:cpu:0             description: CPU           product: AMD Athlon(tm) 64 Processor 3200+           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 4           bus info: cpu@0           version: AMD Athlon(tm) 64 Processor 3200+           slot: Socket 939           size: 1GHz           capacity: 3GHz           width: 64 bits           clock: 200MHz           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up rep_good nopl pni lahf_lm cpufreq                                             id:cache:0                description: L1 cache              physical id: b              slot: Internal Cache              size: 128KiB              capacity: 128KiB              capabilities: synchronous internal write-back                                                           id:cache:1                description: L2 cache              physical id: d              slot: External Cache              size: 512KiB              capacity: 512KiB              capabilities: synchronous internal write-back                                                          id:cpu:1             description: CPU           vendor: Unknown           physical id: 5           bus info: cpu@1           version: AMD Athlon(tm) 64 Processor 3200+           slot: Socket 939           size: 2GHz           capacity: 3GHz           clock: 200MHz                                            id:cache                description: L1 cache              physical id: c              slot: Internal Cache              size: 128KiB              capacity: 128KiB              capabilities: synchronous internal write-back                                                          id:memory             description: System Memory           physical id: 1f           slot: System board or motherboard           size: 16GiB                                            id:bank:0                description: DIMM              physical id: 0              slot: A0              size: 8GiB              width: 64 bits                                                          id:bank:1                description: DIMM              physical id: 1              slot: A1              size: 8GiB              width: 64 bits                                                          id:bank:2                description: DIMM [empty]              physical id: 2              slot: A2              width: 64 bits                                                          id:bank:3                description: DIMM [empty]              physical id: 3              slot: A3              width: 64 bits                                                         id:pci:0             description: Host bridge           product: nForce3 250Gb Host Bridge           vendor: nVidia Corporation           physical id: 100           bus info: pci@0000:00:00.0           version: a1           width: 32 bits           clock: 66MHz           configuration: driver=agpgart-amd64           resources: irq:0 memory:0-1ffffff                                            id:isa                description: ISA bridge              product: nForce3 250Gb LPC Bridge              vendor: nVidia Corporation              physical id: 1              bus info: pci@0000:00:01.0              version: a2              width: 32 bits              clock: 66MHz              capabilities: isa bus_master               configuration: latency=0                                                          id:serial                description: SMBus              product: nForce 250Gb PCI System Management              vendor: nVidia Corporation              physical id: 1.1              bus info: pci@0000:00:01.1              version: a1              width: 32 bits              clock: 66MHz              capabilities: pm cap_list               configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3              resources: irq:10 ioport:e400(size=32) ioport:1c00(size=64) ioport:2000(size=64)                                                          id:usb:0                description: USB Controller              product: CK8S USB Controller              vendor: nVidia Corporation              physical id: 2              bus info: pci@0000:00:02.0              version: a1              width: 32 bits              clock: 66MHz              capabilities: pm ohci bus_master cap_list               configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3              resources: irq:20 memory:f6003000-f6003fff                                                          id:usb:1                description: USB Controller              product: CK8S USB Controller              vendor: nVidia Corporation              physical id: 2.1              bus info: pci@0000:00:02.1              version: a1              width: 32 bits              clock: 66MHz              capabilities: pm ohci bus_master cap_list               configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3              resources: irq:22 memory:f6004000-f6004fff                                                          id:usb:2                description: USB Controller              product: nForce3 EHCI USB 2.0 Controller              vendor: nVidia Corporation              physical id: 2.2              bus info: pci@0000:00:02.2              version: a2              width: 32 bits              clock: 66MHz              capabilities: debug pm ehci bus_master cap_list               configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3              resources: irq:21 memory:f6005000-f60050ff                                                          id:multimedia                description: Multimedia audio controller              product: nForce3 250Gb AC'97 Audio Controller              vendor: nVidia Corporation              physical id: 6              bus info: pci@0000:00:06.0              version: a1              width: 32 bits              clock: 66MHz              capabilities: pm bus_master cap_list               configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2              resources: irq:21 ioport:bc00(size=256) ioport:c000(size=128) memory:f6001000-f6001fff                                                          id:ide:0                description: IDE interface              product: CK8S Parallel ATA Controller (v2.5)              vendor: nVidia Corporation              physical id: 8              bus info: pci@0000:00:08.0              logical name: scsi1              version: a2              width: 32 bits              clock: 66MHz              capabilities: ide pm bus_master cap_list emulated               configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3              resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)                                                        id:cdrom:0                   description: DVD-RAM writer                 product: DVD-RAM GH22NP20                 vendor: HL-DT-ST                 physical id: 0.0.0                 bus info: scsi@1:0.0.0                 logical name: /dev/cdrom1                 logical name: /dev/cdrw1                 logical name: /dev/dvd1                 logical name: /dev/dvdrw1                 logical name: /dev/scd0                 logical name: /dev/sr0                 version: 1.00                 serial: [                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram                  configuration: ansiversion=5 status=nodisc                                                                         id:cdrom:1                   description: DVD-RAM writer                 product: CDDVDW SH-S223C                 vendor: TSSTcorp                 physical id: 0.1.0                 bus info: scsi@1:0.1.0                 logical name: /dev/cdrom                 logical name: /dev/cdrw                 logical name: /dev/dvd                 logical name: /dev/dvdrw                 logical name: /dev/scd1                 logical name: /dev/sr1                 version: SB02                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram                  configuration: ansiversion=5 status=nodisc                                                                           id:ide:1                description: IDE interface              product: nForce3 Serial ATA Controller              vendor: nVidia Corporation              physical id: a              bus info: pci@0000:00:0a.0              logical name: scsi2              logical name: scsi3              version: a2              width: 32 bits              clock: 66MHz              capabilities: ide pm bus_master cap_list emulated               configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3              resources: irq:22 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) ioport:e000(size=128)                                                        id:disk:0                   description: ATA Disk                 product: WDC WD2500AAJS-6                 vendor: Western Digital                 physical id: 0                 bus info: scsi@2:0.0.0                 logical name: /dev/sda                 version: 02.0                 serial: WD-WMAV2A990502                 size: 232GiB (250GB)                 capabilities: partitioned partitioned:dos                  configuration: ansiversion=5 signature=fbf8baea                                                                    id:volume:0                      description: EXT4 volume                    vendor: Linux                    physical id: 1                    bus info: scsi@2:0.0.0,1                    logical name: /dev/sda1                    version: 1.0                    serial: f38aecc5-6c27-4a9d-a7d1-0af5107a2152                    size: 6587MiB                    capacity: 6587MiB                    capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized                     configuration: created=2010-08-04 08:24:51 filesystem=ext4 label=Boot lastmountpoint=/media/Boot modified=2011-07-23 16:42:55 mounted=2011-07-23 16:41:40 state=clean                                                                                        id:volume:1                      description: Linux swap volume                    physical id: 2                    bus info: scsi@2:0.0.0,2                    logical name: /dev/sda2                    version: 1                    serial: 100fbcc3-9c57-4892-8ada-eb8ef96902be                    size: 14GiB                    capacity: 14GiB                    capabilities: primary nofs swap initialized                     configuration: filesystem=swap pagesize=4096                                                                                        id:volume:2                      description: Extended partition                    physical id: 3                    bus info: scsi@2:0.0.0,3                    logical name: /dev/sda3                    size: 114GiB                    capacity: 114GiB                    capabilities: primary extended partitioned partitioned:extended                                                                                 id:logicalvolume:0                         description: Linux filesystem partition                       physical id: 5                       logical name: /dev/sda5                       logical name: /tmp                       capacity: 9GiB                       configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted                                                                                                       id:logicalvolume:1                         description: Linux filesystem partition                       physical id: 6                       logical name: /dev/sda6                       logical name: /usr                       capacity: 9530MiB                       configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted                                                                                                       id:logicalvolume:2                         description: Linux filesystem partition                       physical id: 7                       logical name: /dev/sda7                       logical name: /var                       capacity: 11GiB                       configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted                                                                                                       id:logicalvolume:3                         description: Linux filesystem partition                       physical id: 8                       logical name: /dev/sda8                       logical name: /srv                       capacity: 9538MiB                       configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted                                                                                                       id:logicalvolume:4                         description: Linux filesystem partition                       physical id: 9                       logical name: /dev/sda9                       logical name: /opt                       capacity: 9538MiB                       configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted                                                                                                       id:logicalvolume:5                         description: Linux filesystem partition                       physical id: a                       logical name: /dev/sda10                       logical name: /usr/local                       capacity: 9538MiB                       configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted                                                                                                       id:logicalvolume:6                         description: Linux filesystem partition                       physical id: b                       logical name: /dev/sda11                       logical name: /                       capacity: 27GiB                       configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted                                                                                                       id:logicalvolume:7                         description: Linux filesystem partition                       physical id: c                       logical name: /dev/sda12                       capacity: 29GiB                                                                                                               id:volume:3                      description: Windows NTFS volume                    physical id: 4                    bus info: scsi@2:0.0.0,4                    logical name: /dev/sda4                    version: 3.1                    serial: 583e3fad-069b-7348-b8ce-4bc5c705328a                    size: 97GiB                    capacity: 97GiB                    capabilities: primary ntfs initialized                     configuration: clustersize=4096 created=2011-07-23 20:50:38 filesystem=ntfs label=Windows7 state=clean                                                                                             id:disk:1                   description: ATA Disk                 product: SAMSUNG HD501LJ                 physical id: 1                 bus info: scsi@3:0.0.0                 logical name: /dev/sdb                 version: CR10                 serial: S0MUJ1EQ129689                 size: 465GiB (500GB)                 capabilities: partitioned partitioned:dos                  configuration: ansiversion=5 signature=0009f620                                                                    id:volume:0                      description: EXT4 volume                    vendor: Linux                    physical id: 1                    bus info: scsi@3:0.0.0,1                    logical name: /dev/sdb1                    logical name: /media/Backup                    version: 1.0                    serial: 9972d3c0-79f8-4baa-ae8f-ccbc63f630a8                    size: 269GiB                    capacity: 269GiB                    capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized                     configuration: created=2011-03-14 14:30:35 filesystem=ext4 label=Backup lastmountpoint=/media/Backup modified=2011-10-11 08:53:19 mount.fstype=ext4 mount.options=rw,noatime,user_xattr,barrier=1,data=ordered mounted=2011-10-11 08:53:19 state=mounted                                                                                        id:volume:1                      description: EXT4 volume                    vendor: Linux                    physical id: 2                    bus info: scsi@3:0.0.0,2                    logical name: /dev/sdb2                    logical name: /media/Documents                    version: 1.0                    serial: 34554d66-9ae8-40e4-808a-d3b22d06623d                    size: 98GiB                    capacity: 98GiB                    capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized                     configuration: created=2010-09-11 13:02:58 filesystem=ext4 label=Documents lastmountpoint=/media/Documents modified=2011-10-11 08:53:19 mount.fstype=ext4 mount.options=rw,noatime,user_xattr,barrier=1,data=ordered mounted=2011-10-11 08:53:19 state=mounted                                                                                        id:volume:2                      description: Extended partition                    physical id: 4                    bus info: scsi@3:0.0.0,4                    logical name: /dev/sdb4                    size: 97GiB                    capacity: 97GiB                    capabilities: primary extended partitioned partitioned:extended                                                                                 id:logicalvolume                         description: Linux filesystem partition                       physical id: 5                       logical name: /dev/sdb5                       logical name: /home                       capacity: 97GiB                       configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted                                                                                                                      id:pci:0                description: PCI bridge              product: nForce3 250Gb AGP Host to PCI Bridge              vendor: nVidia Corporation              physical id: b              bus info: pci@0000:00:0b.0              version: a2              width: 32 bits              clock: 66MHz              capabilities: pci normal_decode bus_master               resources: memory:f2000000-f3ffffff memory:e0000000-efffffff                                                        id:display                   description: VGA compatible controller                 product: NV34 [GeForce FX 5200]                 vendor: nVidia Corporation                 physical id: 0                 bus info: pci@0000:01:00.0                 version: a1                 width: 32 bits                 clock: 66MHz                 capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom                  configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5                 resources: irq:16 memory:f2000000-f2ffffff memory:e0000000-efffffff memory:f3000000-f301ffff                                                                           id:pci:1                description: PCI bridge              product: nForce3 250Gb PCI-to-PCI Bridge              vendor: nVidia Corporation              physical id: e              bus info: pci@0000:00:0e.0              version: a2              width: 32 bits              clock: 66MHz              capabilities: pci normal_decode bus_master               resources: ioport:a000(size=4096) memory:f4000000-f5ffffff memory:80000000-800fffff                                                        id:network                   description: Ethernet interface                 product: 88E8001 Gigabit Ethernet Controller                 vendor: Marvell Technology Group Ltd.                 physical id: b                 bus info: pci@0000:02:0b.0                 logical name: eth0                 version: 13                 serial: 00:14:85:26:9c:03                 size: 1Gbit/s                 capacity: 1Gbit/s                 width: 32 bits                 clock: 66MHz                 capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                  configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.62 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=1Gbit/s                 resources: irq:19 memory:f5000000-f5003fff ioport:a000(size=256) memory:80000000-8001ffff                                                                          id:pci:1             description: Host bridge           product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 101           bus info: pci@0000:00:18.0           version: 00           width: 32 bits           clock: 33MHz                                           id:pci:2             description: Host bridge           product: K8 [Athlon64/Opteron] Address Map           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 102           bus info: pci@0000:00:18.1           version: 00           width: 32 bits           clock: 33MHz                                           id:pci:3             description: Host bridge           product: K8 [Athlon64/Opteron] DRAM Controller           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 103           bus info: pci@0000:00:18.2           version: 00           width: 32 bits           clock: 33MHz                                           id:pci:4             description: Host bridge           product: K8 [Athlon64/Opteron] Miscellaneous Control           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 104           bus info: pci@0000:00:18.3           version: 00           width: 32 bits           clock: 33MHz           configuration: driver=k8temp           resources: irq:0                         [/HTML]

---

### Post by matt_symes on 2011-10-11
Hi

> **Jonners59 said:**
> Cheeky :D
Actually, it isn't that clear inside...  there is no label visible.

It was not meant to be cheeky but now i re-read it....:tongue:

> 
RAM:  Mmm  according to System Monitor it only has 2Gb total...  I do NOT recall putting in such a large amount of RAM.  I thought I had put in either 2 x 1Gb or 2 x 2Gb of RAM... even more confused.
Actually i am a bit confused by this as well.  I have three 3G ram in two slots. Have a look at lshw for my memory.

```
matthew@matthew-laptop:~$ sudo lshw -c memory
<snip- Removed cache info >
  *-memory
       description: System Memory
       physical id: 19
       slot: System board or motherboard
       size: 3GiB
     *-bank:0
          description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
          physical id: 0
          slot: S1
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:1
          description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
          physical id: 1
          slot: S2
          size: 1GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
matthew@matthew-laptop:~$ 

```> 
The new cmd line gave no more infor:

```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: nForce
    Version: x.x
    Serial Number:  

```I was hoping dmidecode may return more info.

Try this from the terminal

```
sudo dmidecode -t memory
```or 

```
sudo dmidecode -t 16
```Here is mine (with DMI code 16). It specifies the maximum capacity of the memory array.

```
matthew@matthew-laptop:~$ sudo dmidecode -t 16
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0019, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 8 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

matthew@matthew-laptop:~$ 
```BTW: Please use code tags and not html tags.

Kind regards

---

### Post by Jonners59 on 2011-10-11
> **matt_symes said:**
> 
Actually i am a bit confused by this as well. 
I was hoping dmidecode may return more info.


That makes me feel better!

> **matt_symes said:**
> 
BTW: Please use code tags and not html tags.


OK

> **matt_symes said:**
> 
Try this from the terminal
```
sudo dmidecode -t memory
```


```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0006, DMI type 5, 24 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 4096 MB
    Maximum Total Memory Size: 16384 MB
    Supported Speeds:
        70 ns
        60 ns
        50 ns
    Supported Memory Types:
        Standard
        DIMM
    Memory Module Voltage: 2.9 V
    Associated Memory Slots: 4
        0x0007
        0x0008
        0x0009
        0x000A
    Enabled Error Correcting Capabilities:
        None

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 1
    Current Speed: 5 ns
    Type: Unknown EDO
    Installed Size: 8192 MB (Double-bank Connection)
    Enabled Size: 8192 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: 2
    Current Speed: 5 ns
    Type: Unknown EDO
    Installed Size: 8192 MB (Double-bank Connection)
    Enabled Size: 8192 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A2
    Bank Connections: 3
    Current Speed: 5 ns
    Type: Unknown EDO
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A3
    Bank Connections: 4
    Current Speed: 5 ns
    Type: Unknown EDO
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x001F, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x0020, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x001F
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer:  
    Serial Number:  
    Asset Tag:  
    Part Number:  

Handle 0x0021, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x001F
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer:  
    Serial Number:  
    Asset Tag:  
    Part Number:  

Handle 0x0022, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x001F
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A2
    Bank Locator: Bank4/5
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer:  
    Serial Number:  
    Asset Tag:  
    Part Number:  

Handle 0x0023, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x001F
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: A3
    Bank Locator: Bank6/7
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer:  
    Serial Number:  
    Asset Tag:  
    Part Number:  

```

> **matt_symes said:**
> 
Try this from the terminal
```
sudo dmidecode -t 16
```


```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x001F, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

```

WHat do you think...?

---

### Post by matt_symes on 2011-10-11
Hi

This is a cleaned up version of your memory from lshw.

```
id:memory             
    description: System Memory           
    physical id: 1f           
    slot: System board or motherboard           
    size: 16GiB                                            

id:bank:0                
    description: DIMM              
    physical id: 0              
    slot: A0              
    size: 8GiB              
    width: 64 bits
                                                          
id:bank:1                
    description: DIMM              
    physical id: 1              
    slot: A1              
    size: 8GiB              
   width: 64 bits
                                                         
id:bank:2                
    description: DIMM [empty]              
    physical id: 2              
    slot: A2              
    width: 64 bits                                                          

id:bank:3                
    description: DIMM [empty]              
    physical id: 3              
    slot: A3              
    width: 64 bits

```[FONT=monospace]This suggests you have memory in slot 0 and 1 of size 8G each. Banks 3 and 4 are empty.

[/FONT]> 
id:bank:0 
    size: 8GiB

id:bank:1
    size: 8GiB 
 This suggests your board can handle 16G.
[FONT=monospace]
[/FONT]> Maximum Capacity: 16 GBsudo dmidecode -t memory is suggesting the same thing.

From the terminal post back the results of

```
uname -a
```and 

```
free -m
```and 

```
grep MemTotal /proc/meminfo
```Kind regards

---

### Post by matt_symes on 2011-10-11
Hi

If you check my post #7 you will see that i have

```
*-memory       
         size: 3GiB      
    *-bank:0           
        size: 2GiB      
    *-bank:1           
        size: 1GiB
```3G memory. 2G in bank 0 and 1G in bank 1. 
```

Physical Memory Array
        Maximum Capacity: 8 GB
```My board can handle a maximum of 8G.

General memory info of my system.

```
matthew@matthew-laptop:~$ uname -a
Linux matthew-laptop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
matthew@matthew-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2764       2635        129          0         33        337
-/+ buffers/cache:       2264        500
Swap:         4974         48       4926
matthew@matthew-laptop:~$ grep MemTotal /proc/meminfo
MemTotal:        2830880 kB
matthew@matthew-laptop:~$ 
```

Kind regards

---

### Post by Jonners59 on 2011-10-11
Cheers Matt
I was kinda guessing that too.  Glad you confirmed it.  But it still confuses me as I am sure I did not put that much RAM in and the System Management tools say the same...  OK your requests

```
 uname -a
Linux baronipc 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1919         89          0         10        166
-/+ buffers/cache:       1742        266
Swap:        14472       1547      12925

```

```
grep MemTotal /proc/meminfo
MemTotal:        2056852 kB

```

---

### Post by matt_symes on 2011-10-11
Hi

That is really odd. :-k

Unless i am misreading your output from lshw and dmidecode then they are returning different values than your current memory as returned by free and meminfo.

I am reading lshw and dmidecode on your machine the same way i do on mine and i know that, on my machine at least, it is correct.

Can you post the output of

```
dmesg | grep -i memory
```What does it say in the BIOS or on the BIOS boot screen?

Kind regards

---

### Post by Jonners59 on 2011-10-11
Sorry for the slow response.  Had to see my accountant.

> **matt_symes said:**
> Can you post the output of

```
dmesg | grep -i memory
```


```
dmesg | grep -i memory
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007fff0000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Memory: 2041392k/2097088k available (5943k kernel code, 452k absent, 55244k reserved, 5015k data, 956k init)
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010767] Initializing cgroup subsys memory
[    0.631530] Freeing initrd memory: 12880k freed
[    0.641512] Freeing unused kernel memory: 956k freed
[    0.642835] Freeing unused kernel memory: 184k freed
[    0.648539] Freeing unused kernel memory: 1440k freed

```

> **matt_symes said:**
> What does it say in the BIOS or on the BIOS boot screen?


I don't recall.  It moves so fast, but I'll check next time I log on/boot up.

---

### Post by Jonners59 on 2011-10-11
OK, done a reboot and checked the DOS and it says 2Gb

Also took one of the RAM cards out and it says:
Kingston KVR KVR400x64C3A/1G 2.6v, which I read as 1Gb, and did a check on the web and it is a 1Gb RAM.  SO I was correct in my recollection.

I also booted in to Windows and looked in the PC Properties.  It states it is 8Gb with 2Gb usable.  Not quite sure what that means, maybe the board takes a max of 8Gb but only 2 Gb installed, but that differs from the 16Gb in Ubuntu!!!!!!!!!!!!!!!!!!!!! :confused::confused::confused::confused::confused::confused::confused:

---

### Post by matt_symes on 2011-10-11
Hi

> **Jonners59 said:**
> OK, done a reboot and checked the DOS and it says 2Gb

Also took one of the RAM cards out and it says:
Kingston KVR KVR400x64C3A/1G 2.6v, which I read as 1Gb, and did a check on the web and it is a 1Gb RAM. SO I was correct in my recollection.

I also booted in to Windows and looked in the PC Properties. It states it is 8Gb with 2Gb usable. Not quite sure what that means, maybe the board takes a max of 8Gb but only 2 Gb installed, but that differs from the 16Gb in Ubuntu!!!!!!!!!!!!!!!!!!!!! 

You getting strange results and differing results here in Ubuntu and Windows.

If you have two 1G memory modules installed then at least they both agree about that.

Is your windows 32 or 64 bit ?

You could try cpu-z (free download) in windows and see if that knows what your motherboard and memory is. Then download the motherboard manual.

I'm wondering if your motherboard has a dodgy BIOS that Ubuntu is not reading correctly.

Kind regards

---

