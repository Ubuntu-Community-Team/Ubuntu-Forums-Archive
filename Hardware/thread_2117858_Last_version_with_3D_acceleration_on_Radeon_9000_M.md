---
title: "Last version with 3D acceleration on Radeon 9000 M?"
date: 2013-02-19
forum: Hardware
---

### Post by OldStuffUser on 2013-02-19
Hi,

i've got a laptop here with an Radeon 9000 M and wonder what is the last version
with supported 3D accelleration.

I tried 12.04 and there seems to be no 3D Accelleration.
I thin accelleration was dropped from gallium3d or mesa or something like that for those old chips?

Is there any way to get this thing to accelerate 3d and maybe use unity?

Maybe with some compiling-on-my-own?

Thanks

---

### Post by libarts on 2013-02-19
Here's a list of supported cards.  9000 M doesn't seem to appear here.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by ajgreeny on 2013-02-19
With that card, which I also have in an old Acer Travelmate 2200 laptop, I suspect that all your hardware is going to be unable to run unity well enough to make it a worthwhile option.

I can't answer your specific query about which ubuntu version last supported 3D acceleration, but can tell you that both Xubuntu and Lubuntu 12.04 run extremely well on my old machine with only 512MB ram and a single core celeron CPU.

---

### Post by OldStuffUser on 2013-02-19
> **libarts said:**
> Here's a list of supported cards.  9000 M doesn't seem to appear here.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


Well it is listed : 
```
RV250                       Radeon 9000PRO/9000, M9
```But i've not gotten this card to work in newer Ubuntus.
It worked with some 10.x i believe.
In the newer version i checked with fglrx_gears or sth. like that and the fps were too low.

Overall a Pentium M 1700Mhz and 2 GB Ram is enough,
but without 3d acceleration unity is next to unusable. Its like waiting 3 seconds for the searchbar ... terrible.


Here are the outputs of glxinfo and unity_check
```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:

```



```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.4

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

---

### Post by Yellow Pasque on 2013-02-19
Post your /var/log/Xorg.0.log

---

### Post by Mark Phelps on 2013-02-20
> **OldStuffUser said:**
> Hi,

i've got a laptop here with an Radeon 9000 M and wonder what is the last version
with supported 3D accelleration.



From what I was able to find, those were last supported in 2006 -- which makes the Ubuntu version 6.x.

---

### Post by OldStuffUser on 2013-02-20
Hi,

@Mark Phelps
I remember it working with compiz something around 10.x or 11.x version

@ Temüjin
Looks like the "radeon" driver is running, but i dont know why it is listed as software rendering in the above commands then.

Seems to fail later on with, although i'm not sure what exactly it tries to toll me by that message
```

[    36.818] (EE) AIGLX error: r200 does not export required DRI extension
[    36.818] (EE) AIGLX: reverting to software rendering 
```

Here is the Xor.0.log:
```

[    32.142] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    32.142] X Protocol Version 11, Revision 0
[    32.142] Build Operating System: Linux 2.6.42-34-generic i686 Ubuntu
[    32.142] Current Operating System: Linux ThinkPad-T41 3.2.0-38-generic #60-Ubuntu SMP Wed Feb 13 13:27:35 UTC 2013 i686
[    32.142] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=518d7cbe-3bbb-44ba-b5ca-8f3898fe7621 ro quiet splash nomodeset vt.handoff=7
[    32.142] Build Date: 16 January 2013  11:05:18PM
[    32.142] xorg-server 2:1.11.4-0ubuntu10.11 (For technical support please see http://www.ubuntu.com/support) 
[    32.142] Current version of pixman: 0.24.4
[    32.142]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    32.142] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.142] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 20 20:07:42 2013
[    32.142] (==) Using config file: "/etc/X11/xorg.conf"
[    32.142] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    32.152] (==) ServerLayout "X.org Configured"
[    32.152] (**) |-->Screen "Screen0" (0)
[    32.152] (**) |   |-->Monitor "Monitor0"
[    32.152] (**) |   |-->Device "Card0"
[    32.152] (**) |-->Screen "Screen1" (1)
[    32.152] (**) |   |-->Monitor "Monitor1"
[    32.153] (**) |   |-->Device "Card1"
[    32.153] (**) |-->Screen "Screen2" (2)
[    32.153] (**) |   |-->Monitor "Monitor2"
[    32.153] (**) |   |-->Device "Card2"
[    32.153] (**) |-->Input Device "Mouse0"
[    32.153] (**) |-->Input Device "Keyboard0"
[    32.153] (==) Automatically adding devices
[    32.153] (==) Automatically enabling devices
[    32.153] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    32.153]     Entry deleted from font path.
[    32.153] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    32.153]     Entry deleted from font path.
[    32.153] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    32.153]     Entry deleted from font path.
[    32.153] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    32.153]     Entry deleted from font path.
[    32.153] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    32.153]     Entry deleted from font path.
[    32.153] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    32.153]     Entry deleted from font path.
[    32.153] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    32.153]     Entry deleted from font path.
[    32.153] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    32.153]     Entry deleted from font path.
[    32.153] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    32.153]     Entry deleted from font path.
[    32.153] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    32.153]     Entry deleted from font path.
[    32.153] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    32.153] (**) ModulePath set to "/usr/lib/xorg/modules"
[    32.153] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    32.153] (WW) Disabling Mouse0
[    32.153] (WW) Disabling Keyboard0
[    32.153] (II) Loader magic: 0xc705a0
[    32.153] (II) Module ABI versions:
[    32.153]     X.Org ANSI C Emulation: 0.4
[    32.153]     X.Org Video Driver: 11.0
[    32.154]     X.Org XInput driver : 16.0
[    32.154]     X.Org Server Extension : 6.0
[    32.154] (--) PCI:*(0:1:0:0) 1002:4c66:1014:0531 rev 2, Mem @ 0xe0000000/134217728, 0xc0100000/65536, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    32.155] (II) Open ACPI successful (/var/run/acpid.socket)
[    32.155] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    32.155] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    32.155] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    32.155] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    32.155] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    32.155] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    32.155] (II) LoadModule: "dri"
[    32.155] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    32.158] (II) Module dri: vendor="X.Org Foundation"
[    32.158]     compiled for 1.11.3, module version = 1.0.0
[    32.158]     ABI class: X.Org Server Extension, version 6.0
[    32.158] (II) Loading extension XFree86-DRI
[    32.158] (II) LoadModule: "record"
[    32.158] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    32.158] (II) Module record: vendor="X.Org Foundation"
[    32.158]     compiled for 1.11.3, module version = 1.13.0
[    32.158]     Module class: X.Org Server Extension
[    32.158]     ABI class: X.Org Server Extension, version 6.0
[    32.158] (II) Loading extension RECORD
[    32.158] (II) LoadModule: "glx"
[    32.158] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    32.158] (II) Module glx: vendor="X.Org Foundation"
[    32.158]     compiled for 1.11.3, module version = 1.0.0
[    32.158]     ABI class: X.Org Server Extension, version 6.0
[    32.158] (==) AIGLX enabled
[    32.159] (II) Loading extension GLX
[    32.159] (II) LoadModule: "dbe"
[    32.159] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    32.159] (II) Module dbe: vendor="X.Org Foundation"
[    32.159]     compiled for 1.11.3, module version = 1.0.0
[    32.159]     Module class: X.Org Server Extension
[    32.159]     ABI class: X.Org Server Extension, version 6.0
[    32.159] (II) Loading extension DOUBLE-BUFFER
[    32.159] (II) LoadModule: "dri2"
[    32.159] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    32.159] (II) Module dri2: vendor="X.Org Foundation"
[    32.159]     compiled for 1.11.3, module version = 1.2.0
[    32.159]     ABI class: X.Org Server Extension, version 6.0
[    32.159] (II) Loading extension DRI2
[    32.159] (II) LoadModule: "extmod"
[    32.160] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    32.160] (II) Module extmod: vendor="X.Org Foundation"
[    32.160]     compiled for 1.11.3, module version = 1.0.0
[    32.160]     Module class: X.Org Server Extension
[    32.160]     ABI class: X.Org Server Extension, version 6.0
[    32.160] (II) Loading extension MIT-SCREEN-SAVER
[    32.160] (II) Loading extension XFree86-VidModeExtension
[    32.160] (II) Loading extension XFree86-DGA
[    32.160] (II) Loading extension DPMS
[    32.160] (II) Loading extension XVideo
[    32.160] (II) Loading extension XVideo-MotionCompensation
[    32.160] (II) Loading extension X-Resource
[    32.160] (II) LoadModule: "radeon"
[    32.160] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    32.160] (II) Module radeon: vendor="X.Org Foundation"
[    32.160]     compiled for 1.11.3, module version = 6.14.99
[    32.160]     Module class: X.Org Video Driver
[    32.160]     ABI class: X.Org Video Driver, version 11.0
[    32.160] (II) LoadModule: "fbdev"
[    32.161] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    32.161] (II) Module fbdev: vendor="X.Org Foundation"
[    32.161]     compiled for 1.11.3, module version = 0.4.2
[    32.161]     ABI class: X.Org Video Driver, version 11.0
[    32.161] (II) LoadModule: "vesa"
[    32.161] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    32.161] (II) Module vesa: vendor="X.Org Foundation"
[    32.161]     compiled for 1.11.3, module version = 2.3.0
[    32.161]     Module class: X.Org Video Driver
[    32.161]     ABI class: X.Org Video Driver, version 11.0
[    32.161] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[    32.173] (II) FBDEV: driver for framebuffer: fbdev
[    32.173] (II) VESA: driver for VESA chipsets: vesa
[    32.173] (++) using VT number 7

[    32.173] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    32.174] (II) [KMS] drm report modesetting isn't supported.
[    32.174] (WW) Falling back to old probe method for fbdev
[    32.174] (II) Loading sub module "fbdevhw"
[    32.174] (II) LoadModule: "fbdevhw"
[    32.174] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    32.174] (II) Module fbdevhw: vendor="X.Org Foundation"
[    32.174]     compiled for 1.11.3, module version = 0.0.2
[    32.174]     ABI class: X.Org Video Driver, version 11.0
[    32.174] (WW) Falling back to old probe method for vesa
[    32.174] (II) RADEON(0): TOTO SAYS 00000000c0100000
[    32.174] (II) RADEON(0): MMIO registers at 0x00000000c0100000: size 64KB
[    32.174] (II) RADEON(0): PCI bus 1 card 0 func 0
[    32.174] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    32.174] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    32.174] (==) RADEON(0): Default visual is TrueColor
[    32.174] (II) Loading sub module "vgahw"
[    32.174] (II) LoadModule: "vgahw"
[    32.175] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    32.175] (II) Module vgahw: vendor="X.Org Foundation"
[    32.175]     compiled for 1.11.3, module version = 0.1.0
[    32.175]     ABI class: X.Org Video Driver, version 11.0
[    32.175] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    32.175] (==) RADEON(0): RGB weight 888
[    32.175] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    32.175] (--) RADEON(0): Chipset: "ATI Radeon Mobility 9000 (M9) Lf (AGP)" (ChipID = 0x4c66)
[    32.175] (--) RADEON(0): Linear framebuffer at 0x00000000e0000000
[    32.175] (II) RADEON(0): AGP card detected
[    32.175] (II) Loading sub module "int10"
[    32.175] (II) LoadModule: "int10"
[    32.175] (II) Loading /usr/lib/xorg/modules/libint10.so
[    32.175] (II) Module int10: vendor="X.Org Foundation"
[    32.175]     compiled for 1.11.3, module version = 1.0.0
[    32.175]     ABI class: X.Org Video Driver, version 11.0
[    32.175] (II) RADEON(0): initializing int10
[    32.176] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    32.176] (II) RADEON(0): Legacy BIOS detected
[    32.176] drmOpenDevice: node name is /dev/dri/card0
[    32.176] drmOpenDevice: open result is 11, (OK)
[    32.176] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    32.176] drmOpenDevice: node name is /dev/dri/card0
[    32.176] drmOpenDevice: open result is 11, (OK)
[    32.176] drmOpenByBusid: drmOpenMinor returns 11
[    32.176] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    32.176] (II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.33.0
[    32.176] (==) RADEON(0): Page Flipping disabled
[    32.176] (II) RADEON(0): Will try to use DMA for Xv image transfers
[    32.177] (II) RADEON(0): Detected total video RAM=32768K, accessible=65536K (PCI BAR=131072K)
[    32.177] (--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit DDR SDRAM)
[    32.177] (II) RADEON(0): Color tiling enabled by default
[    32.177] (II) Loading sub module "ddc"
[    32.177] (II) LoadModule: "ddc"
[    32.177] (II) Module "ddc" already built-in
[    32.177] (II) Loading sub module "i2c"
[    32.177] (II) LoadModule: "i2c"
[    32.177] (II) Module "i2c" already built-in
[    32.177] (II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 20000, sclk: 252.000000, mclk: 200.000000
[    32.177] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=35000; xclk=20000
[    32.177] (II) RADEON(0): DFP table revision: 3
[    32.177] (II) RADEON(0): Panel ID string: SXGA+ Single (85MHz)    
[    32.177] (II) RADEON(0): Panel Size from BIOS: 1400x1050
[    32.177] (II) RADEON(0): BIOS provided dividers will be used.
[    32.177] (WW) RADEON(0): LVDS Info:
XRes: 1400, YRes: 1050, DotClock: 84960
HBlank: 200, HOverPlus: 72, HSyncWidth: 40
VBlank: 12, VOverPlus: 2, VSyncWidth: 1
[    32.177] (II) RADEON(0): Output VGA-0 using monitor section Monitor0
[    32.177] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    32.177] (II) RADEON(0): Output DVI-0 has no monitor section
[    32.177] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    32.177] (II) RADEON(0): Output LVDS has no monitor section
[    32.177] (II) RADEON(0): Output S-video has no monitor section
[    32.177] (II) RADEON(0): Default TV standard: NTSC
[    32.177] (II) RADEON(0): TV standards supported by chip: NTSC PAL NTSC-J 
[    32.177] (II) RADEON(0): Port0:
[    32.177]   XRANDR name: VGA-0
[    32.177]   Connector: VGA
[    32.177]   CRT1: INTERNAL_DAC1
[    32.177]   DDC reg: 0x60
[    32.177] (II) RADEON(0): Port1:
[    32.177]   XRANDR name: DVI-0
[    32.177]   Connector: DVI-D
[    32.177]   DFP1: INTERNAL_TMDS1
[    32.177]   DDC reg: 0x64
[    32.177] (II) RADEON(0): Port2:
[    32.177]   XRANDR name: LVDS
[    32.177]   Connector: LVDS
[    32.177]   LCD1: INTERNAL_LVDS
[    32.177]   DDC reg: 0x0
[    32.177] (II) RADEON(0): Port3:
[    32.177]   XRANDR name: S-video
[    32.177]   Connector: S-video
[    32.177]   TV1: INTERNAL_DAC2
[    32.177]   DDC reg: 0x0
[    32.178] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    32.183] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    32.183] finished output detect: 0
[    32.183] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    32.187] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    32.187] finished output detect: 1
[    32.187] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    32.187] finished output detect: 2
[    32.187] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    32.187] finished output detect: 3
[    32.187] finished all detect
[    32.195] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    32.195] (II) RADEON(0): EDID for output VGA-0
[    32.198] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    32.198] (II) RADEON(0): EDID for output DVI-0
[    32.198] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    32.198] (II) RADEON(0): Added native panel mode: 1400x1050
[    32.199] (II) RADEON(0): Printing probed modes for output LVDS
[    32.199] (II) RADEON(0): Modeline "1400x1050"x50.0   84.96  1400 1472 1512 1600  1050 1052 1053 1062 (53.1 kHz)
[    32.199] (II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[    32.199] (II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[    32.199] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[    32.199] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    32.199] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    32.199] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    32.199] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    32.199] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    32.199] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    32.199] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    32.199] (II) RADEON(0): EDID for output S-video
[    32.199] (II) RADEON(0): Output VGA-0 disconnected
[    32.199] (II) RADEON(0): Output DVI-0 disconnected
[    32.199] (II) RADEON(0): Output LVDS connected
[    32.199] (II) RADEON(0): Output S-video disconnected
[    32.199] (II) RADEON(0): Using exact sizes for initial modes
[    32.199] (II) RADEON(0): Output LVDS using initial mode 1400x1050
[    32.199] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    32.199] (==) RADEON(0): DPI set to (96, 96)
[    32.199] (II) Loading sub module "fb"
[    32.199] (II) LoadModule: "fb"
[    32.199] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.199] (II) Module fb: vendor="X.Org Foundation"
[    32.199]     compiled for 1.11.3, module version = 1.0.0
[    32.199]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.199] (II) Loading sub module "ramdac"
[    32.199] (II) LoadModule: "ramdac"
[    32.199] (II) Module "ramdac" already built-in
[    32.199] (==) RADEON(0): Using XAA acceleration architecture
[    32.199] (II) Loading sub module "xaa"
[    32.199] (II) LoadModule: "xaa"
[    32.200] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    32.200] (II) Module xaa: vendor="X.Org Foundation"
[    32.200]     compiled for 1.11.3, module version = 1.2.1
[    32.200]     ABI class: X.Org Video Driver, version 11.0
[    32.200] (==) RADEON(0): Assuming overlay scaler buffer width is 1536
[    32.200] (II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
[    32.200] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    32.200] (II) UnloadModule: "fbdev"
[    32.200] (II) Unloading fbdev
[    32.200] (II) UnloadModule: "fbdevhw"
[    32.200] (II) Unloading fbdevhw
[    32.200] (II) UnloadModule: "vesa"
[    32.200] (II) Unloading vesa
[    32.200] (--) Depth 24 pixmap format is 32 bpp
[    32.200] (II) RADEON(0): RADEONScreenInit e0000000 0 0
[    32.205] Entering TV Save
[    32.205] Save TV timing tables
[    32.205] saveTimingTables: reading timing tables
[    32.205] TV Save done
[    33.205] (II) RADEON(0): Dynamic Power Management Disabled
[    33.205] (==) RADEON(0): Using 24 bit depth buffer
[    33.205] (II) RADEON(0): RADEONInitMemoryMap() : 
[    33.205] (II) RADEON(0):   mem_size         : 0x04000000
[    33.205] (II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
[    33.205] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    33.206] (II) RADEON(0): Depth moves disabled by default
[    33.206] (II) RADEON(0): Using 8 MB GART aperture
[    33.206] (II) RADEON(0): Using 1 MB for the ring buffer
[    33.206] (II) RADEON(0): Using 2 MB for vertex/indirect buffers
[    33.206] (II) RADEON(0): Using 5 MB for GART textures
[    33.206] (II) RADEON(0): Memory manager initialized to (0,0) (1408,5957)
[    33.206] (II) RADEON(0): Reserved area from (0,1400) to (1408,1410)
[    33.206] (II) RADEON(0): Largest offscreen area available: 1408 x 4547
[    33.206] (II) RADEON(0): Will use front buffer at offset 0x0
[    33.206] (II) RADEON(0): Will use back buffer at offset 0xf20000
[    33.206] (II) RADEON(0): Will use depth buffer at offset 0x16b0000
[    33.206] (II) RADEON(0): Will use 1792 kb for textures at offset 0x1e40000
[    33.206] drmOpenDevice: node name is /dev/dri/card0
[    33.206] drmOpenDevice: open result is 11, (OK)
[    33.206] drmOpenDevice: node name is /dev/dri/card0
[    33.206] drmOpenDevice: open result is 11, (OK)
[    33.206] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    33.206] drmOpenDevice: node name is /dev/dri/card0
[    33.206] drmOpenDevice: open result is 11, (OK)
[    33.206] drmOpenByBusid: drmOpenMinor returns 11
[    33.206] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    33.206] (II) [drm] DRM interface version 1.4
[    33.206] (II) [drm] DRM open master succeeded.
[    33.206] (II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
[    33.206] (II) RADEON(0): [drm] framebuffer handle = 0xe0000000
[    33.206] (II) RADEON(0): [drm] added 1 reserved context for kernel
[    33.206] (II) RADEON(0): X context handle = 0x1
[    33.206] (II) RADEON(0): [drm] installed DRM signal handler
[    33.206] (==) RADEON(0): Using AGP 4x
[    33.206] (II) RADEON(0): [agp] Mode 0x1f000207 [AGP 0x8086/0x3340; Card 0x1002/0x4c66 0x1014/0x0531]
[    33.219] (II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
[    33.220] (II) RADEON(0): [agp] ring handle = 0xd0000000
[    33.220] (II) RADEON(0): [agp] Ring mapped at 0xb7499000
[    33.220] (II) RADEON(0): [agp] ring read ptr handle = 0xd0101000
[    33.220] (II) RADEON(0): [agp] Ring read ptr mapped at 0xb774e000
[    33.220] (II) RADEON(0): [agp] vertex/indirect buffers handle = 0xd0102000
[    33.221] (II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb7299000
[    33.221] (II) RADEON(0): [agp] GART texture map handle = 0xd0302000
[    33.221] (II) RADEON(0): [agp] GART Texture map mapped at 0xb6db9000
[    33.221] (II) RADEON(0): [drm] register handle = 0x28020000
[    33.221] (II) RADEON(0): [dri] Visual configs initialized
[    33.221] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    33.221] (II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000 0x1fff0000
[    33.221] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    33.424] (==) RADEON(0): Backing store disabled
[    33.424] (II) RADEON(0): [DRI] installation complete
[    33.445] (II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
[    33.446] (II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
[    33.446] (II) RADEON(0): [drm] dma control initialized, using IRQ 11
[    33.446] (II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
[    33.446] (WW) RADEON(0): DRI init changed memory map, adjusting ...
[    33.446] (WW) RADEON(0):   MC_FB_LOCATION  was: 0xe3ffe000 is: 0xe3ffe000
[    33.446] (WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xd07fd000
[    33.446] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    33.446] (II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000 0xe3ffe000
[    33.446] (II) RADEON(0):   MC_AGP_LOCATION  : 0xd07fd000
[    33.546] (II) RADEON(0): Direct rendering enabled
[    33.546] (II) RADEON(0): Render acceleration disabled
[    33.546] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    33.546]     Screen to screen bit blits
[    33.546]     Solid filled rectangles
[    33.546]     8x8 mono pattern filled rectangles
[    33.546]     Indirect CPU to Screen color expansion
[    33.546]     Solid Lines
[    33.546]     Scanline Image Writes
[    33.546]     Setting up tile and stipple cache:
[    33.546]         32 128x128 slots
[    33.546]         32 256x256 slots
[    33.546]         13 512x512 slots
[    33.546] (II) RADEON(0): Acceleration enabled
[    33.546] (==) RADEON(0): DPMS enabled
[    33.546] (==) RADEON(0): Silken mouse enabled
[    33.546] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00792c00
[    33.547] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00796e00
[    33.547] (II) RADEON(0): Largest offscreen area available: 1408 x 4541
[    33.547] (II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
[    33.547] (II) Loading sub module "theatre_detect"
[    33.547] (II) LoadModule: "theatre_detect"
[    33.547] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    33.547] (II) Module theatre_detect: vendor="X.Org Foundation"
[    33.547]     compiled for 1.11.3, module version = 1.0.0
[    33.547]     ABI class: X.Org Video Driver, version 11.0
[    33.547] (II) RADEON(0): no multimedia table present, disabling Rage Theatre.
[    33.547] (II) RADEON(0): Set up overlay video
[    33.547] (II) RADEON(0): Set up textured video
[    33.547] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    33.547] (II) RADEON(0): [XvMC] Extension initialized.
[    33.597] disable primary dac
[    33.597] disable FP1
[    34.597] disable TV
[    35.597] init memmap
[    35.597] init common
[    35.597] init crtc1
[    35.597] init pll1
[    35.597] restore memmap
[    35.597] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    35.597] (II) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000 0xe3ffe000
[    35.597] (II) RADEON(0):   MC_AGP_LOCATION  : 0xd07fd000
[    35.697] restore common
[    35.797] restore crtc1
[    35.797] restore pll1
[    35.797] set RMX
[    35.797] set LVDS
[    35.798] enable LVDS
[    36.798] disable primary dac
[    36.798] disable FP1
[    36.798] disable TV
[    36.798] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    36.798] (--) RandR disabled
[    36.798] (II) Initializing built-in extension Generic Event Extension
[    36.798] (II) Initializing built-in extension SHAPE
[    36.798] (II) Initializing built-in extension MIT-SHM
[    36.798] (II) Initializing built-in extension XInputExtension
[    36.798] (II) Initializing built-in extension XTEST
[    36.798] (II) Initializing built-in extension BIG-REQUESTS
[    36.798] (II) Initializing built-in extension SYNC
[    36.798] (II) Initializing built-in extension XKEYBOARD
[    36.798] (II) Initializing built-in extension XC-MISC
[    36.798] (II) Initializing built-in extension SECURITY
[    36.798] (II) Initializing built-in extension XINERAMA
[    36.798] (II) Initializing built-in extension XFIXES
[    36.798] (II) Initializing built-in extension RENDER
[    36.798] (II) Initializing built-in extension RANDR
[    36.798] (II) Initializing built-in extension COMPOSITE
[    36.798] (II) Initializing built-in extension DAMAGE
[    36.813] (II) AIGLX: Screen 0 is not DRI2 capable
[    36.813] drmOpenDevice: node name is /dev/dri/card0
[    36.813] drmOpenDevice: open result is 12, (OK)
[    36.813] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    36.813] drmOpenDevice: node name is /dev/dri/card0
[    36.814] drmOpenDevice: open result is 12, (OK)
[    36.814] drmOpenByBusid: drmOpenMinor returns 12
[    36.814] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    36.814] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    36.818] (EE) AIGLX error: r200 does not export required DRI extension
[    36.818] (EE) AIGLX: reverting to software rendering
[    36.835] (II) AIGLX: Loaded and initialized swrast
[    36.835] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    36.836] (II) RADEON(0): Setting screen physical size to 370 x 277
[    36.859] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    36.868] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    36.868] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.868] (II) LoadModule: "evdev"
[    36.869] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.869] (II) Module evdev: vendor="X.Org Foundation"
[    36.869]     compiled for 1.11.3, module version = 2.7.0
[    36.869]     Module class: X.Org XInput Driver
[    36.869]     ABI class: X.Org XInput driver, version 16.0
[    36.869] (II) Using input driver 'evdev' for 'Power Button'
[    36.869] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.869] (**) Power Button: always reports core events
[    36.869] (**) evdev: Power Button: Device: "/dev/input/event2"
[    36.869] (--) evdev: Power Button: Vendor 0 Product 0x1
[    36.870] (--) evdev: Power Button: Found keys
[    36.870] (II) evdev: Power Button: Configuring as keyboard
[    36.870] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    36.870] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    36.870] (**) Option "xkb_rules" "evdev"
[    36.870] (**) Option "xkb_model" "pc105"
[    36.870] (**) Option "xkb_layout" "de"
[    36.874] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    36.875] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    36.875] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    36.875] (II) Using input driver 'evdev' for 'Video Bus'
[    36.875] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.876] (**) Video Bus: always reports core events
[    36.876] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    36.876] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    36.876] (--) evdev: Video Bus: Found keys
[    36.876] (II) evdev: Video Bus: Configuring as keyboard
[    36.876] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input4/event4"
[    36.876] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    36.876] (**) Option "xkb_rules" "evdev"
[    36.876] (**) Option "xkb_model" "pc105"
[    36.876] (**) Option "xkb_layout" "de"
[    36.877] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    36.877] (II) No input driver specified, ignoring this device.
[    36.877] (II) This device may have been added with another device file.
[    36.877] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    36.877] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    36.877] (II) Using input driver 'evdev' for 'Sleep Button'
[    36.877] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.877] (**) Sleep Button: always reports core events
[    36.877] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    36.877] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    36.877] (--) evdev: Sleep Button: Found keys
[    36.877] (II) evdev: Sleep Button: Configuring as keyboard
[    36.877] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    36.877] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    36.877] (**) Option "xkb_rules" "evdev"
[    36.877] (**) Option "xkb_model" "pc105"
[    36.877] (**) Option "xkb_layout" "de"
[    36.878] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    36.878] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    36.878] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    36.878] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.878] (**) AT Translated Set 2 keyboard: always reports core events
[    36.878] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    36.878] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    36.878] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    36.878] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    36.878] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    36.879] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    36.879] (**) Option "xkb_rules" "evdev"
[    36.879] (**) Option "xkb_model" "pc105"
[    36.879] (**) Option "xkb_layout" "de"
[    36.879] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event6)
[    36.879] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    36.879] (**) TPPS/2 IBM TrackPoint: Applying InputClass "trackpoint catchall"
[    36.880] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    36.880] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.880] (**) TPPS/2 IBM TrackPoint: always reports core events
[    36.880] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event6"
[    36.880] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[    36.880] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    36.880] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[    36.880] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[    36.880] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[    36.880] (**) Option "Emulate3Buttons" "true"
[    36.880] (**) Option "EmulateWheel" "true"
[    36.880] (**) Option "EmulateWheelButton" "2"
[    36.880] (**) Option "YAxisMapping" "4 5"
[    36.880] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    36.880] (**) Option "XAxisMapping" "6 7"
[    36.880] (**) evdev: TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
[    36.880] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    36.880] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    36.880] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 10)
[    36.880] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[    36.880] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    36.880] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    36.880] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    36.880] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    36.881] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse0)
[    36.881] (II) No input driver specified, ignoring this device.
[    36.881] (II) This device may have been added with another device file.
[    36.883] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event5)
[    36.883] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    36.883] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[    36.883] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.884] (**) ThinkPad Extra Buttons: always reports core events
[    36.884] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event5"
[    36.884] (--) evdev: ThinkPad Extra Buttons: Vendor 0x1014 Product 0x5054
[    36.884] (--) evdev: ThinkPad Extra Buttons: Found keys
[    36.884] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[    36.884] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input5/event5"
[    36.884] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 11)
[    36.884] (**) Option "xkb_rules" "evdev"
[    36.884] (**) Option "xkb_model" "pc105"
[    36.884] (**) Option "xkb_layout" "de"
[    36.897] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    36.901] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    36.901] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    36.901] (II) RADEON(0): Added native panel mode: 1400x1050
[    36.901] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    37.990] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    37.994] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    37.994] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    37.994] (II) RADEON(0): Added native panel mode: 1400x1050
[    37.994] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    41.592] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    41.596] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    41.596] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    41.596] (II) RADEON(0): Added native panel mode: 1400x1050
[    41.596] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    86.061] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    86.065] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    86.065] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    86.065] (II) RADEON(0): Added native panel mode: 1400x1050
[    86.065] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    86.364] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    86.371] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    86.371] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    86.371] (II) RADEON(0): Added native panel mode: 1400x1050
[    86.371] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    86.834] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[   108.445] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[   108.450] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   108.450] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   108.450] (II) RADEON(0): Added native panel mode: 1400x1050
[   108.450] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0

```

---

### Post by OldStuffUser on 2013-02-20
Well,
going by the above, i found a google hit for 
"radeon.modeset=1" as boot option.

done that and booted, now the radeon driver seems to load ok.

```
ThinkPad-T41:~$ dmesg | grep -i radeon
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=518d7cbe-3bbb-44ba-b5ca-8f3898fe7621 ro quiet splash nomodeset vt.handoff=7 radeon.modeset=1
[   27.508730] [drm] radeon kernel modesetting enabled.
[   27.508858] radeon 0000:01:00.0: power state changed by ACPI to D0
[   27.508864] radeon 0000:01:00.0: power state changed by ACPI to D0
[   27.508878] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   27.546787] radeon 0000:01:00.0: putting AGP V2 device into 1x mode
[   27.546813] radeon 0000:01:00.0: GTT: 256M 0xD0000000 - 0xDFFFFFFF
[   27.546823] radeon 0000:01:00.0: VRAM: 128M 0x00000000E0000000 - 0x00000000E7FFFFFF (32M used)
[   27.546865] [drm] radeon: irq initialized.
[   27.567018] [drm] radeon: 32M of VRAM memory ready
[   27.567021] [drm] radeon: 256M of GTT memory ready.
[   27.598633] radeon 0000:01:00.0: WB disabled
[   28.672380] [drm] radeon: ring at 0x00000000D0001000
[   28.672676] [drm] radeon: ib pool ready.
[   28.684457] [drm] radeon legacy LVDS backlight initialized
[   28.728557] [drm] Radeon Display Connectors
[   28.737753] [drm] radeon: power management initialized
[   29.033718] fbcon: radeondrmfb (fb0) is primary device
[   29.035772] fb0: radeondrmfb frame buffer device
[   29.035789] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0

```
and the unity test says:
```

ThinkPad-T41:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 (RV250 4C66) x86/MMX/SSE2 TCL DRI2
OpenGL version string:  1.3 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity 3D supported:       no

```
Thanks for bringing me on track.
So now the radeon driver loads (can someone explain me why i need to put that manual modeset parameter?)

But since GL_fragment_program is no, i guess unity may not work?
Or in other words: the current acceleration is as much as that chip can do, right?

Also Unity works ... but when opening firefox, i get a solid blue rectangle on the screen ... so i think the rendering works only halfway, probably of the above missing extensions?

---

### Post by balia3 on 2013-09-08
Did you ever solve this problem?
I recently upgraded from ubuntu 10 to ubuntu 12 and after the upgrade lost all my 3d acceleration: no cube for example.

---

