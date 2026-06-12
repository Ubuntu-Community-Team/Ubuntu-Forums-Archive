---
title: "Problemas con placa Intel"
date: 2009-05-26
forum: Hardware
---

### Post by LucasXIIHK on 2009-05-26
Luego de un topic conflictivo pero divertido y aclarador, aquí estoy con duda de soporte técnico....

Instalé con actualización web el Ubuntu 9.04 y repentinamente me quedé sin efectos de escritorio. Mi pregunta entonces es:
¿Como hago para activar los efectos de escritorio que funcionaban perfectamente en 8.04 y 8.10?

Probé editando el xorg.conf y el compiz desde terminal y nada ....
Probé con drivers de terceros de intel .... nada .....

¿Alguno sabe como hacer para normalizar el compiz o llevarlo a las configuraciones del 8.04 o el 8.10?

Por cierto tengo una Notebook Acer Aspire 5315 con chip Intel (esto último bastante obvio por el título del topic)

Desde ya, muchas gracias por el tiempo que dediquen a este problema ^_^

---

### Post by emiliano_raso on 2009-05-27
Otra vez?

Porque no lo banean? xD

EDIT: La solucion es Windows. En Windows TODO es mas facil. Usá Windows.

---

### Post by anarko on 2009-05-27
[www.google.com](www.google.com) 
Busqueda : Acer Aspire 5315 compiz
[1] Aca una posible solucion
Segun dicen esta blacklisted por los creadores de compiz.

[1] [http://ubuntuforums.org/showthread.php?t=610603](http://ubuntuforums.org/showthread.php?t=610603)

---

### Post by LucasXIIHK on 2009-05-27
> **anarko said:**
> [www.google.com]("http://www.google.com") 
Busqueda : Acer Aspire 5315 compiz
[1] Aca una posible solucion
Segun dicen esta blacklisted por los creadores de compiz.

[1] [http://ubuntuforums.org/showthread.php?t=610603](http://ubuntuforums.org/showthread.php?t=610603)

Mil gracias Anarko, espero que funcione ^^

---

### Post by staar on 2009-05-27
y porque el Señor Programador de Software Privativo no es capaz de crear un thread en la categoría correspondiente del foro? esto es problema de hardware, va en el subforo Hardware...

o tanta teoría te obnubiló la vista y la capacidad de lectura comprensiva?

menos PC y más vida real para Ud., Señor Troll...

---

### Post by rubioo on 2009-05-27
Esto no tiene que ir en Hardware?

      Saludos

---

### Post by rubioo on 2009-05-27
staar me ganaste de mano (por ir al baño).

---

### Post by LucasXIIHK on 2009-05-27
> **staar said:**
> y porque el Señor Programador de Software Privativo no es capaz de crear un thread en la categoría correspondiente del foro? esto es problema de hardware, va en el subforo Hardware...

o tanta teoría te obnubiló la vista y la capacidad de lectura comprensiva?

menos PC y más vida real para Ud., Señor Troll...
y porque el Señor Usuario de Software Libre no es capaz de notar que cuando uno es nuevo en una comunidad no se ubica de una? esto es un problema de tolerancia, debería reveerlo....

o tanto p*********o le nubló la vista y no nota estas cosas?

menos violencia y más inteligencia señor bruto.....



 Ahí estoy reiniciando para probar la solución, si sigue presentando problemas aviso ^^

---

### Post by rubioo on 2009-05-27
Eeee, esta bien que tengan opiniones diferentes. Pero se puede discutir todo, hablando
 bien y con respeto.
 Tampoco es para que se arme una foro-novela

---

### Post by eldragon on 2009-05-27
> **LucasXIIHK said:**
> 
 Ahí estoy reiniciando para probar la solución, si sigue presentando problemas aviso ^^


para tratar de debugear esto, mejor seria que postees un Xorg.0.log y un lspci para ver que modelo de placa tenes.

---

### Post by LucasXIIHK on 2009-05-27
> **rubioo said:**
> Eeee, esta bien que tengan opiniones diferentes. Pero se puede discutir todo, hablando
 bien y con respeto.
 Tampoco es para que se arme una foro-novela
Me mataste con lo de foro-novela XDDDD ...... todavía me estoy riendo ....

Ya estoy en linux, a probar la solución ....

---

### Post by LucasXIIHK on 2009-05-27
> **eldragon said:**
> para tratar de debugear esto, mejor seria que postees un Xorg.0.log y un lspci para ver que modelo de placa tenes.
**Okas.... el Xorg.0.log tiene esto:**
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.6.1.901 (1.6.2 RC 1)
Release Date: 2009-5-8
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-xen i686 Ubuntu
Current Operating System: Linux acero 2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686
Build Date: 24 May 2009  12:33:40AM
xorg-server 2:1.6.1.901+git20090523+server-1.6-branch.5cd5a012-0ubuntu0sarvatt2 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 26 22:16:13 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x1bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 3, Mem @ 0x54000000/1048576, 0x40000000/268435456, I/O @ 0x00005110/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.4.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
    965GM, 965GME/GLE, G33, Q35, Q33,
    Mobile Intel® GM45 Express Chipset,
    Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x541003b0 - 0x541003bb (0xc) IS[b]
    [10] 0    0    0x541003c0 - 0x541003df (0x20) IS[b]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "AccelMethod" "uxa"
(**) intel(0): Option "Tiling" "false"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(--) intel(0): Linear framebuffer at 0x40000000
(--) intel(0): IO registers at addr 0x54000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(II) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7616 kB
(II) intel(0): VESA VBE OEM: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)GM965/PM965/GL960 Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video1
(II) intel(0): Output TV has no monitor section
(II) intel(0): EDID for output VGA
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: AUO  Model: 2774  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V7
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742700000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205637200a009d
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID for output TV
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 7676 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 2.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000203 to 0x00000000
(WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(WW) intel(0): PIPEASTAT after: status:
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x80000206 to 0x00000206
(WW) intel(0): PIPEBSTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x100000c0 to 0x000c0000
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710088
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x4e2d1dc8
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x8000085e
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x541003b0 - 0x541003bb (0xc) IS[b](OprU)
    [10] 0    0    0x541003c0 - 0x541003df (0x20) IS[b](OprU)
(II) intel(0): Kernel reported 238592 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 954364 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: node name is /dev/dri/card0
(EE) [drm] drmOpen failed.
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling disabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with untiled buffers.
(II) intel(0): Untiled allocation successful.
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Disable render standby.
(**) intel(0): Option "MigrationHeuristic" "greedy"
(**) intel(0): Option "EXAOptimizeMigration" "true"
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0077f000 (pgoffset 1919)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00043fff: exa G965 state buffer (72 kB)
(II) intel(0): 0x00044000-0x00044fff: overlay registers (4 kB)
(II) intel(0): 0x00045000-0x00045fff: power context (4 kB)
(II) intel(0): 0x00050000-0x0068ffff: front buffer (6400 kB)
(II) intel(0): 0x00690000-0x0194ffff: exa offscreen (19200 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Failed
(--) RandR disabled
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
(II) intel(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) AT Translated Set 2 keyboard: xkb_layout: "es"
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.99.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event11"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) Video Bus: xkb_layout: "es"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) Video Bus: xkb_layout: "es"
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event10"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Genius Optical Mouse
(**) Genius Optical Mouse: always reports core events
(**) Genius Optical Mouse: Device: "/dev/input/event2"
(II) Genius Optical Mouse: Found 3 mouse buttons
(II) Genius Optical Mouse: Found x and y relative axes
(II) Genius Optical Mouse: Configuring as mouse
(**) Genius Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE)
(**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
(**) Genius Optical Mouse: (accel) filter chain progression: 2.00
(**) Genius Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Genius Optical Mouse: (accel) set acceleration profile 0
(II) intel(0): EDID for output VGA
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: AUO  Model: 2774  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V7
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742700000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205637200a009d
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01950000 (pgoffset 6480)
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): EDID for output TV
(EE) intel(0): underrun on pipe B!
(II) intel(0): EDID for output VGA
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: AUO  Model: 2774  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V7
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742700000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205637200a009d
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01950000 (pgoffset 6480)
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): EDID for output TV
(II) intel(0): EDID for output VGA
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: AUO  Model: 2774  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V7
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742700000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205637200a009d
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01950000 (pgoffset 6480)
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): EDID for output TV
(II) intel(0): EDID for output VGA
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: AUO  Model: 2774  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V7
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742700000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205637200a009d
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01950000 (pgoffset 6480)
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): EDID for output TV
(II) intel(0): EDID for output VGA
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: AUO  Model: 2774  Serial#: 0
(II) intel(0): Year: 2006  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B154EW02 V7
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0006af742700000000
(II) intel(0):     01100103802115780a1cf59758508e27
(II) intel(0):     27505400000001010101010101010101
(II) intel(0):     010101010101c71b00a0502017303020
(II) intel(0):     36004bcf100000180000000f00000000
(II) intel(0):     00000000000000000020000000fe0041
(II) intel(0):     554f0a202020202020202020000000fe
(II) intel(0):     004231353445573032205637200a009d
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): EDID vendor "AUO", prod id 10100
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01950000 (pgoffset 6480)
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): EDID for output TV

```**Y el lspci tiene esto:**
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```**Mil Gracias por la atención eldragon....**

---

### Post by eldragon on 2009-05-27
```

(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "AccelMethod" "uxa"
(**) intel(0): Option "Tiling" "false"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(--) intel(0): Linear framebuffer at 0x40000000
(--) intel(0): IO registers at addr 0x54000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration

```

eso me llama la atencion, tenes como option: accelmethod UXA pero despues decide usar EXA. o el uno o el otro... que tenes en tu xorg.conf? no tenes ninguno? si no tenes un xorg, genera uno nuevo. y fijate que podes configurar para tu chipset (965GM)

acordate que xorg ahora detecta (por medio de hal) input devices, asi que todas las secciones sobre mouse y teclado las podes comentar.

te doy un ejemplo: mi xorg (para 945GM) es:

```

Section "ServerFlags"
	Option		"DontZap"	"off"
EndSection


Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/misc"
	FontPath     "/usr/share/fonts/100dpi:unscaled"
	FontPath     "/usr/share/fonts/75dpi:unscaled"
	FontPath     "/usr/share/fonts/TTF"
	FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
	Load  "GLcore"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
        Option      "MigrationHeuristic" "greedy"

EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

fijate que casi no puse opciones dentro de la seccion device. en tu caso, me parece que lo mejor es poner: accelmethod EXA, y tiling FALSE (lo de tiling es porque hay un bug en el driver de intel con respecto a esa opcion y tu tarj de video).

si lees mas escribiendo en la linea de comandos:
```

$ man intel

```

vas a ver mas sobre las opciones, que hacen y que default tienen configurado. asi logre yo limpiar bastante my device section.

otra cosa que estaria bueno es ver cuantos frames obtenes con glxgears. y si da algun error, cual.

---

### Post by guillermolisi on 2009-05-27
En [este thread]("http://ubuntuforums.org/showpost.php?p=7101147&postcount=1") se trata, practicamente, el mismo tema y segun dijo el que lo inicio, funciono la solucion que le han sugerido.

---

### Post by staar on 2009-05-27
Último mensaje para el Adorable Nuevo Troll Comunitario del Foro Oficial del Ubuntu LoCo Team Argentina:

Es costumbre, difundida entre las sociedades humanas (*homo sapiens*), iniciarse en un grupo de individuos de la especie ya conformado, con maneras respetuosas y humildes para con los componentes sociales que conforman el elemento común de conexión entre los integrantes precedentes del grupo, a fin de ser aceptado por el mismo, concepto descrito en lengua Castellana por la palabra *tolerancia*.

La ignorancia de dicha costumbre, conlleva al rechazo por parte de los miembros establecidos en el grupo, produciéndose un fenómeno llamado *hostilidad*, consistente en la agresión hacia el individuo ingresante, que es finalizada, una vez que el mismo prosigue con una de los siguientes comportamientos:

   a) El individuo ingresante depone su actitud, y comienza a actuar conforme a la costumbre ya descrita.

   b) El individuo ingresante se retira del grupo.

          Es mi más sincero deseo, que Ud. opte por la opción a) y cese en su actitud Troll. Sin más que decirle, lo saluda

Atte.

staar

---

### Post by LucasXIIHK on 2009-05-27
> **eldragon said:**
> ```

(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "AccelMethod" "uxa"
(**) intel(0): Option "Tiling" "false"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(--) intel(0): Linear framebuffer at 0x40000000
(--) intel(0): IO registers at addr 0x54000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration

```eso me llama la atencion, tenes como option: accelmethod UXA pero despues decide usar EXA. o el uno o el otro... que tenes en tu xorg.conf? no tenes ninguno? si no tenes un xorg, genera uno nuevo. y fijate que podes configurar para tu chipset (965GM)

acordate que xorg ahora detecta (por medio de hal) input devices, asi que todas las secciones sobre mouse y teclado las podes comentar.

te doy un ejemplo: mi xorg (para 945GM) es:

```

Section "ServerFlags"
    Option        "DontZap"    "off"
EndSection


Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/misc"
    FontPath     "/usr/share/fonts/100dpi:unscaled"
    FontPath     "/usr/share/fonts/75dpi:unscaled"
    FontPath     "/usr/share/fonts/TTF"
    FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
    Load  "GLcore"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
        Option      "MigrationHeuristic" "greedy"

EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```fijate que casi no puse opciones dentro de la seccion device. en tu caso, me parece que lo mejor es poner: accelmethod EXA, y tiling FALSE (lo de tiling es porque hay un bug en el driver de intel con respecto a esa opcion y tu tarj de video).

si lees mas escribiendo en la linea de comandos:
```

$ man intel

```vas a ver mas sobre las opciones, que hacen y que default tienen configurado. asi logre yo limpiar bastante my device section.

otra cosa que estaria bueno es ver cuantos frames obtenes con glxgears. y si da algun error, cual.

Tengo el Tiling en true, voy a probar leer el manual y configurar con paciencia .... mil gracias, si no funciona me vuelvo al ubuntu 8.10 y chau ..... 

Mil Gracias ... saludos!

P.S.:Staar, me refiero con respeto solo a aquellos que me respetan, si me faltás el respeto no esperes que yo te respete .... seas nuevo o viejo en la comunidad da igual, el respeto se tiene que mantener en ambos sentidos ....

---

### Post by staar on 2009-05-27
traducción al criollo: si entrás bardeando al foro, después no pidas respeto pibe...

para tu problema, vuelvo a poner el link que aportó guillermo [http://ubuntuforums.org/showthread.php?p=7101147#post7101147]("http://ubuntuforums.org/showthread.php?p=7101147#post7101147") es un thread donde se trata este tema, donde al parecer hay una solución, confirmada por varios users...

saludos

---

### Post by LucasXIIHK on 2009-05-27
> **staar said:**
> traducción al criollo: si entrás bardeando al foro, después no pidas respeto pibe...

para tu problema, vuelvo a poner el link que aportó guillermo [http://ubuntuforums.org/showthread.php?p=7101147#post7101147](http://ubuntuforums.org/showthread.php?p=7101147#post7101147) es un thread donde se trata este tema, donde al parecer hay una solución, confirmada por varios users...

saludos
Gracias pero no funcionó, la PC anda más lento por las configuraciones en Device y el compiz forzado lo único que logra es poner mi pantalla en blanco ..... 

No hay solución U.U

---

### Post by z37a on 2009-05-27
> **LucasXIIHK said:**
> Gracias pero no funcionó, la PC anda más lento por las configuraciones en Device y el compiz forzado lo único que logra es poner mi pantalla en blanco ..... 

No hay solución U.U


Cuanta memoria le asignastes a tu GPU? En mi caso me paso de andar lento por solo tener puesto 32MB y usar una resolucion de 1680x1050!

---

### Post by LucasXIIHK on 2009-05-27
> **z37a said:**
> Cuanta memoria le asignastes a tu GPU? En mi caso me paso de andar lento por solo tener puesto 32MB y usar una resolucion de 1680x1050!

256MB y estoy a 1280x800 .... cuando activo compiz quedo con la pantalla en blanco .... en las versiones anteriores andaba y ahora no ..... igual ya fue, me estoy bajando el Linux Mint para probarlo .... no se hagan más drama .... a parte tengo el Windows en la otra partición .... pregunté porque capaz que alguno la tenía bien bien clara y me sacaba la duda rápido .... 

Mil gracias de todos modos....

P.S.: Me voy a dormir, me envicié jugando en el ScummVM y se me hizo cualquier hora XD

---

