---
title: "Installing on Intel Core i7 / Haswell"
date: 2015-12-23
forum: Hardware
---

### Post by Nugzar on 2015-12-23
I have fresh installed and upgraded Ubuntu 14.04.3 LTS (before it i tried this distributive and debian with same problem)

I did not install any other software, now, but Firefox crashes and OS freezes (Ctrl+Alt+F1-6 doesn't works. helps only Ctrl+Alt+PrtScr+B)

I have installed those distributive on my laptop and it works good

And i think that the problem in the hardware

here's the output of `uname -a`

```

Linux nugzar-All-Series 3.19.0-42-generic #48~14.04.1-Ubuntu SMP Fri Dec 18 10:24:49 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

the output of `lsusb`
```

Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1908:2311 GEMBIRD 
Bus 001 Device 002: ID 18d1:4ee2 Google Inc. Nexus 4 (debug)
Bus 001 Device 005: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 09da:054f A4 Tech Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

the output of `lspci`

```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation Device 8cb1
00:16.0 Communication controller: Intel Corporation Device 8cba
00:1a.0 USB controller: Intel Corporation Device 8cad
00:1b.0 Audio device: Intel Corporation Device 8ca0
00:1c.0 PCI bridge: Intel Corporation Device 8c90 (rev d0)
00:1c.2 PCI bridge: Intel Corporation Device 8c94 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d0)
00:1d.0 USB controller: Intel Corporation Device 8ca6
00:1f.0 ISA bridge: Intel Corporation Device 8cc6
00:1f.2 SATA controller: Intel Corporation Device 8c82
00:1f.3 SMBus: Intel Corporation Device 8ca2
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 04)

```

the output of `dmesg | tail`

```

[    2.637027] init: plymouth-upstart-bridge main process ended, respawning
[    2.640325] init: plymouth-upstart-bridge main process (1256) terminated with status 1
[    2.640331] init: plymouth-upstart-bridge main process ended, respawning
[    3.982352] r8169 0000:03:00.0 eth0: link up
[    3.982359] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   25.955214] systemd-hostnamed[2193]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[   32.148940] audit_printk_skb: 153 callbacks suppressed
[   32.148942] audit: type=1400 audit(1450850498.046:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2241 comm="apparmor_parser"
[   32.148947] audit: type=1400 audit(1450850498.046:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2241 comm="apparmor_parser"
[   32.149151] audit: type=1400 audit(1450850498.046:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2241 comm="apparmor_parser"

```

the output of `lshw`

```

nugzar-all-series         
    description: Desktop Computer
    product: All Series (All)
    vendor: ASUS
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=ASUS MB frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=All uuid=60AE8E30-DAD7-DD11-B74F-1C872C580189
  *-core
       description: Motherboard
       product: H97-PLUS
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: 150544729602167
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 2502
          date: 04/08/2015
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 44
          slot: System board or motherboard
          size: 32GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             vendor: 0000
             physical id: 0
             serial: 00000000
             slot: DIMM_A1
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             vendor: 0000
             physical id: 1
             serial: 00000000
             slot: DIMM_A2
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             vendor: 0000
             physical id: 2
             serial: 00000000
             slot: DIMM_B1
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             vendor: 0000
             physical id: 3
             serial: 00000000
             slot: DIMM_B2
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz
          vendor: Intel Corp.
          physical id: 53
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz
          slot: SOCKET 1150
          size: 3948MHz
          capacity: 3948MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm xsaveopt cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 54
             slot: CPU Internal L1
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 55
             slot: CPU Internal L2
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 56
             slot: CPU Internal L3
             size: 8MiB
             capacity: 8MiB
             capabilities: synchronous internal write-back unified
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
             resources: irq:24
        *-display
             description: VGA compatible controller
             product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
        *-multimedia:0
             description: Audio device
             product: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:31 memory:f7d14000-f7d17fff
        *-usb:0
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:25 memory:f7d00000-f7d0ffff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:29 memory:f7d1d000-f7d1d00f
        *-usb:1
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:f7d1b000-f7d1b3ff
        *-multimedia:1
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:30 memory:f7d10000-f7d13fff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:e000(size=4096) memory:f7c00000-f7cfffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 11
                serial: 1c:87:2c:58:01:89
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=10.10.1.108 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:27 ioport:e000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pci subtractive_decode bus_master cap_list
                resources: iomemory:202001f10-202001f0f
        *-usb:2
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7d1a000-f7d1a3ff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7d19000-f7d197ff
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7d18000-f7d180ff ioport:f040(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SPCC Solid State
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.6
             serial: EB98075904F000718449
             size: 223GiB (240GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=9fee925c-7ad4-4af4-9f35-a4c38254758a sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: eb5e-9347
                size: 248MiB
                capacity: 249MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat label=boot mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: 22496786-1639-4e3c-89b5-df465c8219e7
                size: 20GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-12-23 10:30:57 filesystem=ext4 lastmountpoint=/ modified=2015-12-23 11:17:06 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-12-23 11:17:06 state=mounted
           *-volume:2
                description: swap partition
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: daf7daf4-c7ab-409d-90a6-101f6a02dab6
                capacity: 31GiB
                capabilities: nofs
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                logical name: /home
                version: 1.0
                serial: 9da82c21-457a-427d-8298-2b3a97722fda
                size: 171GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-12-23 10:30:59 filesystem=ext4 lastmountpoint=/home modified=2015-12-23 11:17:06 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2015-12-23 11:17:06 state=mounted
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@1:14
       logical name: wlan0
       serial: c4:e9:84:dd:82:d7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu multicast=yes wireless=unassociated

```

and logs

[https://www.dropbox.com/s/b4nekla4fyeopcu/faillog?dl=0](https://www.dropbox.com/s/b4nekla4fyeopcu/faillog?dl=0)

[https://www.dropbox.com/s/ffxqe3ez3ak783z/kern.log?dl=0](https://www.dropbox.com/s/ffxqe3ez3ak783z/kern.log?dl=0)

[URL="https://www.dropbox.com/s/nkpxfz7k4apc891/syslog?dl=0"]https://www.dropbox.com/s/nkpxfz7k4apc891/syslog?dl=0

[/URL][https://www.dropbox.com/s/nkpxfz7k4apc891/syslog?dl=0](https://www.dropbox.com/s/nkpxfz7k4apc891/syslog?dl=0)

[https://www.dropbox.com/s/ewkm8qxx9fh2q0h/Screenshot%20from%202015-12-23%2014%3A01%3A55.png?dl=0](https://www.dropbox.com/s/ewkm8qxx9fh2q0h/Screenshot%20from%202015-12-23%2014%3A01%3A55.png?dl=0)

can anybody help me or say in what direction should I go ?

---

### Post by Bucky Ball on 2015-12-23
Welcome. Did you:

```
sudo apt-get update
sudo apt-get upgrade
```

? Might not achieve anything, but should be done.

Bit confused, sorry. You're saying Firefox crashes on any distribution and not just Ubuntu or that it only crashes in Ubuntu? If other distros run fine, it is not a problem with your hardware (but maybe Ubuntu is having a problem with your hardware, if you follow me).

Also, do you mean everything is fine until you open Firefox, then the system crashes?

PS: You have not installed 14.04.3. You are running 14.04.1. From your 'uname -a':

```
#48~14.04.1-Ubuntu
```

If you want to get to .3, you would run the two commands I gave above first (important) THEN run the third below:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Check for and report any issues you encounter along the way, if any. :)

---

### Post by Nugzar on 2015-12-23
Hi!) Thanks for replay!

I have freeze problem with debian too.
almost all programs crashes, it's not just FF problem.
Sorry for my English, my language is Russan.

I switched to main server ubuntu.com
and upgrade packages

I tried to copy output what updated from terminal, but it crashed

there were 6 modules, one of them was xorg-..., other I think not important

what will be the next step?

I do memtest 5-6 times and it's ok/

---

### Post by Bucky Ball on 2015-12-23
So it runs memtest. Did you let it run all the way? That takes awhile. Have you recently replaced or added RAM?

---

### Post by Nugzar on 2015-12-23
no, I haven't replace RAM, but it's new PC with new RAM and all other hardware
Yes it worked all night long

Should I update from 14.4.1 to 14.4.3 ?

---

### Post by mörgæs on 2015-12-23
Better to do a fresh install of 15.10. We have a number of threads dealing with old software on Haswell processors showing a variety of errors.

I don't see any indication that you have hardware problems, but semi-old software can't be expected to work with the latest hardware. 

See more at Phoronix, for example here:
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-HSW-Gfx](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-HSW-Gfx)

---

### Post by Nugzar on 2015-12-24
Ok, thanks for the answer.
I'll try to install 15.10 and then write here

---

### Post by Nugzar on 2015-12-24
Thanks for everybody! Problem resolved with installation of Ubuntu 15.10!

---

### Post by mörgæs on 2015-12-24
You're welcome. 

Please spread the word and help promote the latest releases of Buntu. Semi-old software should only be installed on old hardware (if it should be installed at all).

Maybe you could change the thread title to '**Installing on Intel Core i7 / Haswell**' or similar, since it's not about hardware problems.

---

### Post by Bucky Ball on 2015-12-24
> **mörgæs said:**
> Maybe you could change the thread title to '**Installing on Intel Core i7 / Haswell**' or similar, since it's not about hardware problems.

And if you want to do that, edit first post then 'Go Advanced'. You should be able to change the title from there. :)

Thanks for marking as solved. It helps.

---

### Post by mörgæs on 2015-12-25
- or could you please change it, Bucky?

---

### Post by Bucky Ball on 2015-12-25
Done. The name change will only show on the first post on the thread (and any after the change I think) but the new title will be reflected in searches and on the 'New Posts' page. :)

---

