---
title: "&quot;No se han podido activar los efectos de escritorio&quot;"
date: 2013-03-06
forum: Hardware
---

### Post by Clemenza08 on 2013-03-06
"No se han podido activar los efectos de escritorio" (Solucionado)

Me sale cuando le pongo "Extra" en los efectos visuales.

Esta es mi placa de video:

00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)


Tengo instalado Ubuntu 10.04 64 bit.


Y, por las dudas, esta es mi PC:

    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: H61M-DGS
       vendor: ASRock
       physical id: 0
       serial: M80-2B000501103
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.50 (09/07/2012)
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cache:0
          description: L2 cache
          physical id: 8
          slot: CPU Internal L2
          size: 512KiB
          capacity: 512KiB
          capabilities: internal write-through unified
     *-cache:1
          description: L1 cache
          physical id: 9
          slot: CPU Internal L1
          size: 128KiB
          capacity: 128KiB
          capabilities: internal write-through data
     *-cache:2
          description: L3 cache
          physical id: a
          slot: CPU Internal L3
          size: 3MiB
          capacity: 3MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [Empty]
             slot: ChannelA-DIMM0
        *-bank:1
             description: DIMM Synchronous 1067 MHz (0.9 ns)
             product: 99U5474-015.A00LF
             vendor: Kingston
             physical id: 1
             serial: 9D3480DC
             slot: ChannelB-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU G645 @ 2.90GHz
          vendor: Intel Corp.
          physical id: c
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU G645 @ 2.90GHz
          slot: CPUSocket
          size: 1600MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt xsave lahf_lm arat tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Sandy Bridge Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:f7800000-f7bfffff memory:e0000000-efffffff(prefetchable) ioport:f000(size=64)
        *-communication UNCLAIMED
             description: Communication controller
             product: Cougar Point HECI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f7c0a000-f7c0a00f
        *-usb:0
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f7c08000-f7c083ff
        *-multimedia
             description: Audio device
             product: Cougar Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f7c00000-f7c03fff
        *-pci:0
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24
        *-pci:1
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:e000(size=4096) memory:7eb00000-7ebfffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: bc:5f:f4:7c:7e:90
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.36 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:26 ioport:e000(size=256) memory:f0010000-f0010fff(prefetchable) memory:f0000000-f000ffff(prefetchable) memory:f0020000-f002ffff(prefetchable)
        *-usb:1
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7c07000-f7c073ff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Cougar Point 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi4
             logical name: scsi5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7c06000-f7c067ff
           *-disk
                description: ATA Disk
                product: ST500DM002-1BD14
                vendor: Seagate
                physical id: 0
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: KC45
                serial: Z3TD50YY
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=31b79867
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: cec1-d3a5
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2013-03-02 19:53:29 filesystem=ntfs label=Reservado para el sistema state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: b8621146-25b6-034e-9e55-8d29ef57aad9
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2013-03-02 19:53:45 filesystem=ntfs state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@4:0.0.0,3
                   logical name: /dev/sda3
                   size: 379GiB
                   capacity: 379GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 372GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 7320MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-224BB
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: Cougar Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7c05000-f7c050ff ioport:f040(size=32)

No sé muy bien dónde buscar la solución. Una ayudita por favor.

---

### Post by guillermolisi on 2013-03-07
La causa esta en que la placa de video no esta siendo bien reconocida y la asignacion del driver no es correcta:
> [COLOR=#000000]*-display UNCLAIMED[/COLOR]
[COLOR=#000000]description: VGA compatible controller[/COLOR]
[COLOR=#000000]product: Sandy Bridge Integrated Graphics Controller[/COLOR]
[COLOR=#000000]vendor: Intel Corporation[/COLOR]
[COLOR=#000000]physical id: 2[/COLOR]
[COLOR=#000000]bus info: pci@0000:00:02.0[/COLOR]
[COLOR=#000000]version: 09[/COLOR]
[COLOR=#000000]width: 64 bits[/COLOR]
[COLOR=#000000]clock: 33MHz[/COLOR]
[COLOR=#000000]capabilities: msi pm bus_master cap_list[/COLOR]
[COLOR=#000000]configuration: latency=0[/COLOR]
[COLOR=#000000]resources: memory:f7800000-f7bfffff memory:e0000000-efffffff(prefetchable) ioport:f000(size=64)[/COLOR]
UNCLAIMED esta indicando lo que menciono y por eso los efectos con aceleracion grafica no se pueden activar correctamente.

Por otro lado, alguna razon para seguir usando la 10.04 en lugar de la 12.04 ?

---

### Post by Clemenza08 on 2013-03-07
**Joya ¿y alguna solución posible? O dónde consigo el/los drivers para que todo funcione.**

Uso el  10.04 porque no me termina de convencer el "nuevo" escritorio, prefiero el gnome 2, y no me pinta mucho como queda el 12.04 con el gnome 2.

---

### Post by guillermolisi on 2013-03-07
Los drivers ya los tenes. El problema esta en el reconocimiento de la placa de video que es lo que imposibilita la asignacion del driver de video adecuado.

Para ver cual es la solucion hay que profundizar en la falla.
En el log del Xserver, /var/log/xorg.0.log, hay que investigar. Si queres postealo y lo vemos.

---

### Post by Clemenza08 on 2013-03-07
el xorg.0.log dice esto:


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-30-server x86_64 Ubuntu
Current Operating System: Linux orangutan-desktop 2.6.32-45-generic #104-Ubuntu SMP Tue Feb 19 21:20:09 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-45-generic root=UUID=593e5e54-b59a-4c1c-8c7d-287ec810ac21 ro vga=773 quiet splash
Build Date: 25 February 2012  06:57:33AM
xorg-server 2:1.7.6-2ubuntu7.11 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar  7 21:43:47 2013
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0102:1849:0102 Intel Corporation Sandy Bridge Integrated Graphics Controller rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.15.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262080 kB
(II) VESA(0): VESA VBE OEM: Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R) Sandybridge/Ivybridge Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SAM  Model: 8a8  Serial#: 861418032
(II) VESA(0): Year: 2011  Week: 39
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
(II) VESA(0): Max Image Size [cm]: horiz.: 44  vert.: 25
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.639 redY: 0.340   greenX: 0.324 greenY: 0.622
(II) VESA(0): blueX: 0.155 blueY: 0.042   whiteX: 0.312 whiteY: 0.329
(II) VESA(0): Supported established timings:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1152x864@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported standard timings:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) VESA(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 108.0 MHz   Image Size:  443 x 249 mm
(II) VESA(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
(II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 150 MHz
(II) VESA(0): Monitor name: S20B300
(II) VESA(0): Serial No: H1AK500000
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff004c2da80830325833
(II) VESA(0): 	271501030e2c19782a81f1a357539f27
(II) VESA(0): 	0a5054bfee80714f81c081009500950f
(II) VESA(0): 	010101010101302a40c8608464301850
(II) VESA(0): 	1300bbf91000001e000000fd00384b1e
(II) VESA(0): 	510f000a202020202020000000fc0053
(II) VESA(0): 	3230423330300a2020202020000000ff
(II) VESA(0): 	004831414b3530303030300a202000f8
(II) VESA(0): EDID vendor "SAM", prod id 2216
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 161 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 162 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 163 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 164 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 165 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 166 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 167 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 168 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 169 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16e (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16f (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 170 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 171 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13c (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 94
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1920
	BnkNumberOfImagePages: 94
	LinNumberOfImagePages: 94
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 14d (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 47
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 47
	LinNumberOfImagePages: 47
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 15c (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 23
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 23
	LinNumberOfImagePages: 23
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 13a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 135
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 135
	LinNumberOfImagePages: 135
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 14b (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 68
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 68
	LinNumberOfImagePages: 68
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 15a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 33
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 33
	LinNumberOfImagePages: 33
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 107 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 203
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 203
	LinNumberOfImagePages: 203
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 11a (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 101
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 101
	LinNumberOfImagePages: 101
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 11b (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 105 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 169
	LinNumberOfImagePages: 169
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 214
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 214
	LinNumberOfImagePages: 214
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 135
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 135
	LinNumberOfImagePages: 135
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 101 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 103 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 254
	LinNumberOfImagePages: 254
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 152
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 152
	LinNumberOfImagePages: 152
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 17d (1600x900)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 900
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 185
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 185
	LinNumberOfImagePages: 185
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 17e (1600x900)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 900
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 92
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 92
	LinNumberOfImagePages: 92
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 17f (1600x900)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00084c1
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 900
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 45
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 45
	LinNumberOfImagePages: 45
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 4095 64KB banks (262080kB)
(II) VESA(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): <default monitor>: Using maximum pixel clock of 150.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1600x900 (pitch 1600)
(**) VESA(0): *Built-in mode "1600x900"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (440, 250) mm
(**) VESA(0): DPI set to (92, 91)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262080 kB
(II) VESA(0): VESA VBE OEM: Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R) Sandybridge/Ivybridge Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7f745652f000,
	physical address = 0xe0000000, size = 268369920
(II) VESA(0): Setting up VESA Mode 0x17F (1600x900)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) XKB: reuse xkmfile /var/lib/xkb/server-188C20793BE00CBD61865C180F610EC4A3A6D8CD.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)


Un poco largo.

Che, desde ya muchísimas gracias por la predisposición, el tiempo y la ayuda... Supongo que de eso se trata Ubuntu: de unos para otros.

---

### Post by Clemenza08 on 2013-03-08
el xorg.0.log dice esto:


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-30-server x86_64 Ubuntu
Current Operating System: Linux orangutan-desktop 2.6.32-45-generic #104-Ubuntu SMP Tue Feb 19 21:20:09 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-45-generic root=UUID=593e5e54-b59a-4c1c-8c7d-287ec810ac21 ro vga=773 quiet splash
Build Date: 25 February 2012 06:57:33AM
xorg-server 2:1.7.6-2ubuntu7.11 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.16.4
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 7 21:43:47 2013
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section. Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) | |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Entry deleted from font path.
(==) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/Type1,
/usr/share/fonts/X11/100dpi,
/usr/share/fonts/X11/75dpi,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
X.Org ANSI C Emulation: 0.4
X.Org Video Driver: 6.0
X.Org XInput driver : 7.0
X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0102:1849:0102 Intel Corporation Sandy Bridge Integrated Graphics Controller rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.13.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.1.0
ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 2.15.0
Module class: X.Org Video Driver
ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 2.3.0
Module class: X.Org Video Driver
ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 0.4.1
ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 0.0.2
ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.1.0
ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262080 kB
(II) VESA(0): VESA VBE OEM: Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R) Sandybridge/Ivybridge Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
"Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SAM Model: 8a8 Serial#: 861418032
(II) VESA(0): Year: 2011 Week: 39
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input, Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync: Separate Composite SyncOnGreen
(II) VESA(0): Max Image Size [cm]: horiz.: 44 vert.: 25
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.639 redY: 0.340 greenX: 0.324 greenY: 0.622
(II) VESA(0): blueX: 0.155 blueY: 0.042 whiteX: 0.312 whiteY: 0.329
(II) VESA(0): Supported established timings:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1152x864@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported standard timings:
(II) VESA(0): #0: hsize: 1152 vsize 864 refresh: 75 vid: 20337
(II) VESA(0): #1: hsize: 1280 vsize 720 refresh: 60 vid: 49281
(II) VESA(0): #2: hsize: 1280 vsize 800 refresh: 60 vid: 129
(II) VESA(0): #3: hsize: 1440 vsize 900 refresh: 60 vid: 149
(II) VESA(0): #4: hsize: 1440 vsize 900 refresh: 75 vid: 3989
(II) VESA(0): Supported detailed timing:
(II) VESA(0): clock: 108.0 MHz Image Size: 443 x 249 mm
(II) VESA(0): h_active: 1600 h_sync: 1624 h_sync_end 1704 h_blank_end 1800 h_border: 0
(II) VESA(0): v_active: 900 v_sync: 901 v_sync_end 904 v_blanking: 1000 v_border: 0
(II) VESA(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 150 MHz
(II) VESA(0): Monitor name: S20B300
(II) VESA(0): Serial No: H1AK500000
(II) VESA(0): EDID (in hex):
(II) VESA(0): 00ffffffffffff004c2da80830325833
(II) VESA(0): 271501030e2c19782a81f1a357539f27
(II) VESA(0): 0a5054bfee80714f81c081009500950f
(II) VESA(0): 010101010101302a40c8608464301850
(II) VESA(0): 1300bbf91000001e000000fd00384b1e
(II) VESA(0): 510f000a202020202020000000fc0053
(II) VESA(0): 3230423330300a2020202020000000ff
(II) VESA(0): 004831414b3530303030300a202000f8
(II) VESA(0): EDID vendor "SAM", prod id 2216
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1600x900"x0.0 108.00 1600 1624 1704 1800 900 901 904 1000 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0 36.00 800 824 896 1024 600 601 603 625 +hsync +vsync (35.2 kHz)
(II) VESA(0): Modeline "640x480"x0.0 31.50 640 656 720 840 480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0 31.50 640 664 704 832 480 489 492 520 -hsync -vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0 30.24 640 704 768 864 480 483 486 525 -hsync -vsync (35.0 kHz)
(II) VESA(0): Modeline "640x480"x0.0 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0 28.32 720 738 846 900 400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0 78.75 1024 1040 1136 1312 768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0 75.00 1024 1048 1184 1328 768 771 777 806 -hsync -vsync (56.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "832x624"x0.0 57.28 832 864 928 1152 624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VESA(0): Modeline "800x600"x0.0 49.50 800 816 896 1056 600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0 50.00 800 856 976 1040 600 637 643 666 +hsync +vsync (48.1 kHz)
(II) VESA(0): Modeline "1152x864"x0.0 108.00 1152 1216 1344 1600 864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1280x720"x60.0 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync (44.8 kHz)
(II) VESA(0): Modeline "1280x800"x0.0 83.50 1280 1352 1480 1680 800 803 809 831 -hsync +vsync (49.7 kHz)
(II) VESA(0): Modeline "1440x900"x0.0 106.50 1440 1520 1672 1904 900 903 909 934 -hsync +vsync (55.9 kHz)
(II) VESA(0): Modeline "1440x900"x0.0 136.75 1440 1536 1688 1936 900 903 909 942 -hsync +vsync (70.6 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 161 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 162 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 163 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 164 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 165 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 166 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 167 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 168 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 169 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 16a (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 16b (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 16c (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 16d (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 16e (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 16f (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 170 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 171 (0x0)
ModeAttributes: 0x0
WinAAttributes: 0x0
WinBAttributes: 0x0
WinGranularity: 0
WinSize: 0
WinASegment: 0x0
WinBSegment: 0x0
WinFuncPtr: 0x0
BytesPerScanline: 0
XResolution: 0
YResolution: 0
XCharSize: 0
YCharSize: 0
NumberOfPlanes: 0
BitsPerPixel: 0
NumberOfBanks: 0
MemoryModel: 0
BankSize: 0
NumberOfImages: 0
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0x0
LinBytesPerScanLine: 0
BnkNumberOfImagePages: 0
LinNumberOfImagePages: 0
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 13c (1920x1440)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 1920
XResolution: 1920
YResolution: 1440
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 8
NumberOfBanks: 1
MemoryModel: 4
BankSize: 0
NumberOfImages: 94
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 1920
BnkNumberOfImagePages: 94
LinNumberOfImagePages: 94
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
Mode: 14d (1920x1440)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 3840
XResolution: 1920
YResolution: 1440
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 16
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 47
RedMaskSize: 5
RedFieldPosition: 11
GreenMaskSize: 6
GreenFieldPosition: 5
BlueMaskSize: 5
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 3840
BnkNumberOfImagePages: 47
LinNumberOfImagePages: 47
LinRedMaskSize: 5
LinRedFieldPosition: 11
LinGreenMaskSize: 6
LinGreenFieldPosition: 5
LinBlueMaskSize: 5
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
*Mode: 15c (1920x1440)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 7680
XResolution: 1920
YResolution: 1440
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 32
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 23
RedMaskSize: 8
RedFieldPosition: 16
GreenMaskSize: 8
GreenFieldPosition: 8
BlueMaskSize: 8
BlueFieldPosition: 0
RsvdMaskSize: 8
RsvdFieldPosition: 24
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 7680
BnkNumberOfImagePages: 23
LinNumberOfImagePages: 23
LinRedMaskSize: 8
LinRedFieldPosition: 16
LinGreenMaskSize: 8
LinGreenFieldPosition: 8
LinBlueMaskSize: 8
LinBlueFieldPosition: 0
LinRsvdMaskSize: 8
LinRsvdFieldPosition: 24
MaxPixelClock: 230000000
Mode: 13a (1600x1200)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 1600
XResolution: 1600
YResolution: 1200
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 8
NumberOfBanks: 1
MemoryModel: 4
BankSize: 0
NumberOfImages: 135
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 1600
BnkNumberOfImagePages: 135
LinNumberOfImagePages: 135
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
Mode: 14b (1600x1200)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 3200
XResolution: 1600
YResolution: 1200
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 16
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 68
RedMaskSize: 5
RedFieldPosition: 11
GreenMaskSize: 6
GreenFieldPosition: 5
BlueMaskSize: 5
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 3200
BnkNumberOfImagePages: 68
LinNumberOfImagePages: 68
LinRedMaskSize: 5
LinRedFieldPosition: 11
LinGreenMaskSize: 6
LinGreenFieldPosition: 5
LinBlueMaskSize: 5
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
*Mode: 15a (1600x1200)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 6400
XResolution: 1600
YResolution: 1200
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 32
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 33
RedMaskSize: 8
RedFieldPosition: 16
GreenMaskSize: 8
GreenFieldPosition: 8
BlueMaskSize: 8
BlueFieldPosition: 0
RsvdMaskSize: 8
RsvdFieldPosition: 24
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 6400
BnkNumberOfImagePages: 33
LinNumberOfImagePages: 33
LinRedMaskSize: 8
LinRedFieldPosition: 16
LinGreenMaskSize: 8
LinGreenFieldPosition: 8
LinBlueMaskSize: 8
LinBlueFieldPosition: 0
LinRsvdMaskSize: 8
LinRsvdFieldPosition: 24
MaxPixelClock: 230000000
Mode: 107 (1280x1024)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 1280
XResolution: 1280
YResolution: 1024
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 8
NumberOfBanks: 1
MemoryModel: 4
BankSize: 0
NumberOfImages: 203
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 1280
BnkNumberOfImagePages: 203
LinNumberOfImagePages: 203
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
Mode: 11a (1280x1024)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 2560
XResolution: 1280
YResolution: 1024
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 16
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 101
RedMaskSize: 5
RedFieldPosition: 11
GreenMaskSize: 6
GreenFieldPosition: 5
BlueMaskSize: 5
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 2560
BnkNumberOfImagePages: 101
LinNumberOfImagePages: 101
LinRedMaskSize: 5
LinRedFieldPosition: 11
LinGreenMaskSize: 6
LinGreenFieldPosition: 5
LinBlueMaskSize: 5
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
*Mode: 11b (1280x1024)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 5120
XResolution: 1280
YResolution: 1024
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 32
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 50
RedMaskSize: 8
RedFieldPosition: 16
GreenMaskSize: 8
GreenFieldPosition: 8
BlueMaskSize: 8
BlueFieldPosition: 0
RsvdMaskSize: 8
RsvdFieldPosition: 24
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 5120
BnkNumberOfImagePages: 50
LinNumberOfImagePages: 50
LinRedMaskSize: 8
LinRedFieldPosition: 16
LinGreenMaskSize: 8
LinGreenFieldPosition: 8
LinBlueMaskSize: 8
LinBlueFieldPosition: 0
LinRsvdMaskSize: 8
LinRsvdFieldPosition: 24
MaxPixelClock: 230000000
Mode: 105 (1024x768)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 1024
XResolution: 1024
YResolution: 768
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 8
NumberOfBanks: 1
MemoryModel: 4
BankSize: 0
NumberOfImages: 84
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 1024
BnkNumberOfImagePages: 84
LinNumberOfImagePages: 84
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
Mode: 117 (1024x768)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 2048
XResolution: 1024
YResolution: 768
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 16
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 169
RedMaskSize: 5
RedFieldPosition: 11
GreenMaskSize: 6
GreenFieldPosition: 5
BlueMaskSize: 5
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 2048
BnkNumberOfImagePages: 169
LinNumberOfImagePages: 169
LinRedMaskSize: 5
LinRedFieldPosition: 11
LinGreenMaskSize: 6
LinGreenFieldPosition: 5
LinBlueMaskSize: 5
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
*Mode: 118 (1024x768)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 4096
XResolution: 1024
YResolution: 768
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 32
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 84
RedMaskSize: 8
RedFieldPosition: 16
GreenMaskSize: 8
GreenFieldPosition: 8
BlueMaskSize: 8
BlueFieldPosition: 0
RsvdMaskSize: 8
RsvdFieldPosition: 24
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 4096
BnkNumberOfImagePages: 84
LinNumberOfImagePages: 84
LinRedMaskSize: 8
LinRedFieldPosition: 16
LinGreenMaskSize: 8
LinGreenFieldPosition: 8
LinBlueMaskSize: 8
LinBlueFieldPosition: 0
LinRsvdMaskSize: 8
LinRsvdFieldPosition: 24
MaxPixelClock: 230000000
*Mode: 112 (640x480)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 2560
XResolution: 640
YResolution: 480
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 32
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 214
RedMaskSize: 8
RedFieldPosition: 16
GreenMaskSize: 8
GreenFieldPosition: 8
BlueMaskSize: 8
BlueFieldPosition: 0
RsvdMaskSize: 8
RsvdFieldPosition: 24
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 2560
BnkNumberOfImagePages: 214
LinNumberOfImagePages: 214
LinRedMaskSize: 8
LinRedFieldPosition: 16
LinGreenMaskSize: 8
LinGreenFieldPosition: 8
LinBlueMaskSize: 8
LinBlueFieldPosition: 0
LinRsvdMaskSize: 8
LinRsvdFieldPosition: 24
MaxPixelClock: 230000000
Mode: 114 (800x600)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 1600
XResolution: 800
YResolution: 600
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 16
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 16
RedMaskSize: 5
RedFieldPosition: 11
GreenMaskSize: 6
GreenFieldPosition: 5
BlueMaskSize: 5
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 1600
BnkNumberOfImagePages: 16
LinNumberOfImagePages: 16
LinRedMaskSize: 5
LinRedFieldPosition: 11
LinGreenMaskSize: 6
LinGreenFieldPosition: 5
LinBlueMaskSize: 5
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
*Mode: 115 (800x600)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 3200
XResolution: 800
YResolution: 600
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 32
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 135
RedMaskSize: 8
RedFieldPosition: 16
GreenMaskSize: 8
GreenFieldPosition: 8
BlueMaskSize: 8
BlueFieldPosition: 0
RsvdMaskSize: 8
RsvdFieldPosition: 24
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 3200
BnkNumberOfImagePages: 135
LinNumberOfImagePages: 135
LinRedMaskSize: 8
LinRedFieldPosition: 16
LinGreenMaskSize: 8
LinGreenFieldPosition: 8
LinBlueMaskSize: 8
LinBlueFieldPosition: 0
LinRsvdMaskSize: 8
LinRsvdFieldPosition: 24
MaxPixelClock: 230000000
Mode: 101 (640x480)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 640
XResolution: 640
YResolution: 480
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 8
NumberOfBanks: 1
MemoryModel: 4
BankSize: 0
NumberOfImages: 50
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 640
BnkNumberOfImagePages: 50
LinNumberOfImagePages: 50
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
Mode: 103 (800x600)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 832
XResolution: 800
YResolution: 600
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 8
NumberOfBanks: 1
MemoryModel: 4
BankSize: 0
NumberOfImages: 254
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 832
BnkNumberOfImagePages: 254
LinNumberOfImagePages: 254
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
Mode: 111 (640x480)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 1280
XResolution: 640
YResolution: 480
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 16
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 152
RedMaskSize: 5
RedFieldPosition: 11
GreenMaskSize: 6
GreenFieldPosition: 5
BlueMaskSize: 5
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 1280
BnkNumberOfImagePages: 152
LinNumberOfImagePages: 152
LinRedMaskSize: 5
LinRedFieldPosition: 11
LinGreenMaskSize: 6
LinGreenFieldPosition: 5
LinBlueMaskSize: 5
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
Mode: 17d (1600x900)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 1600
XResolution: 1600
YResolution: 900
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 8
NumberOfBanks: 1
MemoryModel: 4
BankSize: 0
NumberOfImages: 185
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 1600
BnkNumberOfImagePages: 185
LinNumberOfImagePages: 185
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
Mode: 17e (1600x900)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 3200
XResolution: 1600
YResolution: 900
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 16
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 92
RedMaskSize: 5
RedFieldPosition: 11
GreenMaskSize: 6
GreenFieldPosition: 5
BlueMaskSize: 5
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 3200
BnkNumberOfImagePages: 92
LinNumberOfImagePages: 92
LinRedMaskSize: 5
LinRedFieldPosition: 11
LinGreenMaskSize: 6
LinGreenFieldPosition: 5
LinBlueMaskSize: 5
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 230000000
*Mode: 17f (1600x900)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0x0
WinFuncPtr: 0xc00084c1
BytesPerScanline: 6400
XResolution: 1600
YResolution: 900
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 32
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 45
RedMaskSize: 8
RedFieldPosition: 16
GreenMaskSize: 8
GreenFieldPosition: 8
BlueMaskSize: 8
BlueFieldPosition: 0
RsvdMaskSize: 8
RsvdFieldPosition: 24
DirectColorModeInfo: 0
PhysBasePtr: 0xe0000000
LinBytesPerScanLine: 6400
BnkNumberOfImagePages: 45
LinNumberOfImagePages: 45
LinRedMaskSize: 8
LinRedFieldPosition: 16
LinGreenMaskSize: 8
LinGreenFieldPosition: 8
LinBlueMaskSize: 8
LinBlueFieldPosition: 0
LinRsvdMaskSize: 8
LinRsvdFieldPosition: 24
MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 4095 64KB banks (262080kB)
(II) VESA(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): <default monitor>: Using maximum pixel clock of 150.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
(II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(--) VESA(0): Virtual size is 1600x900 (pitch 1600)
(**) VESA(0): *Built-in mode "1600x900"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (440, 250) mm
(**) VESA(0): DPI set to (92, 91)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.1.0
ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 1.0.0
ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262080 kB
(II) VESA(0): VESA VBE OEM: Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R) Sandybridge/Ivybridge Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): virtual address = 0x7f745652f000,
physical address = 0xe0000000, size = 268369920
(II) VESA(0): Setting up VESA Mode 0x17F (1600x900)
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(==) VESA(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
compiled for 1.7.6, module version = 2.3.2
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) XKB: reuse xkmfile /var/lib/xkb/server-188C20793BE00CBD61865C180F610EC4A3A6D8CD.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "es"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)


Un poco largo.

Che, desde ya muchísimas gracias por la predisposición, el tiempo y la ayuda... Supongo que de eso se trata Ubuntu: de unos para otros.

---

### Post by guillermolisi on 2013-03-08
Salvo un par de Warnings, no veo problemas en como detecta y trabaja el Xserver. Utiliza y reconoce perfectamente bien tanto la placa de video Intel como su memoria y monitor (Samsung).

En base a esto, instalaste Compiz para obtener los efectos que queres ?

---

### Post by Clemenza08 on 2013-04-05
Bueno, pasó un tiempo, pero lo solucioné.

Eh aquí el procedimiento:

Ya teniendo instalados el mesa util y el compiz, agregué los repositorios de los controladores de mi placa de video, de intel y optimicé mi kernel.

Los comandos fueron estos:

sudo add-apt-repository ppa:glasen/intel-driver
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty

Después todo funcionó de maravilla. Fue magnuflétido y floté en un mar de maravilla ubúntico.

Espero sirva para algunos con similar inconveniente y similar equipo.

---

### Post by guillermolisi on 2013-04-05
El repositorio ppa[COLOR=#000000]:glasen/intel-driver tiene varios paquetes actualizados a fines de Marzo de este año. Si bien esto pareceria ser menor, para las instalaciones LTS como la 10.04 no lo es, mas aun si no utilizan los repos backports.

Algo similar ocurre con [/COLOR][COLOR=#000000]ppa:kernel-ppa/ppa ya que de alguna forma reemplaza/complementa las imagenes y encabezados de versiones mas modernas del kernel cuando no se tiene activado el repositorio backports.

Felicitaciones y gracias por compartir la solucion ![/COLOR]

---

