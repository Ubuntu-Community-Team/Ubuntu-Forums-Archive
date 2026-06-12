---
title: "LG Laptop overheats - cannot control fans"
date: 2009-05-07
forum: Hardware
---

### Post by argail1980 on 2009-05-07
Hi everyone,

I have a LG P1 pro Express dual. ATI X1400 graphics chip and ubuntu 8.10

Sometimes the Laptop spontaneously shuts down. I figured out this was because of a heat problem.
I find that the processor gets very hot (somewhat around 72°C) as soon as the system works under load. Examples are when I'm playing browser games or when I'm running virtualbox or MS-Office under wine.

Judging by the output of "acpi -tc" the fan is off, but I can hear it going. And the fan reacts to the "Fn+(fan symbol)" combination on the keyboard. 
I would appreciate any help on the interpretation on the below outputs of acpi and lm-sensors. Has anybody experience with that particular laptop? What can I do to get the temperature down?

Thanks!


/var/log/messages:
```
May  5 22:48:48 LT2 kernel: [10199.687907] ACPI: Hot trip point
May  5 22:52:23 LT2 kernel: [10413.898309] ACPI: Critical trip point
```

I have installed lm-sensors. The output of sensors is:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +64.0°C  (crit = +99.0°C)                  
temp2:       +57.0°C  (crit = +85.0°C)                  
temp3:       +40.0°C  (crit = +85.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +56.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +56.0°C  (high = +85.0°C, crit = +85.0°C)  


```
(these temeratures are among the lowest I had today)


and the one of "acpi -tc"

```
     Battery 0: Discharging, 98%, discharging at zero rate - will never fully discharge.
     Thermal 0: ok, 40.0 degrees C
     Thermal 1: ok, 57.0 degrees C
     Thermal 2: ok, 64.0 degrees C
     Cooling 0: Processor 0 of 10
     Cooling 1: Processor 0 of 10
     Cooling 2: Fan 0 of 1

```
here the output of lshw:
```
lt2                       
    description: Notebook
    product: P1-JDGEG
    vendor: LG Electronics
    version: Not Applicable
    serial: 612KSPD000688
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
  *-core
       description: Motherboard
       product: ROCKY
       vendor: LG Electronics
       physical id: 0
       version: Not Applicable
       serial: Not Applicable
       slot: @
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: RKYWSF1E (09/26/2006)
          size: 109KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: U1
          size: 1067MHz
          capacity: 2160MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: M2
             size: 512MiB
             width: 32 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1067MHz
          capacity: 1067MHz
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
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: Radeon Mobility X1400
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: ET-131x PCI-E Ethernet Controller
                vendor: Agere Systems
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:e0:91:14:e0:d1
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=et131x ip=130.83.3.48 latency=0 module=et131x multicast=yes
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wmaster0
                version: 02
                serial: 00:18:de:d8:4b:23
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=130.83.111.146 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 0.1
                bus info: pci@0000:06:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 0.2
                bus info: pci@0000:06:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 0.3
                bus info: pci@0000:06:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=57 maxlatency=4 mingnt=7 module=sdhci_pci
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
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T10N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: PH01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: FUJITSU MHV2120B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: NWB9T6B258A2
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=af84af84
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 3b1b7f29-1747-43d0-a6bd-8658c1c4bfcc
                   size: 108GiB
                   capacity: 108GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-03 16:48:20 filesystem=ext3 modified=2009-05-07 13:46:16 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-05-07 11:12:34 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2949MiB
                   capacity: 2949MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2949MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:40:94:0b:5c:d4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by argail1980 on 2009-05-07
please? any help?

---

### Post by argail1980 on 2009-05-08
another BUMP

---

### Post by argail1980 on 2009-06-02
never give up hope that somebody will talk to you...

---

### Post by eggdeng on 2009-07-27
OK, we hear you!
I have the same problem with my LG P1 Express Dual, and so apparently do a lot of other LG P1 and S1 users.
There seem to be 2 possible fixes
1) update the BIOS
With a lot of patience, you can download the file LGBIOS08.iso from 
[http://rapidshare.com/users/DIR165/]("http://rapidshare.com/users/DIR165/"). Instructions at [http://forum.notebookreview.com/showthread.php?t=302646]("http://forum.notebookreview.com/showthread.php?t=302646")
2) More promising, undervolt the processors
This involves getting PHC support for the kernel module acpi-cpufreq. Precompiled modules are available for kernels up to 2.6.23. I am using 2.6.24 so I'm going to wait a bit. Instructions at
[http://ubuntuforums.org/showthread.php?t=786402]("http://ubuntuforums.org/showthread.php?t=786402") with link to the German Wiki and at [http://aldeby.org/blog/index.php/linux-phc-cpu-undervolting.html]("http://aldeby.org/blog/index.php/linux-phc-cpu-undervolting.html")
Again, I haven't tried either of these - yet, so > Alle Angaben ohne Gewähr. ;-)Best of luck.

---

### Post by s0undt3ch on 2009-08-08
> **argail1980 said:**
> Hi everyone,

I have a LG P1 pro Express dual. ATI X1400 graphics chip....

We have the same laptop and the same issues.

I've upgraded my bios using the iso provided above, still no luck. Have you solved your issues?

---

### Post by 67GTA on 2009-08-08
You might start here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by s0undt3ch on 2009-08-08
> **67GTA said:**
> You might start here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

I'll read the whole thread, yet, I've upgraded my kernel to 2.6.31-5-generic(karmic) and also installed cpufrequtils and cpufreqd. Left app's at their defaults and, although the 2nd cpu is still hotter than the first, it's less temperature(performance mode-cpu's at full throttle 1.8Ghz) then I used to had(powersave - cpu's locked at 1Ghz).

```
$ acpi -tc
     Battery 0: Discharging, 100%, discharging at zero rate - will never fully discharge.
     Thermal 0: ok, 40.0 degrees C
     Thermal 1: ok, 47.0 degrees C
     Thermal 2: ok, 54.0 degrees C
     Cooling 0: LCD 0 of 8
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10
     Cooling 3: Fan 0 of 1
```

---

### Post by sergiom99 on 2009-08-09
> **67GTA said:**
> You might start here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)
This would surely help!
Improved mine.

---

### Post by 67GTA on 2009-08-09
> **sergiom99 said:**
> This would surely help!
Improved mine.

I'll be happy to take a look. Zip up a copy of your dsdt.dsl file and post it in the DSDT thread.

---

