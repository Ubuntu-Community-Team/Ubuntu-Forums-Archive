---
title: "KDE freezes after login (11.10, 64-bit)"
date: 2011-12-30
forum: Hardware
---

### Post by wieman01 on 2011-12-30
Hello, 

This has been a problem for a while now, but it has deteriorated to the point where I can't ignore it any longer. 

When I log on to KDE the desktop would show but the system would hang for about 2 minutes. I can move the cursor and even open programs through shortcuts, but the screen does not refresh. 

I suspect it has something to do with the video driver. So here is what I have got. Thanks for your help.

_**LSHW:**_
```
winnie                    
    description: Computer
    product: Aspire 1810TZ (Montevina_Fab)
    vendor: Acer
    version: v0.3115
    serial: LXPJ502064950080F02500
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal family=Intel_Mobile sku=Montevina_Fab uuid=CAA75EDC-205F-49B3-B080-F4754AC8D0C5
  *-core
       description: Motherboard
       product: Base Board Product Name
       vendor: Acer
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: v0.3115
          date: 08/14/2009
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           U4100  @ 1.30GHz
          vendor: Intel Corp.
          physical id: 16
          bus info: cpu@0
          version: Genuine Intel(R) CPU           U4100  @ 1.30GHz
          slot: CPU
          size: 1300MHz
          capacity: 1300MHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
        *-cache:0
             description: L2 cache
             physical id: 17
             slot: Unknown
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 19
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 18
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: EBE21UE8AFSA-8G-F
             vendor: 7F7FFE0000000000
             physical id: 0
             serial: 9D3B215A
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM [empty]
             physical id: 1
             slot: DIMM2
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:90000000-903fffff memory:80000000-8fffffff ioport:30d0(size=8)
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
             resources: memory:92400000-924fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:30a0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:94504c00-94504fff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:94500000-94503fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:93500000-944fffff ioport:90400000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8131 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: c0
                serial: 00:26:9e:ae:ff:e3
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:45 memory:93500000-9353ffff ioport:2000(size=128)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:92500000-934fffff ioport:91400000(size=16777216)
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1000
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 00:1e:64:3a:d3:90
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-14-generic firmware=39.31.5.1 build 35138 ip=192.168.168.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:44 memory:92500000-92501fff
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:3080(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3060(size=32)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3040(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:94504800-94504bff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller
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
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:30c8(size=8) ioport:30dc(size=4) ioport:30c0(size=8) ioport:30d8(size=4) ioport:3020(size=32) memory:94504000-945047ff
           *-disk
                description: ATA Disk
                product: SAMSUNG 470 Seri
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AXM0
                serial: S0SUNEAB501965
                size: 59GiB (64GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00052636
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 4684eefc-c442-48b2-8a65-67d17060ce98
                   size: 9536MiB
                   capacity: 9536MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-22 20:29:38 filesystem=ext4 lastmountpoint=/ modified=2011-12-28 17:50:20 mount.fstype=ext4 mount.options=rw,noatime,nodiratime,errors=remount-ro,user_xattr,acl,commit=600,barrier=1,data=ordered,discard mounted=2011-12-30 07:11:04 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 50GiB
                   capacity: 50GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 2861MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,commit=600,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 47GiB
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
             resources: memory:94505000-945050ff ioport:3000(size=32)
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define4
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define5
       serial: OEM_Define2
       capacity: 75mWh
```

_**Xorg:**_
```
[  4579.327] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  4579.327] X Protocol Version 11, Revision 0
[  4579.327] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[  4579.327] Current Operating System: Linux Winnie 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
[  4579.327] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=4684eefc-c442-48b2-8a65-67d17060ce98 ro quiet splash vt.handoff=7
[  4579.327] Build Date: 19 October 2011  05:21:26AM
[  4579.327] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[  4579.327] Current version of pixman: 0.22.2
[  4579.330] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  4579.330] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  4579.331] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 30 08:27:18 2011
[  4579.331] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  4579.331] (==) No Layout section.  Using the first Screen section.
[  4579.331] (==) No screen section available. Using defaults.
[  4579.331] (**) |-->Screen "Default Screen Section" (0)
[  4579.331] (**) |   |-->Monitor "<default monitor>"
[  4579.332] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  4579.332] (==) Automatically adding devices
[  4579.332] (==) Automatically enabling devices
[  4579.332] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  4579.332] 	Entry deleted from font path.
[  4579.332] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  4579.332] 	Entry deleted from font path.
[  4579.332] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  4579.332] 	Entry deleted from font path.
[  4579.332] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  4579.332] 	Entry deleted from font path.
[  4579.332] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  4579.332] 	Entry deleted from font path.
[  4579.332] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  4579.332] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  4579.332] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  4579.332] (II) Loader magic: 0x7e0220
[  4579.332] (II) Module ABI versions:
[  4579.332] 	X.Org ANSI C Emulation: 0.4
[  4579.332] 	X.Org Video Driver: 10.0
[  4579.332] 	X.Org XInput driver : 12.3
[  4579.332] 	X.Org Server Extension : 5.0
[  4579.334] (--) PCI:*(0:0:2:0) 8086:2a42:1025:029b rev 7, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x000030d0/8
[  4579.334] (--) PCI: (0:0:2:1) 8086:2a43:1025:029b rev 7, Mem @ 0x92400000/1048576
[  4579.334] (II) Open ACPI successful (/var/run/acpid.socket)
[  4579.334] (II) LoadModule: "extmod"
[  4579.335] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  4579.335] (II) Module extmod: vendor="X.Org Foundation"
[  4579.335] 	compiled for 1.10.4, module version = 1.0.0
[  4579.335] 	Module class: X.Org Server Extension
[  4579.335] 	ABI class: X.Org Server Extension, version 5.0
[  4579.335] (II) Loading extension MIT-SCREEN-SAVER
[  4579.335] (II) Loading extension XFree86-VidModeExtension
[  4579.335] (II) Loading extension XFree86-DGA
[  4579.335] (II) Loading extension DPMS
[  4579.335] (II) Loading extension XVideo
[  4579.335] (II) Loading extension XVideo-MotionCompensation
[  4579.335] (II) Loading extension X-Resource
[  4579.335] (II) LoadModule: "dbe"
[  4579.335] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  4579.335] (II) Module dbe: vendor="X.Org Foundation"
[  4579.335] 	compiled for 1.10.4, module version = 1.0.0
[  4579.335] 	Module class: X.Org Server Extension
[  4579.335] 	ABI class: X.Org Server Extension, version 5.0
[  4579.335] (II) Loading extension DOUBLE-BUFFER
[  4579.335] (II) LoadModule: "glx"
[  4579.336] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  4579.336] (II) Module glx: vendor="X.Org Foundation"
[  4579.336] 	compiled for 1.10.4, module version = 1.0.0
[  4579.336] 	ABI class: X.Org Server Extension, version 5.0
[  4579.336] (==) AIGLX enabled
[  4579.336] (II) Loading extension GLX
[  4579.336] (II) LoadModule: "record"
[  4579.336] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  4579.336] (II) Module record: vendor="X.Org Foundation"
[  4579.336] 	compiled for 1.10.4, module version = 1.13.0
[  4579.336] 	Module class: X.Org Server Extension
[  4579.336] 	ABI class: X.Org Server Extension, version 5.0
[  4579.336] (II) Loading extension RECORD
[  4579.336] (II) LoadModule: "dri"
[  4579.337] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  4579.337] (II) Module dri: vendor="X.Org Foundation"
[  4579.337] 	compiled for 1.10.4, module version = 1.0.0
[  4579.337] 	ABI class: X.Org Server Extension, version 5.0
[  4579.337] (II) Loading extension XFree86-DRI
[  4579.337] (II) LoadModule: "dri2"
[  4579.337] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  4579.337] (II) Module dri2: vendor="X.Org Foundation"
[  4579.337] 	compiled for 1.10.4, module version = 1.2.0
[  4579.337] 	ABI class: X.Org Server Extension, version 5.0
[  4579.337] (II) Loading extension DRI2
[  4579.337] (==) Matched intel as autoconfigured driver 0
[  4579.337] (==) Matched vesa as autoconfigured driver 1
[  4579.338] (==) Matched fbdev as autoconfigured driver 2
[  4579.338] (==) Assigned the driver to the xf86ConfigLayout
[  4579.338] (II) LoadModule: "intel"
[  4579.338] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  4579.338] (II) Module intel: vendor="X.Org Foundation"
[  4579.338] 	compiled for 1.10.4, module version = 2.15.901
[  4579.338] 	Module class: X.Org Video Driver
[  4579.338] 	ABI class: X.Org Video Driver, version 10.0
[  4579.338] (II) LoadModule: "vesa"
[  4579.339] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  4579.339] (II) Module vesa: vendor="X.Org Foundation"
[  4579.339] 	compiled for 1.10.2, module version = 2.3.0
[  4579.339] 	Module class: X.Org Video Driver
[  4579.339] 	ABI class: X.Org Video Driver, version 10.0
[  4579.339] (II) LoadModule: "fbdev"
[  4579.339] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  4579.345] (II) Module fbdev: vendor="X.Org Foundation"
[  4579.345] 	compiled for 1.10.0, module version = 0.4.2
[  4579.345] 	ABI class: X.Org Video Driver, version 10.0
[  4579.345] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[  4579.345] (II) VESA: driver for VESA chipsets: vesa
[  4579.345] (II) FBDEV: driver for framebuffer: fbdev
[  4579.345] (++) using VT number 7

[  4579.348] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  4579.348] (WW) Falling back to old probe method for vesa
[  4579.348] (WW) Falling back to old probe method for fbdev
[  4579.348] (II) Loading sub module "fbdevhw"
[  4579.348] (II) LoadModule: "fbdevhw"
[  4579.349] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  4579.349] (II) Module fbdevhw: vendor="X.Org Foundation"
[  4579.349] 	compiled for 1.10.4, module version = 0.0.2
[  4579.349] 	ABI class: X.Org Video Driver, version 10.0
[  4579.349] drmOpenDevice: node name is /dev/dri/card0
[  4579.349] drmOpenDevice: open result is 9, (OK)
[  4579.349] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[  4579.349] drmOpenDevice: node name is /dev/dri/card0
[  4579.349] drmOpenDevice: open result is 9, (OK)
[  4579.349] drmOpenByBusid: drmOpenMinor returns 9
[  4579.349] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  4579.349] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  4579.349] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  4579.349] (==) intel(0): RGB weight 888
[  4579.349] (==) intel(0): Default visual is TrueColor
[  4579.349] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[  4579.349] (--) intel(0): Chipset: "GM45"
[  4579.349] (**) intel(0): Relaxed fencing enabled
[  4579.349] (**) intel(0): Wait on SwapBuffers? enabled
[  4579.349] (**) intel(0): Triple buffering? enabled
[  4579.349] (**) intel(0): Framebuffer tiled
[  4579.349] (**) intel(0): Pixmaps tiled
[  4579.350] (**) intel(0): 3D buffers tiled
[  4579.350] (**) intel(0): SwapBuffers wait enabled
[  4579.350] (==) intel(0): video overlay key set to 0x101fe
[  4579.350] (II) intel(0): Output LVDS1 has no monitor section
[  4579.350] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[  4579.380] (II) intel(0): Output VGA1 has no monitor section
[  4579.410] (II) intel(0): Output HDMI1 has no monitor section
[  4579.411] (II) intel(0): Output DP1 has no monitor section
[  4579.449] (II) intel(0): Output HDMI2 has no monitor section
[  4579.450] (II) intel(0): Output DP2 has no monitor section
[  4579.451] (II) intel(0): Output DP3 has no monitor section
[  4579.451] (II) intel(0): EDID for output LVDS1
[  4579.451] (II) intel(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[  4579.451] (II) intel(0): Year: 2009  Week: 9
[  4579.451] (II) intel(0): EDID Version: 1.3
[  4579.451] (II) intel(0): Digital Display Input
[  4579.451] (II) intel(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[  4579.451] (II) intel(0): Gamma: 2.20
[  4579.451] (II) intel(0): No DPMS capabilities specified
[  4579.452] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  4579.452] (II) intel(0): First detailed timing is preferred mode
[  4579.452] (II) intel(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[  4579.452] (II) intel(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[  4579.452] (II) intel(0): Manufacturer's mask: 0
[  4579.452] (II) intel(0): Supported detailed timing:
[  4579.452] (II) intel(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[  4579.452] (II) intel(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[  4579.452] (II) intel(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[  4579.452] (II) intel(0):  N116B6-L02
[  4579.452] (II) intel(0):  CMO
[  4579.452] (II) intel(0):  N116B6-L02
[  4579.452] (II) intel(0): EDID (in hex):
[  4579.452] (II) intel(0): 	00ffffffffffff000daf001100000000
[  4579.452] (II) intel(0): 	0913010380190e780acf459059579529
[  4579.452] (II) intel(0): 	1f505400000001010101010101010101
[  4579.452] (II) intel(0): 	0101010101019c19562a50000830070e
[  4579.452] (II) intel(0): 	1300009010000018000000fe004e3131
[  4579.452] (II) intel(0): 	3642362d4c30320a2020000000fe0043
[  4579.452] (II) intel(0): 	4d4f0a202020202020202020000000fe
[  4579.452] (II) intel(0): 	004e31313642362d4c30320a20200065
[  4579.452] (II) intel(0): EDID vendor "CMO", prod id 4352
[  4579.452] (II) intel(0): Printing DDC gathered Modelines:
[  4579.452] (II) intel(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[  4579.452] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  4579.452] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  4579.453] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[  4579.453] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[  4579.453] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[  4579.453] (II) intel(0): Printing probed modes for output LVDS1
[  4579.453] (II) intel(0): Modeline "1366x768"x60.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[  4579.453] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[  4579.453] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[  4579.453] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  4579.453] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  4579.453] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  4579.453] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  4579.484] (II) intel(0): EDID for output VGA1
[  4579.512] (II) intel(0): EDID for output HDMI1
[  4579.512] (II) intel(0): EDID for output DP1
[  4579.532] (II) intel(0): EDID for output HDMI2
[  4579.533] (II) intel(0): EDID for output DP2
[  4579.534] (II) intel(0): EDID for output DP3
[  4579.534] (II) intel(0): Output LVDS1 connected
[  4579.534] (II) intel(0): Output VGA1 disconnected
[  4579.534] (II) intel(0): Output HDMI1 disconnected
[  4579.534] (II) intel(0): Output DP1 disconnected
[  4579.534] (II) intel(0): Output HDMI2 disconnected
[  4579.534] (II) intel(0): Output DP2 disconnected
[  4579.534] (II) intel(0): Output DP3 disconnected
[  4579.534] (II) intel(0): Using exact sizes for initial modes
[  4579.534] (II) intel(0): Output LVDS1 using initial mode 1366x768
[  4579.534] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  4579.534] (II) intel(0): Kernel page flipping support detected, enabling
[  4579.534] (**) intel(0): Display dimensions: (250, 140) mm
[  4579.534] (**) intel(0): DPI set to (138, 139)
[  4579.534] (II) Loading sub module "fb"
[  4579.534] (II) LoadModule: "fb"
[  4579.534] (II) Loading /usr/lib/xorg/modules/libfb.so
[  4579.535] (II) Module fb: vendor="X.Org Foundation"
[  4579.535] 	compiled for 1.10.4, module version = 1.0.0
[  4579.535] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  4579.535] (II) Loading sub module "dri2"
[  4579.535] (II) LoadModule: "dri2"
[  4579.535] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  4579.535] (II) Module dri2: vendor="X.Org Foundation"
[  4579.535] 	compiled for 1.10.4, module version = 1.2.0
[  4579.535] 	ABI class: X.Org Server Extension, version 5.0
[  4579.535] (II) UnloadModule: "vesa"
[  4579.535] (II) Unloading vesa
[  4579.535] (II) UnloadModule: "fbdev"
[  4579.535] (II) Unloading fbdev
[  4579.535] (II) UnloadModule: "fbdevhw"
[  4579.535] (II) Unloading fbdevhw
[  4579.535] (==) Depth 24 pixmap format is 32 bpp
[  4579.535] (II) intel(0): [DRI2] Setup complete
[  4579.535] (II) intel(0): [DRI2]   DRI driver: i965
[  4579.535] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[  4579.552] (II) UXA(0): Driver registered support for the following operations:
[  4579.552] (II)         solid
[  4579.552] (II)         copy
[  4579.552] (II)         composite (RENDER acceleration)
[  4579.552] (II)         put_image
[  4579.552] (II)         get_image
[  4579.552] (==) intel(0): Backing store disabled
[  4579.552] (==) intel(0): Silken mouse enabled
[  4579.552] (II) intel(0): Initializing HW Cursor
[  4579.590] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  4579.591] (==) intel(0): DPMS enabled
[  4579.591] (==) intel(0): Intel XvMC decoder enabled
[  4579.591] (II) intel(0): Set up textured video
[  4579.591] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[  4579.591] (II) intel(0): direct rendering: DRI2 Enabled
[  4579.591] (==) intel(0): hotplug detection: "enabled"
[  4579.591] (--) RandR disabled
[  4579.591] (II) Initializing built-in extension Generic Event Extension
[  4579.591] (II) Initializing built-in extension SHAPE
[  4579.591] (II) Initializing built-in extension MIT-SHM
[  4579.591] (II) Initializing built-in extension XInputExtension
[  4579.591] (II) Initializing built-in extension XTEST
[  4579.591] (II) Initializing built-in extension BIG-REQUESTS
[  4579.591] (II) Initializing built-in extension SYNC
[  4579.591] (II) Initializing built-in extension XKEYBOARD
[  4579.591] (II) Initializing built-in extension XC-MISC
[  4579.591] (II) Initializing built-in extension SECURITY
[  4579.591] (II) Initializing built-in extension XINERAMA
[  4579.591] (II) Initializing built-in extension XFIXES
[  4579.591] (II) Initializing built-in extension RENDER
[  4579.591] (II) Initializing built-in extension RANDR
[  4579.592] (II) Initializing built-in extension COMPOSITE
[  4579.592] (II) Initializing built-in extension DAMAGE
[  4579.592] (II) Initializing built-in extension GESTURE
[  4579.603] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
[  4579.612] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  4579.612] (II) AIGLX: enabled GLX_INTEL_swap_event
[  4579.612] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  4579.612] (II) AIGLX: enabled GLX_SGI_make_current_read
[  4579.612] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  4579.612] (II) AIGLX: Loaded and initialized i965
[  4579.612] (II) GLX: Initialized DRI2 GL provider for screen 0
[  4579.613] (II) intel(0): Setting screen physical size to 361 x 203
[  4579.643] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  4579.669] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[  4579.669] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  4579.669] (II) LoadModule: "evdev"
[  4579.669] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4579.670] (II) Module evdev: vendor="X.Org Foundation"
[  4579.670] 	compiled for 1.10.2, module version = 2.6.0
[  4579.670] 	Module class: X.Org XInput Driver
[  4579.670] 	ABI class: X.Org XInput driver, version 12.3
[  4579.670] (II) Using input driver 'evdev' for 'Power Button'
[  4579.670] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4579.670] (**) Power Button: always reports core events
[  4579.670] (**) Power Button: Device: "/dev/input/event3"
[  4579.671] (--) Power Button: Found keys
[  4579.671] (II) Power Button: Configuring as keyboard
[  4579.671] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[  4579.671] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  4579.671] (**) Option "xkb_rules" "evdev"
[  4579.671] (**) Option "xkb_model" "pc105"
[  4579.671] (**) Option "xkb_layout" "de"
[  4579.678] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[  4579.683] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[  4579.683] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  4579.683] (II) Using input driver 'evdev' for 'Video Bus'
[  4579.683] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4579.684] (**) Video Bus: always reports core events
[  4579.684] (**) Video Bus: Device: "/dev/input/event5"
[  4579.684] (--) Video Bus: Found keys
[  4579.684] (II) Video Bus: Configuring as keyboard
[  4579.684] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[  4579.684] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  4579.684] (**) Option "xkb_rules" "evdev"
[  4579.684] (**) Option "xkb_model" "pc105"
[  4579.684] (**) Option "xkb_layout" "de"
[  4579.692] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  4579.692] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  4579.692] (II) Using input driver 'evdev' for 'Power Button'
[  4579.692] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4579.693] (**) Power Button: always reports core events
[  4579.693] (**) Power Button: Device: "/dev/input/event0"
[  4579.693] (--) Power Button: Found keys
[  4579.693] (II) Power Button: Configuring as keyboard
[  4579.693] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  4579.693] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  4579.693] (**) Option "xkb_rules" "evdev"
[  4579.693] (**) Option "xkb_model" "pc105"
[  4579.693] (**) Option "xkb_layout" "de"
[  4579.694] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[  4579.694] (II) No input driver/identifier specified (ignoring)
[  4579.694] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[  4579.694] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  4579.694] (II) Using input driver 'evdev' for 'Sleep Button'
[  4579.694] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4579.694] (**) Sleep Button: always reports core events
[  4579.694] (**) Sleep Button: Device: "/dev/input/event2"
[  4579.694] (--) Sleep Button: Found keys
[  4579.694] (II) Sleep Button: Configuring as keyboard
[  4579.694] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[  4579.694] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  4579.694] (**) Option "xkb_rules" "evdev"
[  4579.695] (**) Option "xkb_model" "pc105"
[  4579.695] (**) Option "xkb_layout" "de"
[  4579.699] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event6)
[  4579.699] (II) No input driver/identifier specified (ignoring)
[  4579.699] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[  4579.699] (II) No input driver/identifier specified (ignoring)
[  4579.703] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
[  4579.703] (II) No input driver/identifier specified (ignoring)
[  4579.706] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event11)
[  4579.706] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[  4579.706] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[  4579.706] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4579.706] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[  4579.706] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event11"
[  4579.706] (--) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[  4579.706] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[  4579.706] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[  4579.706] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[  4579.706] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[  4579.706] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[  4579.706] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[  4579.706] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  4579.706] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb4/4-2/4-2:1.0/input/input11/event11"
[  4579.706] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[  4579.706] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[  4579.706] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[  4579.706] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[  4579.707] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[  4579.707] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[  4579.707] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse1)
[  4579.707] (II) No input driver/identifier specified (ignoring)
[  4579.709] (II) config/udev: Adding input device WebCam (/dev/input/event9)
[  4579.709] (**) WebCam: Applying InputClass "evdev keyboard catchall"
[  4579.709] (II) Using input driver 'evdev' for 'WebCam'
[  4579.709] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4579.709] (**) WebCam: always reports core events
[  4579.709] (**) WebCam: Device: "/dev/input/event9"
[  4579.709] (--) WebCam: Found keys
[  4579.709] (II) WebCam: Configuring as keyboard
[  4579.709] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9/event9"
[  4579.709] (II) XINPUT: Adding extended input device "WebCam" (type: KEYBOARD)
[  4579.709] (**) Option "xkb_rules" "evdev"
[  4579.709] (**) Option "xkb_model" "pc105"
[  4579.709] (**) Option "xkb_layout" "de"
[  4579.719] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[  4579.719] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  4579.719] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  4579.719] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4579.719] (**) AT Translated Set 2 keyboard: always reports core events
[  4579.719] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[  4579.719] (--) AT Translated Set 2 keyboard: Found keys
[  4579.719] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  4579.719] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[  4579.719] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  4579.719] (**) Option "xkb_rules" "evdev"
[  4579.719] (**) Option "xkb_model" "pc105"
[  4579.719] (**) Option "xkb_layout" "de"
[  4579.720] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[  4579.721] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  4579.721] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  4579.721] (II) LoadModule: "synaptics"
[  4579.721] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  4579.721] (II) Module synaptics: vendor="X.Org Foundation"
[  4579.721] 	compiled for 1.10.4, module version = 1.4.1
[  4579.721] 	Module class: X.Org XInput Driver
[  4579.721] 	ABI class: X.Org XInput driver, version 12.3
[  4579.721] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  4579.721] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  4579.721] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  4579.721] (**) Option "Device" "/dev/input/event10"
[  4579.752] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5888
[  4579.752] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5012
[  4579.752] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  4579.752] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  4579.752] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  4579.772] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  4579.772] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  4579.796] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event10"
[  4579.796] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  4579.796] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  4579.796] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  4579.796] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.035
[  4579.796] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  4579.796] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  4579.796] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  4579.796] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  4579.797] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  4579.798] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  4579.798] (II) No input driver/identifier specified (ignoring)
[  4583.860] (II) XKB: reuse xkmfile /var/lib/xkb/server-A854226913527907A36C4D2DAF9AFA87EAB7AF64.xkm
[  4595.129] (II) intel(0): EDID vendor "CMO", prod id 4352
[  4595.129] (II) intel(0): Printing DDC gathered Modelines:
[  4595.129] (II) intel(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)

```

---

### Post by wieman01 on 2012-01-01
Solution was to remove my entire profile and create a new user. No more issues since then.

---

