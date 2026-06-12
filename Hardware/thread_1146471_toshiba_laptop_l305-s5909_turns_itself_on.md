---
title: "toshiba laptop l305-s5909 turns itself on"
date: 2009-05-02
forum: Hardware
---

### Post by weavejd on 2009-05-02
I have a toshiba laptop, l305-s5909, dual booting vista home 64/ ubuntu 9.04 64. If I shut down either in ubuntu or vista, the thing will turn itself back on. Same thing was happening when I had only ubuntu 8.10 64 loaded. I wanted to determine what was going on, so I reformatted and just installed vista - no problems - shut down, stayed off. Installed 8.10 as a dual boot, and then would not stay turned off. When 9.04 was released, upgraded hoping that would solve the problem, but no such luck.
toshiba released a new bios, v1.80, so I flashed it, thinking that would solve the problem, but it didn't. I've turned off everything in the Insyde H2 bios that has to do with 'wake' - wake on lan, wake on wlan, wake on keyboard, etc.

Does anyone one have any suggestions? I'm going to be traveling soon and really don't want to mess with removing and installing the battery every time I use the pc.

Thanks

output of lshw:
    description: Notebook
    product: Satellite L305
    vendor: TOSHIBA
    version: PSLB8U-05302F
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=2006B5E0-B82E-11DD-A70E-001E3383C75E
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: 1.80 (03/20/2009)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 2F2F2F2F2F2F2F2F2F2F2F2F2F2F2F2F2F2F
             vendor: Samsung
             physical id: 0
             serial: 83741C2F
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 333333333333333333333333333333333333
             vendor: Samsung
             physical id: 1
             serial: 83741C33
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1e
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
          slot: CPU
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 1066MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm cpufreq
        *-cache:0
             description: L2 cache
             physical id: 1f
             slot: Unknown
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 21
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 20
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1e:33:83:c7:5e
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: Wireless WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 00
                serial: 00:21:6b:47:19:88
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.0.101 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi5
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: TOSHIBA MK3252GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LV01
                serial: 88SHC37FT
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0fd8ae86
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 8ed7e47e-5938-da44-9b1d-969ad189f63b
                   size: 1498MiB
                   capacity: 1500MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-04-08 21:51:04 filesystem=ntfs label=TOSHIBA System Volume state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/Grumpy2_C
                   version: 3.1
                   serial: 0ac3b7ba-4ce9-814d-83c9-c1c977d863d8
                   size: 87GiB
                   capacity: 87GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-04-08 21:51:07 filesystem=ntfs label=xxxxx_C mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 208GiB
                   capacity: 208GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 200GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 8707MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RW  DVRTD08L
                vendor: PIONEER
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 2.54
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@1:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by weavejd on 2009-05-04
Anyone else using a laptop that has the Insyde H2 bios?

---

### Post by niccoIndy on 2009-05-05
I have a toshiba l305-s5919 (Insyde h20 bios). I have the same issue however it was after installing the omnibook module. Since this was one of the first things i did, i just formatted the partition and planned to reinstall with out the module, funny enough this didn't fix it. I had to flash my bios to get it to stop randomly booting back up. 
 
I have not reinstalled the omnibook module, so essentially I am unable to use ubuntu on it at the moment. The processor gets quite warm like 80c before turning on the fan without the omnibook module.

---

### Post by swinky on 2009-05-07
I'm running a Toshiba Satellite L305-S5891. The omnibook module is certainly the culprit, as I have had the same problems, too.

The fan issue is easily fixed if you are running Jaunty. Open up /boot/grub/menu.lst and add **acpi_osi="Linux"** to your kernel boot parameters. My fan now properly spins up (at about 50 degrees) and spins back down (at about 35 degrees.)

---

### Post by Ceyx on 2009-05-09
Have a look at the BIOS settings ( f2 at boot )

My Toshiba L300D with Insyde H20 bios ( there is a joke there somewhere with that name ) has a setting " Critical Battery Wakeup " which may be responsible for your notebook turning itself on by itself...

Ciao !

---

### Post by weavejd on 2009-05-10
Thanks for the comments. As far as the bios, I have all "wake on" settings turned off, even the critical battery one.
Unfortunately, to get the problem resolved before my trip, I used the vista partition manager to get rid of ubuntu for now and just have vista running on the laptop :(
I'll give ubuntu a try later on. Next time I install, maybe I should go 32 instead of 64 bit?

---

### Post by weavejd on 2009-05-22
Well, I re-installed Ubuntu 9.04 64 bit, added the acpi_osi="Linux" to the boot parameters and all seems well as far as cooling and remaining turned off (it WAS the omnibook module).
The only issue now is getting hibernate to work. All I get is a blank screen when trying to resume.

---

### Post by Ghotler on 2009-05-31
> **weavejd said:**
> Well, I re-installed Ubuntu 9.04 64 bit, added the acpi_osi="Linux" to the boot parameters and all seems well as far as cooling and remaining turned off (it WAS the omnibook module).
The only issue now is getting hibernate to work. All I get is a blank screen when trying to resume.

sudo pm-suspend --quirk-s3-mode --quirk-vbe-post

try this, to me its work fine

---

### Post by Ghotler on 2009-05-31
Well i have an L300 Toshiba, with Insyde H2O BIOS, I try a lot to get working the fn keys and the fan controll:

I try to the options of bootline that is the "acpi_osi=Linux", its work for me until i reboot my comp, then the fan controll work but the fn keys not anymore...and its appeard for me, with this options my CPU work 10 % more... 

so i try an other way to solve the prob,
reading on internet, i found a developer team who develop to Toshiba laptops, currtenly for the toshiba_acpi and toshiba modules into the kernel...
they make a kernel patch to fix the toshiba_acpi and toshiba modules, so i downloaded the patch for the 2.6.29 version of kernel and patched it and compiled, then i boot from the new kernel, but the modules are didnt want to work again...

so i searching an other way, then found the omnibook modules for HP Omnibooks and Thoshiba Satellites models, i downloaded it, compiled and install, then configured, its work fine, but my laptop after when i shutdown turns back from itself after some minutes...

Well, I realy want to solve this prob, anyway, just what we/I need is that the fn keys , i mean not all, but the birghtness keys and the mute keys anyway have to be good to work, and the fan controll...thats all...
But a rad somewhere our prob will solve than if the insyde h2o BIOS will decompiled/disassembled...I think this is just a few years will be, what we have to waiting....

---

### Post by Squirrel E. Doom on 2009-08-31
I have a l305-s5909. I have Jaunty installed on an external and have a few questions if anyone could help. First, I can not use the battery at all. If the power cord is unplugged the computer shuts off. Second, the cpu fan is not working. Is the acpi_osi="Linux" command what I need to use and if so where on the boot menu would I insert this? I am a bit timid with the boot menu thing since I have managed to cause some serious problems in the past with that. Thanks for any help with this.

Also, using DeVeDe causes the computer to turn off when trying to burn a dvd. Have not tried any other apps yet. Could this all be related to the 'unregistered PM caps (version 7)' error seen at boot up?

---

