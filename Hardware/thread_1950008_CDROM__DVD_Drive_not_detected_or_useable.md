---
title: "CDROM / DVD Drive not detected or useable"
date: 2012-03-31
forum: Hardware
---

### Post by jamieofm on 2012-03-31
Hi all, 

I am new to Ubuntu and am having trouble with getting my system to read my DVD drive / CD drive. 

The drive i know is fine & works perfectly under windows. However it does not show up in Ubuntu. 

I am using Ubuntu 12.04. 

I have read the forums and tried a few things, typing 'mount' gives the following output

/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jamie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jamie)


the command cat /etc/fstab gives the following

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=f40b564f-e99d-4908-b508-aa9eeb1d0f7e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e988b1a6-8980-42dc-bcfc-0f54ce360b01 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=9855fd20-ee0b-4bce-a1a7-726d97b77914 none            swap    sw              0       0


The output of 'sudo lshw -C disk' gives 

*-disk                  
       description: ATA Disk
       product: SAMSUNG SP2504C
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: VT10
       serial: S09QJ1GL623770
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0002aa7f
  *-disk
       description: ATA Disk
       product: SAMSUNG SP1604N/
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: TM10
       serial: S0DNJ10YB03388
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0003d240
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdd
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sde
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sdf

This command 'sudo hdparm -I /dev/dvd' gives:

/dev/dvd: No such file or directory

The output of 'sudo dmesg | grep -i dvd' OR 'sudo dmesg | grep -i CD-ROM

gives absolutely nothing. 

I tried the Disk Utility package and that does not show up the DVD / CD-ROM

'ls -al /dev/hd*' gives
ls: cannot access /dev/hd*: No such file or directory

same for 'ls -al /dev/sr*'

Any help much appreciated !

---

### Post by morpet28 on 2012-03-31
I'm having the same prob with ubuntu 11.10 can someone please help

---

### Post by jamieofm on 2012-03-31
I have also tried looking at the bios settings, i'm no expert but the DVD drive seems to be detected there but thats it.

---

### Post by jamieofm on 2012-04-01
Ok, so i have managed to test my DVD drive to be sure it is 100% ok. I managed that by sticking in a bootable windows CD and booting from the DVD drive. Worked fine. Needless to say i dont want to put windows back on this machine but it is frustrating that i just cant seem to find a solution as to how to get Ubuntu to recognize that i have a DVD drive !

So i am totally convinced that the drive is ok, however I dont know why Ubuntu will not see it. This must be fixable.

---

### Post by Bill Z on 2012-04-02
I have noticed this problem with 11.10.

However I also noticed that if I have a smart USB stick in another USB port then Ubuntu does see the CD ROM.  Like a SandDisk or some of the Kingstons.  Sounds wacky but it works.

My theory is that the smart USB stick that has some software in it to speed up the up and down load speed does something to wake up the OS and it sees everything in the USBs.

I also noticed that after I get the OS to see the CD ROMs and then remove everything then put just the USB back, the OS thinks there is a CD ROM connected.  So, the OS does some type of association.

I am not bit level smart enough to tell anyone how to fix this but I do use this work around.

---

### Post by dandnsmith on 2012-04-02
The fact that Windows CD boots goes in accord with the BIOS recognising the drive - if it weren't recognised, the CD wouldn't boot.

Have you also tested a LiveCD Ubuntu, to see whether you can get to the desktop - if you can, then the basic functionality is present, and there's something out of kilter in your installation.

You haven't posted anything about the hardware, which gives no chance for someone to recognise it, and possibly point out the problem.

I suggest you post the ouputs from:
a) sudo lshw
b) sudo lspci -v
and surround them with *code* quotes to render them easily readable.
This will, possibly, set us on the right track

---

### Post by morpet28 on 2012-04-02
a)           
    description: Notebook
    version: C3LMDZ19
    width: 32 bits
    capabilities: smbios-2.40 dmi-2.40 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 family=N/A sku=N/A uuid=E5462240-F54A-11DA-8197-0013A908EEAA
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
       slot: Bank 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0130J3
          date: 05/11/2006
          size: 100KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2300  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: N/A
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor est tm2 xtpr pdcm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: pipeline-burst internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM DDR2
             physical id: 0
             slot: SODIMM1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR2
             physical id: 1
             slot: SODIMM2
             size: 512MiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:d0000000-d1ffffff ioport:b0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G72M [GeForce Go 7400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:d1000000-d1ffffff memory:b0000000-bfffffff memory:d0000000-d0ffffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:d2300000-d2303fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:c8000000-c9ffffff ioport:c0000000(size=33554432)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:ca000000-cbffffff ioport:c2000000(size=33554432)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:4000(size=4096) memory:cc000000-cdffffff ioport:c4000000(size=33554432)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 02
                serial: 00:13:02:66:1d:39
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-17-generic firmware=15.32.2.9 ip=192.168.1.78 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:46 memory:cc000000-cc000fff
        *-pci:4
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:5000(size=4096) memory:ce000000-cfffffff ioport:c6000000(size=33554432)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1800(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1820(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1840(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1860(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d2304000-d23043ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:6000(size=4096) memory:d2000000-d20fffff ioport:40000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:0a:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:d2007000-d2007fff ioport:6400(size=256) ioport:6800(size=256) memory:40000000-43ffffff memory:44000000-47ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 3.1
                bus info: pci@0000:0a:03.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=3
                resources: irq:16 memory:d2006000-d20067ff memory:d2000000-d2003fff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 3.2
                bus info: pci@0000:0a:03.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7
                resources: irq:17 memory:d2004000-d2004fff
           *-network
                description: Ethernet interface
                product: PRO/100 VE Network Connection
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:0a:08.0
                logical name: eth1
                version: 02
                serial: 00:13:a9:08:ee:aa
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:d2005000-d2005fff ioport:6000(size=64)
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1880(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW DW-G520A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: GFS1
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:18c8(size=8) ioport:18ac(size=4) ioport:18c0(size=8) ioport:18a8(size=4) ioport:18b0(size=16) memory:d2304400-d23047ff
           *-disk
                description: ATA Disk
                product: ST96812AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.14
                serial: 5PJ80AC4
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000f1dc0
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: e4116e7d-bb6f-429d-8be4-b7d1eb45f0e2
                   size: 53GiB
                   capacity: 53GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-11-22 21:54:01 filesystem=ext4 lastmountpoint=/ modified=2012-01-05 11:41:56 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-04-02 15:45:52 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 2380MiB
                   capacity: 2380MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2380MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0(size=32)

---

### Post by morpet28 on 2012-04-02
b)
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: d0000000-d1ffffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Capabilities: [88] Subsystem: Sony Corporation Device 81ef
    Capabilities: [80] Power Management version 2
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at d2300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: c8000000-c9ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c1ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Sony Corporation Device 81ef
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: ca000000-cbffffff
    Prefetchable memory behind bridge: 00000000c2000000-00000000c3ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Sony Corporation Device 81ef
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: cc000000-cdffffff
    Prefetchable memory behind bridge: 00000000c4000000-00000000c5ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Sony Corporation Device 81ef
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=09, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: ce000000-cfffffff
    Prefetchable memory behind bridge: 00000000c6000000-00000000c7ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Sony Corporation Device 81ef
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d2304000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: d2000000-d20fffff
    Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
    Capabilities: [50] Subsystem: Sony Corporation Device 81ef

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1880 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 18c8 [size=8]
    I/O ports at 18ac [size=4]
    I/O ports at 18c0 [size=8]
    I/O ports at 18a8 [size=4]
    I/O ports at 18b0 [size=16]
    Memory at d2304400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Sony Corporation Device 81ef
    Flags: medium devsel, IRQ 10
    I/O ports at 18e0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [60] Power Management version 2
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1051
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at cc000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-13-02-ff-ff-66-1d-39
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at d2007000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 44000000-47fff000
    I/O window 0: 00006400-000064ff
    I/O window 1: 00006800-000068ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at d2006000 (32-bit, non-prefetchable) [size=2K]
    Memory at d2000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at d2004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
    Subsystem: Sony Corporation Device 81ef
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at d2005000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 6000 [size=64]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: e100
    Kernel modules: e100

---

### Post by jamieofm on 2012-04-02
Thanks to all who have replied. I have managed to solve this problem for myself. See below. 

So I have solved this problem. Lots of searching etc led me to pull the  DVD / CD drive out of the system and have a look if it was set to  'Slave' or 'Master' via the pins on the rear of the player. 

The switch was set to 'Slave', i moved this across to 'Master' replaced  the drive in the PC hooking it up again to it's connections and hey  presto everything is fine ! Plays DVD's and audio CD's etc no problem. 

Solved. 

Now maybe someone smart can explain why Ubuntu does not like the drive set as Slave whilst windows doesnt seem to care. 

Hope this helps someone else.

---

### Post by dandnsmith on 2012-04-03
Looking at those listings, you were probably using the wrong device names to address the device.
Windows is probably using a different strategy to get to it - I know that the way they use the BIOS info is different, resulting in some oddities at times.
Your BIOS is rather more tolerant as regards booting than some of my older systems where, if you put a CD in the slave position it just won't boot from it.

Happy to hear that you resolved it - and I'll have to bear that one in mind for the future.

---

