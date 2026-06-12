---
title: "Acer Aspire 4710G no sound and fax modem"
date: 2011-07-06
forum: Hardware
---

### Post by anisrehan on 2011-07-06
I have upgraded my ubuntu 10.10 to 11.04 recently, and after upgrade 2 things were not working.

[LIST=1]
[*]fax modem
[*]wifi
[/LIST]
I  have followed the procedure posted in different forums, and un  installed the driver suggested by ubuntu, and that resolved the wifi  problem.

Now after looking for some fax modem, which is offered  by the sound card, I tried different solution, and now fax modem is not  working along with the sound.

I tried a lot of solutions, but none worked.

following are the outputs of different command lines people suggested in forums and guides.

```

sudo lshw
webcarepk                 
    description: Notebook
    version: 0100
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=2C342780-DD0F-11DC-A00C-AD84DC9C2627
  *-core
       description: Motherboard
       product: Volvi
       vendor: Acer
       physical id: 0
       version: Rev
       serial: LXANR0C00580719CAF2000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V1.14
          date: 11/05/2007
          size: 100KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) Duo CPU      T2450  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          slot: U2E1
          size: 800MHz
          capacity: 2GHz
          width: 32 bits
          clock: 133MHz
           capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8  apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe  nx constant_tsc arch_perfmon bts aperfmperf pni monitor est tm2 xtpr  pdcm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capabilities: burst external write-back
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
          physical id: e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR2 Synchronous
             physical id: 1
             slot: M2
             size: 1GiB
             width: 32 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
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
             resources: irq:40 ioport:2000(size=4096) memory:dc000000-dc0fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Radeon HD 2400 XT
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                 resources: irq:46 memory:c0000000-cfffffff memory:dc000000-dc00ffff  ioport:2000(size=256) memory:dc020000-dc03ffff
        *-multimedia UNCLAIMED
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
             resources: memory:dc400000-dc403fff
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
             resources: irq:41 ioport:3000(size=4096) memory:d6000000-d7ffffff ioport:d0000000(size=33554432)
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1d:72:1b:b4:09
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                 capabilities: pm vpd msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.116 firmware=5787m-v3.23 latency=0 link=no multicast=yes  port=twisted pair
                resources: irq:45 memory:d6000000-d600ffff
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
             resources: irq:42 ioport:4000(size=4096) memory:d8000000-d9ffffff ioport:d2000000(size=33554432)
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:d8000000-d8003fff
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
             resources: irq:43 ioport:5000(size=4096) memory:da000000-dbffffff ioport:d4000000(size=33554432)
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
             resources: irq:19 ioport:1860(size=32)
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
             resources: irq:23 memory:dc404000-dc4043ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:dc100000-dc1fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 6
                bus info: pci@0000:0a:06.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32
                resources: irq:22 memory:dc101000-dc101fff memory:dc100000-dc1007ff
           *-generic
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 6.2
                bus info: pci@0000:0a:06.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:22 memory:dc100800-dc1008ff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 6.3
                bus info: pci@0000:0a:06.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm cap_list
                configuration: latency=32
                resources: memory:dc102000-dc102fff
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
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1880(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T20N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: WP03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
              resources: irq:44 ioport:18c8(size=8) ioport:18ac(size=4)  ioport:18c0(size=8) ioport:18a8(size=4) ioport:18b0(size=16)  memory:dc404400-dc4047ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK3252GS
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: LV01
                serial: X8P9C0I5T
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=7688a6d4
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/win2008
                   version: 3.1
                   serial: 5e2ce3a0-309f-5c48-970f-ff59090edd64
                   size: 97GiB
                   capacity: 97GiB
                   capabilities: primary bootable ntfs initialized
                    configuration: clustersize=4096 created=2011-01-28 12:52:58  filesystem=ntfs label=win2008 modified_by_chkdsk=true  mount.fstype=fuseblk  mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096  mounted_on_nt4=true resize_log_file=true state=mounted  upgrade_on_mount=true
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/wares
                   version: 3.1
                   serial: 46e9e5fc-4dd1-4125-a2d1-48980ad85c8f
                   size: 97GiB
                   capacity: 97GiB
                   capabilities: primary ntfs initialized
                    configuration: clustersize=4096 created=2010-09-02 12:43:44  filesystem=ntfs label=wares mount.fstype=fuseblk  mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096  state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   size: 102GiB
                   capacity: 102GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 41GiB
                       configuration: mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered  state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2245MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /media/backup
                      capacity: 58GiB
                       configuration: mount.fstype=fuseblk  mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096  state=mounted
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
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1f:3a:1b:29:43
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic  firmware=410.2160 ip=192.168.15.131 link=yes multicast=yes wireless=IEEE  802.11bg

``````

cat /proc/asound/card0/codec* | grep Codec
cat: /proc/asound/card0/codec*: No such file or directory

``````

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh 
is here: [http://www.alsa-project.org/db/?f=fe...238af95b51ff1d]("http://www.alsa-project.org/db/?f=fe658796655756fe87f97e4dee238af95b51ff1d")
alsa-info.sh: 381: [[: not found
ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactlalsa-info.sh: 381: [[: not found
ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

alsa-info.sh: 624: [[: not found
alsa-info.sh: 624: [[: not found
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
alsa-info.sh: 5: [[: not found
alsa-info.sh: 5: [[: not found
alsa-info.sh: 5: [[: not found
alsa-info.sh: 5: [[: not found
alsa-info.sh: 5: [[: not found
alsa-info.sh: 5: [[: not found
cat: /proc/asound/modules: No such file or directory
alsa-info.sh: 5: [[: not found
alsa-info.sh: 751: [[: not found
alsa-info.sh: 776: [[: not found
Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : read: 776: Illegal option -e
alsa-info.sh: 812: [[: not found

alsa-info.sh: 812: [[: not found

Your ALSA information is in /tmp/alsa-info.txt.dGzwSIKUHv

  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

alsa-info.sh: 624: [[: not found
alsa-info.sh: 624: [[: not found
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
alsa-info.sh: 5: [[: not found
alsa-info.sh: 5: [[: not found
alsa-info.sh: 5: [[: not found
alsa-info.sh: 5: [[: not found
alsa-info.sh: 5: [[: not found
alsa-info.sh: 5: [[: not found
cat: /proc/asound/modules: No such file or directory
alsa-info.sh: 5: [[: not found
alsa-info.sh: 751: [[: not found
alsa-info.sh: 776: [[: not found
Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : read: 776: Illegal option -e
alsa-info.sh: 812: [[: not found

alsa-info.sh: 812: [[: not found

Your ALSA information is in /tmp/alsa-info.txt.dGzwSIKUHv


```
Now I am stuck, at least the sound should work if not the fax modem.
In my sound settings, I don't have anything under hardware tab.

running alsa-mixer opens a blank window.

what should I do to get the sound and fax modem working???

---

### Post by lidex on 2011-07-06
I would suggest backing up your data and wiping out that natty install then install from scratch using the latest natty release.

---

### Post by anisrehan on 2011-07-07
Thanks for the advice
I thought of doing it, but the problems are 

[LIST]
[*]I have a lot of work going on,
[*]this is the single laptop/pc I have and
[*]No other os is running on it.
[/LIST]
So it will be a great risk.
In windows, I use to insert the installation media, and refresh the drivers, doesn't linux has anything like that?

---

