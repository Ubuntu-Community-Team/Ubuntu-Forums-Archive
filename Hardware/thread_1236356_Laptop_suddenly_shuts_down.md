---
title: "Laptop suddenly shuts down"
date: 2009-08-10
forum: Hardware
---

### Post by Levo on 2009-08-10
I recently installed Ubuntu Jaunty 9.04 on an Fujitsu Siemens Amilo Xi 2428. Everything works fine (except the remote control). When it runs on battery it suddenly "closes" (like pressing the reset button) after some minutes, but the battery state is more than 90%. Does anybody know why this happens and how can this be fixed?

---

### Post by Levo on 2009-08-10
This problem doesn't occur under other OS (e.g. Windows).

---

### Post by tgalati4 on 2009-08-10
It could be a lot of things:

No thermal management so something heats up and causes a thermal shutdown.
No power management so there is excessive amperage draw causing shutdown.

When you boot up again in linux, check all the files in /var/log.  Note any error or warning conditions.

Does everything else work correctly under Jaunty?

---

### Post by sergiom99 on 2009-08-10
try>
1. update your system:
```
sudo apt-get update && sudo apt-get upgrade
```

2. Install lm-sensors to check your Temp:
```
sudo apt-get install lm-sensors && sensors
```

3. Check under power management if there's some kind of settings to shutdown your laptop when it reaches some battery level or the like.

Posting your config would also help:
```
sudo lshw 
```
and paste it here.

PS: You might also want to check your DSDT file and make a custom one. It's really easy with this how-to: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by Levo on 2009-08-11
> **sergiom99 said:**
> 
1. update your system:
```
sudo apt-get update && sudo apt-get upgrade
```
The system is automatically updated.

> **sergiom99 said:**
> 
2. Install lm-sensors to check your Temp:
```
sudo apt-get install lm-sensors && sensors
```
I installed lm-sensors, but I don't know how to use it. sensors cannot be found in the repository.

> **sergiom99 said:**
> 
3. Check under power management if there's some kind of settings to shutdown your laptop when it reaches some battery level or the like.
Yes, I have configured it to sleep.

> **sergiom99 said:**
> 
Posting your config would also help:
```
sudo lshw 
```
and paste it here.
```
    description: Notebook
    product: AMILO Xi 2428
    vendor: FUJITSU SIEMENS
    serial: YSMT012342
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=00DEDA77-1C16-DC11-9F88-CD417330066E
  *-core
       description: Motherboard
       product: F40
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: 00030D0055008F31
       serial: 5500890D29
       slot: PEG Slot J6B2
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: 1.06C (09/14/2007)
          size: 97KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: U2E1
          size: 800MHz
          capacity: 4096MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
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
             size: 4MiB
             capacity: 4MiB
             capabilities: burst internal write-back
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
          physical id: 16
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: vmx ht cpufreq
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
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
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
                product: GeForce 8600M GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
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
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-memory UNCLAIMED
                description: Memory controller
                product: Turbo Memory Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wmaster0
                version: 61
                serial: 00:13:e8:b4:05:97
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.2.9 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 01
                serial: 00:03:0d:74:58:7c
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
        *-pci:5
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: Mass storage controller
                product: Sil 3531 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress bus_master cap_list
                configuration: driver=sata_sil24 latency=0
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 4
                bus info: pci@0000:08:04.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T20N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: WW01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVS-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXE807509966
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6ec91506
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: c24d2c00-4325-4644-832c-a139e68d91c2
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-10-25 21:21:57 filesystem=ntfs label=WinRE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/DATA
                   version: 3.1
                   serial: ecc43867-3193-9d4e-bbbe-71e977589926
                   size: 169GiB
                   capacity: 169GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-12-23 00:12:46 filesystem=ntfs label=DATA mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 56c66795-8a4f-2b46-856f-b828f87858bc
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-17 23:08:12 filesystem=ntfs label=WIN-VISTA modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 721MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 14GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-battery
       description: Lithium Ion Battery
       vendor: SIMPLO
       physical id: 1
       version: SAMSUNG
       serial: e01021401B37B31520255
       slot: MAIN
       capacity: 48840mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:53:61:ab:82:f9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

> **sergiom99 said:**
> 
PS: You might also want to check your DSDT file and make a custom one. It's really easy with this how-to: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)
What does this config file do?

---

### Post by Levo on 2009-08-11
> **tgalati4 said:**
> It could be a lot of things:

No thermal management so something heats up and causes a thermal shutdown.
No power management so there is excessive amperage draw causing shutdown.

When you boot up again in linux, check all the files in /var/log.  Note any error or warning conditions.

Does everything else work correctly under Jaunty?

Yes, everything works fine. I did not find anything suspicious in the log  files.

PS: The laptop is never hot.

---

### Post by sergiom99 on 2009-08-11
I think that before sensors you need the system to detect them.
```
sudo sensors-detect
```

About the DSDT, its all explained in the thread and check this for more reference: [http://en.wikipedia.org/wiki/DSDT#Firmware_Interface](http://en.wikipedia.org/wiki/DSDT#Firmware_Interface)
Its related to the way ACPI is handled. By default, BIOS are "tuned" for windows.

---

### Post by Levo on 2009-08-11
> **sergiom99 said:**
> I think that before sensors you need the system to detect them.
```
sudo sensors-detect
```

About the DSDT, its all explained in the thread and check this for more reference: [http://en.wikipedia.org/wiki/DSDT#Firmware_Interface](http://en.wikipedia.org/wiki/DSDT#Firmware_Interface)
Its related to the way ACPI is handled. By default, BIOS are "tuned" for windows.

I configured the sensors. I installed lm-sensors, but there not any executable for this in /usr/bin/. And there isn't any package "sensors" in the repository.
The laptop is never hot. I think I'll try to make a new DSDT file.

---

### Post by sergiom99 on 2009-08-11
Levo,
the package is lm-sensors, but the command is sensors.
Other similar command is acpitools.
In mine, this last one, only started showing some info when I got my own DSDT file.

> sergio@kubuntu:~$ acpitool
  Battery #1     : discharging, 55.78%
  AC adapter     : off-line
  Thermal zone 1 : ok, 39 C

sergio@kubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +39.0°C  (crit = +95.0°C)
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +36.0°C
Core0 Temp:  +33.0°C
Core1 Temp:  +42.0°C
Core1 Temp:  +39.0°C

Do you have a Window$ dual-boot in your machine? Does the same happens if it shutdown in Ubuntu and you just restart it into Win?

As for the remote, try installing lirc. But that's just a non urgent matter ;-)

---

### Post by tgalati4 on 2009-08-11
So your BIOS is 2007 vintage.  Your processor is a Core2 Duo which is relatively new.  What are your BIOS settings for power management?  Specifically what are your battery/powersaving settings?

There may be a conflict between what the BIOS is trying to do and what the kernel is trying to control.  

So, your choices are:

Try setting different power management BIOS settings and record the behavior.  

Try installing (on a second partition) Hardy or Intrepid and see if sleep works any better.

Since sleep on a laptop is vital, that needs to fixed first before worrying about the lastest versions of packages.

Did a google search on your model reveal anything?

Finally, if Hardy/Intrepid/Jaunty won't work, then I would try Fedora then OpenSUSE.

Each handle acpi and sleep/suspend differently.

What is the output of:

cat /proc/acpi/wakeup

I'm thinking that you need a kernel switch during boot, but I don't know what switch yet.

One other possibility.  You could have a bad battery.  I've seen instances where linux freaks out with bad hardware, but Windows moves along, ignoring the hardware fault until there is a bluescreen.  So you think it's a normal windows lockup, when it's really a hardware problem that is masked by Windows brilliant operating system.

How old is the battery?  Can you get a replacement?

In Jaunty, the gnome-power-manager puts an icon on your taskbar.  If you right-click it, you get a power history graph.  Look at the power (in watts) then look at the voltage.  If the voltage decline is too steep, from 12 VDC to 10.5 VDC in a matter of minutes, then I would suspect that you have a bad cell.  Normal voltage decline would take 1 to 2 hours.

Keep a terminal open while on battery:

dmesg | tail -f

And keep watch on any error messages before shutdown.

---

### Post by Levo on 2009-08-19
Thank you all for your help. I'm going to buy a new battery and see if this happens again.
The battery is 1,5 year old. Every time Ubuntu boots, a message appears telling that its capacity is lower than 17%.

---

### Post by sergiom99 on 2009-08-19
Have you tried this?
> **sergiom99 said:**
> HP says that you need to do a complete drain-charge cycle every three months or so to keep batteries healthy. You do this by disabling all actions on low battery charge and let the computer poweroff when battery is drained. And then you charge it until full charge with laptop powered off.

Also, I read somewhere in the forums, that you need to 'let Ubuntu know' your battery life by letting it drain once, and then fully charging.

[http://ubuntuforums.org/showthread.php?t=1242973](http://ubuntuforums.org/showthread.php?t=1242973)

---

### Post by Levo on 2009-08-20
> **sergiom99 said:**
> Have you tried this?


[http://ubuntuforums.org/showthread.php?t=1242973](http://ubuntuforums.org/showthread.php?t=1242973)


The battery was being charged in the laptop for more than 1,5 year and it was never used (it was always on power). So I think that the battery is dead.

---

