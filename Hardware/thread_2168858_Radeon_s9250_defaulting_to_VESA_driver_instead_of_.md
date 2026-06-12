---
title: "Radeon s9250 defaulting to VESA driver instead of RADEON driver w/12.04; 10.04 works"
date: 2013-08-19
forum: Hardware
---

### Post by EarlsFurniture on 2013-08-19
I'm working with the following hardware on a Xubuntu 12.04.1 system:

ASUS Tusi-M rev 1 motherboard
Intell PIII 1.2GHz Coppermine

Video Card: Diamond Stealth ATI Radeon s9250PCI256SB
(supposed to have S-Video out port but doesn't - ubuntu seems to detect TV cababilities though - I have to call TigerDirect about this - might have received wrong card)
(listed as having 16 x 16M RAM - or 256MB, but looks like 128M per output instead)
(Shows as "9200" instead of "9250")

Originally I was using the onboard SiS630 graphics.  I purchased this ATI video card to hopefully give the machine a little boost, especially accessing a Windows XP VM via VNC on the server. (running in VMWARE player) I also opted for sticking with the 12.04.1 hardware stack because the 12.04.2 (quantal) stack refused to produce a working gui at all using the onboard SiS chipset. I didn't want to roll that forward again unless necessary.

The only way I can get a usable GUI is to set "radeon.modeset=0" in /etc/default/grub and to NOT have an xorg.conf file in /etc/X11/
With this configuration, the radeon driver loads, then unloads, then VESA takes over and handles the screen. (but I'm limited to only 16MB Video RAM and essentially no use of the card's capabilities limted as they are)

However, I tested with a Ubuntu 10.04.4 Live CD and that system has no problem using the RADEON opensource driver properly (even without modesetting disabled).

So I know the hardware works. (Still need to find out what happend to my S-video out and my other 128MB of Video RAM)

The issue has to be a change with either the kernel (modesetting perhaps), Xorg, or the radeon driver.

With much searching and tinkering, I've managed to get as far as a console login by disabling modesetting as noted, and using a custom xorg.conf, but X will not start (screens found but none have a usable configuration).

Note, if I turn modesetting on, I end up with a black screen and a dead keyboard and I can't SSH into the system, with modesetting turned off, and without the custom xorg.conf, I get a blinking cursor - no working consoles on F1-F6, but I can SSH into it.

In a nutshell:
modeset & anything produces a black screen and I can not SSH into the system.
nomodeset & custom xorg.conf briefly flashes the plymouth boot then fails and falls back to a console login.
nomodeset & no xorg.conf produces a flashing cursor, no console on F1-F6 but I can SSH into the system.
nomodeset & no xorg.conf produces a working gui using the vesa driver.

Thus it seems modesetting is preventing the kernel from loading as I can't even get a usable system that way.

I've tried everything I can think of that seems relevant and am stumped.

Perhaps I've just been looking at this too long. (2 weeks now) I think I'm close to the solution, but for the life of me can't see it.

Any help is greatly appreciated.

Here are some relevant command results and log files from the session where VESA is being used:

```
uname -a

3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:21:10 UTC 2013 i686 i686 i386 GNU/Linux
```

Some File versions on this 12.04 system:
```

ii  libdrm-radeon1                                    2.4.43-0ubuntu0.0.2                                  Userspace interface to radeon-specific kernel DRM services -- runtime
ii  radeontool                                        1.6.2-1.1                                            utility to control ATI Radeon backlight functions on laptops
ii  xserver-xorg-video-radeon                         1:6.99.99~git20120913.8637f772-0ubuntu1~precise~xup2 X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg                                      1:7.6+12ubuntu2                                      X.Org X server
ii  xserver-xorg-core                                 2:1.11.4-0ubuntu10.13                                Xorg X server - core server
ii  xserver-xorg-input-all                            1:7.6+12ubuntu2                                      X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev                          1:2.7.0-0ubuntu1.2                                   X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse                          1:1.7.1-1build3                                      X.Org X server -- mouse input driver
ii  xserver-xorg-video-all                            1:7.6+12ubuntu2                                      X.Org X server -- output driver metapackage
ii  xserver-xorg-video-ati                            1:6.99.99~git20120913.8637f772-0ubuntu1~precise~xup2 X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-fbdev                          1:0.4.2-4ubuntu2                                     X.Org X server -- fbdev display driver
ii  xserver-xorg-video-sis                            1:0.10.3-3build2                                     X.Org X server -- SiS display driver
ii  xserver-xorg-video-vesa                           1:2.3.0-7build2                                      X.Org X server -- VESA display driver
```
*note, I removed the SiS driver to see if that would help - no dice. Also, I'm using the x-swat ppa, but the originals produced the same results.

```
lspci

00:0d.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] (rev 01)
00:0d.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 21)
```

```
sudo lspci -nnk -vvv -s 00:0d

00:0d.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] [1002:5960] (rev 01) (prog-if 00 [VGA controller])
    Subsystem: Hightech Information System Ltd. Device [1787:2020]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Region 1: I/O ports at 9400 [size=256]
    Region 2: Memory at bd000000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at 40020000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel modules: radeon, radeonfb

00:0d.1 Display controller [0380]: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] (Secondary) [1002:5940] (rev 01)
    Subsystem: Hightech Information System Ltd. Device [1787:2021]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 32 bytes
    Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at bc800000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
```

```
sudo lshw -c display

*-display UNCLAIMED     
       description: VGA compatible controller
       product: 630/730 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 21
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff memory:bd800000-bd81ffff ioport:a800(size=128)
  *-display:0 UNCLAIMED
       description: VGA compatible controller
       product: RV280 [Radeon 9200 PRO]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: d
       bus info: pci@0000:00:0d.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=32 mingnt=8
       resources: memory:e8000000-efffffff ioport:9400(size=256) memory:bd000000-bd00ffff memory:40020000-4003ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 PRO] (Secondary)
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: d.1
       bus info: pci@0000:00:0d.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 mingnt=8
       resources: memory:d8000000-dfffffff memory:bc800000-bc80ffff
```

```
lsmod

Module                  Size  Used by
snd_ice1724           107034  0 
snd_cmipci             35513  0 
snd_ice17xx_ak4xxx     13163  1 snd_ice1724
gameport               15060  1 snd_cmipci
snd_ac97_codec        110213  1 snd_ice1724
radeon                733914  0 
ac97_bus               12642  1 snd_ac97_codec
snd_ak4xxx_adda        18464  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_ak4114             14326  1 snd_ice1724
snd_pt2258             12986  1 snd_ice1724
snd_i2c                13863  2 snd_ice1724,snd_pt2258
snd_ak4113             14307  1 snd_ice1724
snd_pcm                80916  5 snd_ice1724,snd_cmipci,snd_ac97_codec,snd_ak4114,snd_ak4113
snd_opl3_lib           18863  1 snd_cmipci
snd_hwdep              13276  1 snd_opl3_lib
snd_mpu401_uart        13865  1 snd_cmipci
snd_seq_midi           13132  0 
snd_rawmidi            25424  3 snd_ice1724,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_timer              28931  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
drm                   197641  3 radeon,ttm,drm_kms_helper
ppdev                  12849  0 
snd                    62218  16 snd_ice1724,snd_cmipci,snd_ac97_codec,snd_ak4xxx_adda,snd_ak4114,snd_pt2258,snd_i2c,snd_ak4113,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
snd_page_alloc         14115  1 snd_pcm
i2c_algo_bit           13199  1 radeon
nfsd                  229909  2 
shpchp                 32265  0 
soundcore              14635  1 snd
nfs                   372273  1 
binfmt_misc            17292  1 
lockd                  78865  2 nfsd,nfs
fscache                50642  1 nfs
auth_rpcgss            39597  2 nfsd,nfs
nfs_acl                12771  2 nfsd,nfs
sunrpc                215112  12 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
parport_pc             32114  1 
mac_hid                13077  0 
i2c_sis630             13110  0 
sis_agp                13165  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
e1000                 101795  0 
usbhid                 41937  0 
hid                    77428  1 usbhid
sis900                 22729  0
```

My custom /etc/X11/xorg.conf
```
Section "Device"
    Identifier    "Diamond Stealth ATI Radeon S9250"
    Driver        "radeon"
EndSection

Section "Monitor"
    Identifier    "CTX VT202"
    VendorName    "CTX"
    ModelName     "202a"
    ModeLine    "1280x1024 75.00"  138.54  1280 1368 1504 1778  1024 1025 1028 1069  -HSync +Vsync
    ModeLine    "1280x1024 70.00"  128.94  1280 1368 1504 1728  1024 1025 1028 1066  -Hsync +Vsync
    ModeLine    "1280x1024 60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -Hsync +Vsync
    Option        "PreferredMode" "1280x1024 75.00"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Diamond Stealth ATI Radeon S9250"
    Monitor        "CTX VT202"
SubSection "Display"
    Modes        "1280x1024 75.00" "1280x1024 70.00" "1280x1024 60.00"
EndSubSection
EndSection
```

```
sudo cat /var/log/Xorg.0.log | grep EE

[ 82695.327] (EE) Failed to load module "fglrx" (module does not exist, 0)
[ 82695.402] (EE) Failed to load module "fglrx" (module does not exist, 0)
[ 82695.422] (EE) open /dev/fb0: No such file or directory

sudo cat /var/log/Xorg.0.log | grep WW

[ 82695.327] (WW) Warning, couldn't open module fglrx
[ 82695.402] (WW) Warning, couldn't open module fglrx
[ 82695.421] (WW) Falling back to old probe method for fbdev
[ 82697.219] (WW) VESA(1): Unable to estimate virtual size
```

Entire Xorg.0.log (sorry, can't seem to upload a file here)
```
[ 82694.879] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[ 82694.879] X Protocol Version 11, Revision 0
[ 82694.879] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[ 82694.879] Current Operating System: Linux rachel-TUSIM 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:21:10 UTC 2013 i686
[ 82694.879] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-51-generic root=UUID=fca70f2d-9417-4944-b66f-2af19e22ab37 ro quiet splash radeon.modeset=0
[ 82694.880] Build Date: 11 April 2013  01:04:30PM
[ 82694.880] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[ 82694.880] Current version of pixman: 0.24.4
[ 82694.880]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[ 82694.880] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 82694.880] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 15 15:59:45 2013
[ 82695.005] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 82695.075] (==) No Layout section.  Using the first Screen section.
[ 82695.075] (==) No screen section available. Using defaults.
[ 82695.075] (**) |-->Screen "Default Screen Section" (0)
[ 82695.075] (**) |   |-->Monitor "<default monitor>"
[ 82695.076] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[ 82695.076] (==) Automatically adding devices
[ 82695.076] (==) Automatically enabling devices
[ 82695.109] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 82695.109]     Entry deleted from font path.
[ 82695.109] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 82695.109]     Entry deleted from font path.
[ 82695.109] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 82695.109]     Entry deleted from font path.
[ 82695.125] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 82695.125]     Entry deleted from font path.
[ 82695.125] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 82695.125]     Entry deleted from font path.
[ 82695.125] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[ 82695.125]     Entry deleted from font path.
[ 82695.125] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[ 82695.125] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 82695.125] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 82695.125] (II) Loader magic: 0x5025a0
[ 82695.125] (II) Module ABI versions:
[ 82695.125]     X.Org ANSI C Emulation: 0.4
[ 82695.125]     X.Org Video Driver: 11.0
[ 82695.125]     X.Org XInput driver : 16.0
[ 82695.125]     X.Org Server Extension : 6.0
[ 82695.127] (--) PCI:*(0:0:13:0) 1002:5960:1787:2020 rev 1, Mem @ 0xe8000000/134217728, 0xbd000000/65536, I/O @ 0x00009400/256, BIOS @ 0x????????/131072
[ 82695.127] (--) PCI: (0:0:13:1) 1002:5940:1787:2021 rev 1, Mem @ 0xd8000000/134217728, 0xbc800000/65536
[ 82695.127] (--) PCI: (0:1:0:0) 1039:6300:1043:80e1 rev 33, Mem @ 0xf0000000/134217728, 0xbd800000/131072, I/O @ 0x0000a800/128
[ 82695.127] (II) Open ACPI successful (/var/run/acpid.socket)
[ 82695.127] (II) LoadModule: "extmod"
[ 82695.232] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 82695.233] (II) Module extmod: vendor="X.Org Foundation"
[ 82695.233]     compiled for 1.11.3, module version = 1.0.0
[ 82695.233]     Module class: X.Org Server Extension
[ 82695.233]     ABI class: X.Org Server Extension, version 6.0
[ 82695.233] (II) Loading extension MIT-SCREEN-SAVER
[ 82695.233] (II) Loading extension XFree86-VidModeExtension
[ 82695.233] (II) Loading extension XFree86-DGA
[ 82695.233] (II) Loading extension DPMS
[ 82695.233] (II) Loading extension XVideo
[ 82695.233] (II) Loading extension XVideo-MotionCompensation
[ 82695.233] (II) Loading extension X-Resource
[ 82695.233] (II) LoadModule: "dbe"
[ 82695.234] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 82695.234] (II) Module dbe: vendor="X.Org Foundation"
[ 82695.234]     compiled for 1.11.3, module version = 1.0.0
[ 82695.234]     Module class: X.Org Server Extension
[ 82695.234]     ABI class: X.Org Server Extension, version 6.0
[ 82695.234] (II) Loading extension DOUBLE-BUFFER
[ 82695.234] (II) LoadModule: "glx"
[ 82695.235] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 82695.267] (II) Module glx: vendor="X.Org Foundation"
[ 82695.267]     compiled for 1.11.3, module version = 1.0.0
[ 82695.267]     ABI class: X.Org Server Extension, version 6.0
[ 82695.267] (==) AIGLX enabled
[ 82695.267] (II) Loading extension GLX
[ 82695.267] (II) LoadModule: "record"
[ 82695.268] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 82695.268] (II) Module record: vendor="X.Org Foundation"
[ 82695.268]     compiled for 1.11.3, module version = 1.13.0
[ 82695.268]     Module class: X.Org Server Extension
[ 82695.268]     ABI class: X.Org Server Extension, version 6.0
[ 82695.268] (II) Loading extension RECORD
[ 82695.269] (II) LoadModule: "dri"
[ 82695.269] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 82695.289] (II) Module dri: vendor="X.Org Foundation"
[ 82695.289]     compiled for 1.11.3, module version = 1.0.0
[ 82695.289]     ABI class: X.Org Server Extension, version 6.0
[ 82695.289] (II) Loading extension XFree86-DRI
[ 82695.289] (II) LoadModule: "dri2"
[ 82695.290] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 82695.309] (II) Module dri2: vendor="X.Org Foundation"
[ 82695.309]     compiled for 1.11.3, module version = 1.2.0
[ 82695.309]     ABI class: X.Org Server Extension, version 6.0
[ 82695.309] (II) Loading extension DRI2
[ 82695.309] (==) Matched fglrx as autoconfigured driver 0
[ 82695.309] (==) Matched ati as autoconfigured driver 1
[ 82695.309] (==) Matched vesa as autoconfigured driver 2
[ 82695.309] (==) Matched fbdev as autoconfigured driver 3
[ 82695.309] (==) Assigned the driver to the xf86ConfigLayout
[ 82695.309] (II) LoadModule: "fglrx"
[ 82695.327] (WW) Warning, couldn't open module fglrx
[ 82695.327] (II) UnloadModule: "fglrx"
[ 82695.327] (II) Unloading fglrx
[ 82695.327] (EE) Failed to load module "fglrx" (module does not exist, 0)
[ 82695.328] (II) LoadModule: "ati"
[ 82695.329] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 82695.343] (II) Module ati: vendor="X.Org Foundation"
[ 82695.343]     compiled for 1.11.3, module version = 6.99.99
[ 82695.343]     Module class: X.Org Video Driver
[ 82695.344]     ABI class: X.Org Video Driver, version 11.0
[ 82695.344] (II) LoadModule: "radeon"
[ 82695.344] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 82695.386] (II) Module radeon: vendor="X.Org Foundation"
[ 82695.386]     compiled for 1.11.3, module version = 6.99.99
[ 82695.386]     Module class: X.Org Video Driver
[ 82695.386]     ABI class: X.Org Video Driver, version 11.0
[ 82695.386] (II) LoadModule: "vesa"
[ 82695.387] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 82695.396] (II) Module vesa: vendor="X.Org Foundation"
[ 82695.396]     compiled for 1.11.3, module version = 2.3.0
[ 82695.396]     Module class: X.Org Video Driver
[ 82695.396]     ABI class: X.Org Video Driver, version 11.0
[ 82695.396] (II) LoadModule: "fbdev"
[ 82695.397] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 82695.400] (II) Module fbdev: vendor="X.Org Foundation"
[ 82695.400]     compiled for 1.11.3, module version = 0.4.2
[ 82695.400]     ABI class: X.Org Video Driver, version 11.0
[ 82695.400] (==) Matched fglrx as autoconfigured driver 0
[ 82695.400] (==) Matched ati as autoconfigured driver 1
[ 82695.400] (==) Matched vesa as autoconfigured driver 2
[ 82695.400] (==) Matched fbdev as autoconfigured driver 3
[ 82695.400] (==) Assigned the driver to the xf86ConfigLayout
[ 82695.400] (II) LoadModule: "fglrx"
[ 82695.402] (WW) Warning, couldn't open module fglrx
[ 82695.402] (II) UnloadModule: "fglrx"
[ 82695.402] (II) Unloading fglrx
[ 82695.402] (EE) Failed to load module "fglrx" (module does not exist, 0)
[ 82695.402] (II) LoadModule: "ati"
[ 82695.403] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 82695.403] (II) Module ati: vendor="X.Org Foundation"
[ 82695.403]     compiled for 1.11.3, module version = 6.99.99
[ 82695.403]     Module class: X.Org Video Driver
[ 82695.403]     ABI class: X.Org Video Driver, version 11.0
[ 82695.403] (II) LoadModule: "vesa"
[ 82695.404] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 82695.404] (II) Module vesa: vendor="X.Org Foundation"
[ 82695.404]     compiled for 1.11.3, module version = 2.3.0
[ 82695.404]     Module class: X.Org Video Driver
[ 82695.404]     ABI class: X.Org Video Driver, version 11.0
[ 82695.404] (II) UnloadModule: "vesa"
[ 82695.404] (II) Unloading vesa
[ 82695.404] (II) Failed to load module "vesa" (already loaded, 0)
[ 82695.404] (II) LoadModule: "fbdev"
[ 82695.405] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 82695.405] (II) Module fbdev: vendor="X.Org Foundation"
[ 82695.405]     compiled for 1.11.3, module version = 0.4.2
[ 82695.405]     ABI class: X.Org Video Driver, version 11.0
[ 82695.405] (II) UnloadModule: "fbdev"
[ 82695.405] (II) Unloading fbdev
[ 82695.405] (II) Failed to load module "fbdev" (already loaded, 0)
[ 82695.405] (II) RADEON: Driver for ATI Radeon chipsets:
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
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
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
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE
[ 82695.419] (II) VESA: driver for VESA chipsets: vesa
[ 82695.419] (II) FBDEV: driver for framebuffer: fbdev
[ 82695.419] (++) using VT number 7

[ 82695.420] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 82695.420] (II) [KMS] drm report modesetting isn't supported.
[ 82695.420] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 82695.421] (WW) Falling back to old probe method for fbdev
[ 82695.421] (II) Loading sub module "fbdevhw"
[ 82695.421] (II) LoadModule: "fbdevhw"
[ 82695.421] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 82695.421] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 82695.421]     compiled for 1.11.3, module version = 0.0.2
[ 82695.422]     ABI class: X.Org Video Driver, version 11.0
[ 82695.422] (EE) open /dev/fb0: No such file or directory
[ 82695.422] (II) Loading sub module "vbe"
[ 82695.422] (II) LoadModule: "vbe"
[ 82695.423] (II) Loading /usr/lib/xorg/modules/libvbe.so
[ 82695.423] (II) Module vbe: vendor="X.Org Foundation"
[ 82695.423]     compiled for 1.11.3, module version = 1.1.0
[ 82695.423]     ABI class: X.Org Video Driver, version 11.0
[ 82695.423] (II) Loading sub module "int10"
[ 82695.423] (II) LoadModule: "int10"
[ 82695.424] (II) Loading /usr/lib/xorg/modules/libint10.so
[ 82695.424] (II) Module int10: vendor="X.Org Foundation"
[ 82695.424]     compiled for 1.11.3, module version = 1.0.0
[ 82695.424]     ABI class: X.Org Video Driver, version 11.0
[ 82695.424] (II) VESA(1): initializing int10
[ 82695.428] (II) VESA(1): Primary V_BIOS segment is: 0xc000
[ 82695.429] (II) VESA(1): VESA BIOS detected
[ 82695.430] (II) VESA(1): VESA VBE Version 2.0
[ 82695.430] (II) VESA(1): VESA VBE Total Mem: 16384 kB
[ 82695.430] (II) VESA(1): VESA VBE OEM: ATI RADEON 9200
[ 82695.430] (II) VESA(1): VESA VBE OEM Software Rev: 1.0
[ 82695.430] (II) VESA(1): VESA VBE OEM Vendor: ATI Technologies Inc.
[ 82695.430] (II) VESA(1): VESA VBE OEM Product: V280
[ 82695.430] (II) VESA(1): VESA VBE OEM Product Rev: 01.00
[ 82695.733] (II) VESA(1): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[ 82695.733] (==) VESA(1): Depth 24, (--) framebuffer bpp 32
[ 82695.733] (==) VESA(1): RGB weight 888
[ 82695.733] (==) VESA(1): Default visual is TrueColor
[ 82695.733] (==) VESA(1): Using gamma correction (1.0, 1.0, 1.0)
[ 82695.733] (II) Loading sub module "ddc"
[ 82695.733] (II) LoadModule: "ddc"
[ 82695.733] (II) Module "ddc" already built-in
[ 82695.811] (II) VESA(1): VESA VBE DDC supported
[ 82695.811] (II) VESA(1): VESA VBE DDC Level 2
[ 82695.812] (II) VESA(1): VESA VBE DDC transfer in appr. 2 sec.
[ 82696.862] (II) VESA(1): VESA VBE DDC read successfully
[ 82696.862] (II) VESA(1): Manufacturer: CTX  Model: 202a  Serial#: 0
[ 82696.862] (II) VESA(1): Year: 2005  Week: 46
[ 82696.862] (II) VESA(1): EDID Version: 1.3
[ 82696.862] (II) VESA(1): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[ 82696.862] (II) VESA(1): Sync:  Separate
[ 82696.862] (II) VESA(1): Max Image Size [cm]: horiz.: 34  vert.: 27
[ 82696.863] (II) VESA(1): Gamma: 2.20
[ 82696.863] (II) VESA(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[ 82696.863] (II) VESA(1): First detailed timing not preferred mode in violation of standard!
[ 82696.863] (II) VESA(1): redX: 0.637 redY: 0.348   greenX: 0.290 greenY: 0.610
[ 82696.863] (II) VESA(1): blueX: 0.137 blueY: 0.080   whiteX: 0.310 whiteY: 0.330
[ 82696.863] (II) VESA(1): Supported established timings:
[ 82696.863] (II) VESA(1): 720x400@70Hz
[ 82696.863] (II) VESA(1): 640x480@60Hz
[ 82696.863] (II) VESA(1): 640x480@72Hz
[ 82696.863] (II) VESA(1): 640x480@75Hz
[ 82696.863] (II) VESA(1): 800x600@56Hz
[ 82696.863] (II) VESA(1): 800x600@60Hz
[ 82696.863] (II) VESA(1): 800x600@72Hz
[ 82696.863] (II) VESA(1): 800x600@75Hz
[ 82696.863] (II) VESA(1): 1024x768@60Hz
[ 82696.863] (II) VESA(1): 1024x768@70Hz
[ 82696.863] (II) VESA(1): 1024x768@75Hz
[ 82696.863] (II) VESA(1): 1280x1024@75Hz
[ 82696.863] (II) VESA(1): Manufacturer's mask: 0
[ 82696.863] (II) VESA(1): Supported detailed timing:
[ 82696.863] (II) VESA(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
[ 82696.863] (II) VESA(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[ 82696.863] (II) VESA(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[ 82696.863] (II) VESA(1): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 145 MHz
[ 82696.863] (II) VESA(1): Serial No: LE554601055
[ 82696.863] (II) VESA(1): Monitor name: X782
[ 82696.863] (II) VESA(1): EDID (in hex):
[ 82696.863] (II) VESA(1):     00ffffffffffff000e982a2000000000
[ 82696.863] (II) VESA(1):     2e0f010308221b78e80526a3594a9c23
[ 82696.863] (II) VESA(1):     144f54afcf0001010101010101010101
[ 82696.863] (II) VESA(1):     010101010101302a009851002a403070
[ 82696.863] (II) VESA(1):     1300520e1100001e000000fd00384b1e
[ 82696.864] (II) VESA(1):     500e000a202020202020000000ff004c
[ 82696.864] (II) VESA(1):     453535343630313035350a20000000fc
[ 82696.864] (II) VESA(1):     00583738320a2020202020202020007e
[ 82696.864] (II) VESA(1): EDID vendor "CTX", prod id 8234
[ 82696.864] (II) VESA(1): Using EDID range info for horizontal sync
[ 82696.864] (II) VESA(1): Using EDID range info for vertical refresh
[ 82696.864] (II) VESA(1): Printing DDC gathered Modelines:
[ 82696.864] (II) VESA(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 82696.864] (II) VESA(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 82696.864] (II) VESA(1): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[ 82696.864] (II) VESA(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[ 82696.864] (II) VESA(1): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[ 82696.864] (II) VESA(1): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 82696.864] (II) VESA(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[ 82696.864] (II) VESA(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[ 82696.864] (II) VESA(1): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[ 82696.864] (II) VESA(1): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[ 82696.864] (II) VESA(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 82696.864] (II) VESA(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[ 82696.864] (II) VESA(1): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[ 82696.864] (II) VESA(1): Searching for matching VESA mode(s):
[ 82696.872] Mode: 6a (800x600)
[ 82696.872]     ModeAttributes: 0x1b
[ 82696.872]     WinAAttributes: 0x7
[ 82696.872]     WinBAttributes: 0x0
[ 82696.872]     WinGranularity: 64
[ 82696.872]     WinSize: 64
[ 82696.872]     WinASegment: 0xa000
[ 82696.872]     WinBSegment: 0xa000
[ 82696.872]     WinFuncPtr: 0xc0005406
[ 82696.872]     BytesPerScanline: 100
[ 82696.872]     XResolution: 800
[ 82696.872]     YResolution: 600
[ 82696.872]     XCharSize: 8
[ 82696.872]     YCharSize: 14
[ 82696.872]     NumberOfPlanes: 4
[ 82696.872]     BitsPerPixel: 4
[ 82696.873]     NumberOfBanks: 1
[ 82696.873]     MemoryModel: 3
[ 82696.873]     BankSize: 0
[ 82696.873]     NumberOfImages: 3
[ 82696.873]     RedMaskSize: 0
[ 82696.873]     RedFieldPosition: 0
[ 82696.873]     GreenMaskSize: 0
[ 82696.873]     GreenFieldPosition: 0
[ 82696.873]     BlueMaskSize: 0
[ 82696.873]     BlueFieldPosition: 0
[ 82696.873]     RsvdMaskSize: 0
[ 82696.873]     RsvdFieldPosition: 0
[ 82696.873]     DirectColorModeInfo: 0
[ 82696.873]     PhysBasePtr: 0x0
[ 82696.880] Mode: 102 (800x600)
[ 82696.880]     ModeAttributes: 0x1b
[ 82696.880]     WinAAttributes: 0x7
[ 82696.880]     WinBAttributes: 0x0
[ 82696.880]     WinGranularity: 64
[ 82696.880]     WinSize: 64
[ 82696.880]     WinASegment: 0xa000
[ 82696.880]     WinBSegment: 0xa000
[ 82696.880]     WinFuncPtr: 0xc0005406
[ 82696.880]     BytesPerScanline: 100
[ 82696.881]     XResolution: 800
[ 82696.881]     YResolution: 600
[ 82696.881]     XCharSize: 8
[ 82696.881]     YCharSize: 14
[ 82696.881]     NumberOfPlanes: 4
[ 82696.881]     BitsPerPixel: 4
[ 82696.881]     NumberOfBanks: 1
[ 82696.881]     MemoryModel: 3
[ 82696.881]     BankSize: 0
[ 82696.881]     NumberOfImages: 3
[ 82696.881]     RedMaskSize: 0
[ 82696.881]     RedFieldPosition: 0
[ 82696.881]     GreenMaskSize: 0
[ 82696.881]     GreenFieldPosition: 0
[ 82696.881]     BlueMaskSize: 0
[ 82696.881]     BlueFieldPosition: 0
[ 82696.881]     RsvdMaskSize: 0
[ 82696.881]     RsvdFieldPosition: 0
[ 82696.881]     DirectColorModeInfo: 0
[ 82696.881]     PhysBasePtr: 0x0
[ 82696.889] Mode: 104 (1024x768)
[ 82696.889]     ModeAttributes: 0x1b
[ 82696.889]     WinAAttributes: 0x7
[ 82696.889]     WinBAttributes: 0x0
[ 82696.889]     WinGranularity: 64
[ 82696.889]     WinSize: 64
[ 82696.889]     WinASegment: 0xa000
[ 82696.889]     WinBSegment: 0xa000
[ 82696.889]     WinFuncPtr: 0xc0005406
[ 82696.889]     BytesPerScanline: 128
[ 82696.889]     XResolution: 1024
[ 82696.889]     YResolution: 768
[ 82696.889]     XCharSize: 8
[ 82696.889]     YCharSize: 16
[ 82696.889]     NumberOfPlanes: 4
[ 82696.889]     BitsPerPixel: 4
[ 82696.889]     NumberOfBanks: 1
[ 82696.889]     MemoryModel: 3
[ 82696.889]     BankSize: 0
[ 82696.889]     NumberOfImages: 1
[ 82696.889]     RedMaskSize: 0
[ 82696.889]     RedFieldPosition: 0
[ 82696.889]     GreenMaskSize: 0
[ 82696.889]     GreenFieldPosition: 0
[ 82696.889]     BlueMaskSize: 0
[ 82696.889]     BlueFieldPosition: 0
[ 82696.889]     RsvdMaskSize: 0
[ 82696.889]     RsvdFieldPosition: 0
[ 82696.889]     DirectColorModeInfo: 0
[ 82696.889]     PhysBasePtr: 0x0
[ 82696.893] Mode: 182 (320x200)
[ 82696.893]     ModeAttributes: 0xbb
[ 82696.893]     WinAAttributes: 0x7
[ 82696.893]     WinBAttributes: 0x0
[ 82696.893]     WinGranularity: 64
[ 82696.893]     WinSize: 64
[ 82696.893]     WinASegment: 0xa000
[ 82696.893]     WinBSegment: 0xa000
[ 82696.893]     WinFuncPtr: 0xc0005406
[ 82696.893]     BytesPerScanline: 320
[ 82696.893]     XResolution: 320
[ 82696.893]     YResolution: 200
[ 82696.893]     XCharSize: 8
[ 82696.893]     YCharSize: 8
[ 82696.893]     NumberOfPlanes: 1
[ 82696.893]     BitsPerPixel: 8
[ 82696.893]     NumberOfBanks: 1
[ 82696.893]     MemoryModel: 4
[ 82696.894]     BankSize: 0
[ 82696.894]     NumberOfImages: 254
[ 82696.894]     RedMaskSize: 0
[ 82696.894]     RedFieldPosition: 0
[ 82696.894]     GreenMaskSize: 0
[ 82696.894]     GreenFieldPosition: 0
[ 82696.894]     BlueMaskSize: 0
[ 82696.894]     BlueFieldPosition: 0
[ 82696.894]     RsvdMaskSize: 0
[ 82696.894]     RsvdFieldPosition: 0
[ 82696.894]     DirectColorModeInfo: 0
[ 82696.894]     PhysBasePtr: 0xe8000000
[ 82696.897] Mode: 10d (320x200)
[ 82696.897]     ModeAttributes: 0xbb
[ 82696.897]     WinAAttributes: 0x7
[ 82696.897]     WinBAttributes: 0x0
[ 82696.897]     WinGranularity: 64
[ 82696.897]     WinSize: 64
[ 82696.897]     WinASegment: 0xa000
[ 82696.897]     WinBSegment: 0xa000
[ 82696.897]     WinFuncPtr: 0xc0005406
[ 82696.897]     BytesPerScanline: 640
[ 82696.897]     XResolution: 320
[ 82696.897]     YResolution: 200
[ 82696.897]     XCharSize: 8
[ 82696.898]     YCharSize: 8
[ 82696.898]     NumberOfPlanes: 1
[ 82696.898]     BitsPerPixel: 15
[ 82696.898]     NumberOfBanks: 1
[ 82696.898]     MemoryModel: 6
[ 82696.898]     BankSize: 0
[ 82696.898]     NumberOfImages: 127
[ 82696.898]     RedMaskSize: 5
[ 82696.898]     RedFieldPosition: 10
[ 82696.898]     GreenMaskSize: 5
[ 82696.898]     GreenFieldPosition: 5
[ 82696.898]     BlueMaskSize: 5
[ 82696.898]     BlueFieldPosition: 0
[ 82696.898]     RsvdMaskSize: 0
[ 82696.898]     RsvdFieldPosition: 0
[ 82696.898]     DirectColorModeInfo: 0
[ 82696.898]     PhysBasePtr: 0xe8000000
[ 82696.901] Mode: 10e (320x200)
[ 82696.901]     ModeAttributes: 0xbb
[ 82696.901]     WinAAttributes: 0x7
[ 82696.901]     WinBAttributes: 0x0
[ 82696.901]     WinGranularity: 64
[ 82696.901]     WinSize: 64
[ 82696.901]     WinASegment: 0xa000
[ 82696.901]     WinBSegment: 0xa000
[ 82696.901]     WinFuncPtr: 0xc0005406
[ 82696.901]     BytesPerScanline: 640
[ 82696.901]     XResolution: 320
[ 82696.901]     YResolution: 200
[ 82696.901]     XCharSize: 8
[ 82696.902]     YCharSize: 8
[ 82696.902]     NumberOfPlanes: 1
[ 82696.902]     BitsPerPixel: 16
[ 82696.902]     NumberOfBanks: 1
[ 82696.902]     MemoryModel: 6
[ 82696.902]     BankSize: 0
[ 82696.902]     NumberOfImages: 127
[ 82696.902]     RedMaskSize: 5
[ 82696.902]     RedFieldPosition: 11
[ 82696.902]     GreenMaskSize: 6
[ 82696.902]     GreenFieldPosition: 5
[ 82696.902]     BlueMaskSize: 5
[ 82696.902]     BlueFieldPosition: 0
[ 82696.902]     RsvdMaskSize: 0
[ 82696.902]     RsvdFieldPosition: 0
[ 82696.902]     DirectColorModeInfo: 0
[ 82696.902]     PhysBasePtr: 0xe8000000
[ 82696.905] Mode: 10f (320x200)
[ 82696.905]     ModeAttributes: 0xbb
[ 82696.905]     WinAAttributes: 0x7
[ 82696.905]     WinBAttributes: 0x0
[ 82696.905]     WinGranularity: 64
[ 82696.905]     WinSize: 64
[ 82696.905]     WinASegment: 0xa000
[ 82696.905]     WinBSegment: 0xa000
[ 82696.905]     WinFuncPtr: 0xc0005406
[ 82696.905]     BytesPerScanline: 960
[ 82696.905]     XResolution: 320
[ 82696.905]     YResolution: 200
[ 82696.906]     XCharSize: 8
[ 82696.906]     YCharSize: 8
[ 82696.906]     NumberOfPlanes: 1
[ 82696.906]     BitsPerPixel: 24
[ 82696.906]     NumberOfBanks: 1
[ 82696.906]     MemoryModel: 6
[ 82696.906]     BankSize: 0
[ 82696.906]     NumberOfImages: 84
[ 82696.906]     RedMaskSize: 8
[ 82696.906]     RedFieldPosition: 16
[ 82696.906]     GreenMaskSize: 8
[ 82696.906]     GreenFieldPosition: 8
[ 82696.906]     BlueMaskSize: 8
[ 82696.906]     BlueFieldPosition: 0
[ 82696.906]     RsvdMaskSize: 0
[ 82696.906]     RsvdFieldPosition: 0
[ 82696.906]     DirectColorModeInfo: 0
[ 82696.906]     PhysBasePtr: 0xe8000000
[ 82696.909] *Mode: 120 (320x200)
[ 82696.909]     ModeAttributes: 0xbb
[ 82696.909]     WinAAttributes: 0x7
[ 82696.909]     WinBAttributes: 0x0
[ 82696.909]     WinGranularity: 64
[ 82696.909]     WinSize: 64
[ 82696.909]     WinASegment: 0xa000
[ 82696.909]     WinBSegment: 0xa000
[ 82696.909]     WinFuncPtr: 0xc0005406
[ 82696.909]     BytesPerScanline: 1280
[ 82696.909]     XResolution: 320
[ 82696.910]     YResolution: 200
[ 82696.910]     XCharSize: 8
[ 82696.910]     YCharSize: 8
[ 82696.910]     NumberOfPlanes: 1
[ 82696.910]     BitsPerPixel: 32
[ 82696.910]     NumberOfBanks: 1
[ 82696.910]     MemoryModel: 6
[ 82696.910]     BankSize: 0
[ 82696.910]     NumberOfImages: 63
[ 82696.910]     RedMaskSize: 8
[ 82696.910]     RedFieldPosition: 16
[ 82696.910]     GreenMaskSize: 8
[ 82696.910]     GreenFieldPosition: 8
[ 82696.910]     BlueMaskSize: 8
[ 82696.910]     BlueFieldPosition: 0
[ 82696.910]     RsvdMaskSize: 0
[ 82696.910]     RsvdFieldPosition: 0
[ 82696.910]     DirectColorModeInfo: 0
[ 82696.910]     PhysBasePtr: 0xe8000000
[ 82696.913] Mode: 192 (320x240)
[ 82696.914]     ModeAttributes: 0xbb
[ 82696.914]     WinAAttributes: 0x7
[ 82696.914]     WinBAttributes: 0x0
[ 82696.914]     WinGranularity: 64
[ 82696.914]     WinSize: 64
[ 82696.914]     WinASegment: 0xa000
[ 82696.914]     WinBSegment: 0xa000
[ 82696.914]     WinFuncPtr: 0xc0005406
[ 82696.914]     BytesPerScanline: 320
[ 82696.914]     XResolution: 320
[ 82696.914]     YResolution: 240
[ 82696.914]     XCharSize: 8
[ 82696.914]     YCharSize: 8
[ 82696.914]     NumberOfPlanes: 1
[ 82696.914]     BitsPerPixel: 8
[ 82696.914]     NumberOfBanks: 1
[ 82696.914]     MemoryModel: 4
[ 82696.914]     BankSize: 0
[ 82696.914]     NumberOfImages: 127
[ 82696.914]     RedMaskSize: 0
[ 82696.914]     RedFieldPosition: 0
[ 82696.914]     GreenMaskSize: 0
[ 82696.914]     GreenFieldPosition: 0
[ 82696.914]     BlueMaskSize: 0
[ 82696.914]     BlueFieldPosition: 0
[ 82696.914]     RsvdMaskSize: 0
[ 82696.914]     RsvdFieldPosition: 0
[ 82696.914]     DirectColorModeInfo: 0
[ 82696.914]     PhysBasePtr: 0xe8000000
[ 82696.918] Mode: 193 (320x240)
[ 82696.918]     ModeAttributes: 0xbb
[ 82696.918]     WinAAttributes: 0x7
[ 82696.918]     WinBAttributes: 0x0
[ 82696.918]     WinGranularity: 64
[ 82696.918]     WinSize: 64
[ 82696.918]     WinASegment: 0xa000
[ 82696.918]     WinBSegment: 0xa000
[ 82696.918]     WinFuncPtr: 0xc0005406
[ 82696.918]     BytesPerScanline: 640
[ 82696.918]     XResolution: 320
[ 82696.918]     YResolution: 240
[ 82696.918]     XCharSize: 8
[ 82696.918]     YCharSize: 8
[ 82696.918]     NumberOfPlanes: 1
[ 82696.918]     BitsPerPixel: 15
[ 82696.918]     NumberOfBanks: 1
[ 82696.918]     MemoryModel: 6
[ 82696.918]     BankSize: 0
[ 82696.918]     NumberOfImages: 84
[ 82696.918]     RedMaskSize: 5
[ 82696.918]     RedFieldPosition: 10
[ 82696.918]     GreenMaskSize: 5
[ 82696.918]     GreenFieldPosition: 5
[ 82696.918]     BlueMaskSize: 5
[ 82696.918]     BlueFieldPosition: 0
[ 82696.918]     RsvdMaskSize: 0
[ 82696.918]     RsvdFieldPosition: 0
[ 82696.918]     DirectColorModeInfo: 0
[ 82696.918]     PhysBasePtr: 0xe8000000
[ 82696.922] Mode: 194 (320x240)
[ 82696.922]     ModeAttributes: 0xbb
[ 82696.922]     WinAAttributes: 0x7
[ 82696.922]     WinBAttributes: 0x0
[ 82696.922]     WinGranularity: 64
[ 82696.922]     WinSize: 64
[ 82696.922]     WinASegment: 0xa000
[ 82696.922]     WinBSegment: 0xa000
[ 82696.922]     WinFuncPtr: 0xc0005406
[ 82696.922]     BytesPerScanline: 640
[ 82696.922]     XResolution: 320
[ 82696.922]     YResolution: 240
[ 82696.922]     XCharSize: 8
[ 82696.922]     YCharSize: 8
[ 82696.922]     NumberOfPlanes: 1
[ 82696.922]     BitsPerPixel: 16
[ 82696.922]     NumberOfBanks: 1
[ 82696.922]     MemoryModel: 6
[ 82696.922]     BankSize: 0
[ 82696.922]     NumberOfImages: 84
[ 82696.922]     RedMaskSize: 5
[ 82696.922]     RedFieldPosition: 11
[ 82696.922]     GreenMaskSize: 6
[ 82696.922]     GreenFieldPosition: 5
[ 82696.922]     BlueMaskSize: 5
[ 82696.922]     BlueFieldPosition: 0
[ 82696.922]     RsvdMaskSize: 0
[ 82696.922]     RsvdFieldPosition: 0
[ 82696.923]     DirectColorModeInfo: 0
[ 82696.923]     PhysBasePtr: 0xe8000000
[ 82696.926] Mode: 195 (320x240)
[ 82696.926]     ModeAttributes: 0xbb
[ 82696.926]     WinAAttributes: 0x7
[ 82696.926]     WinBAttributes: 0x0
[ 82696.926]     WinGranularity: 64
[ 82696.926]     WinSize: 64
[ 82696.926]     WinASegment: 0xa000
[ 82696.926]     WinBSegment: 0xa000
[ 82696.926]     WinFuncPtr: 0xc0005406
[ 82696.926]     BytesPerScanline: 960
[ 82696.926]     XResolution: 320
[ 82696.926]     YResolution: 240
[ 82696.926]     XCharSize: 8
[ 82696.926]     YCharSize: 8
[ 82696.926]     NumberOfPlanes: 1
[ 82696.926]     BitsPerPixel: 24
[ 82696.926]     NumberOfBanks: 1
[ 82696.926]     MemoryModel: 6
[ 82696.926]     BankSize: 0
[ 82696.926]     NumberOfImages: 63
[ 82696.926]     RedMaskSize: 8
[ 82696.926]     RedFieldPosition: 16
[ 82696.926]     GreenMaskSize: 8
[ 82696.927]     GreenFieldPosition: 8
[ 82696.927]     BlueMaskSize: 8
[ 82696.927]     BlueFieldPosition: 0
[ 82696.927]     RsvdMaskSize: 0
[ 82696.927]     RsvdFieldPosition: 0
[ 82696.927]     DirectColorModeInfo: 0
[ 82696.927]     PhysBasePtr: 0xe8000000
[ 82696.930] *Mode: 196 (320x240)
[ 82696.930]     ModeAttributes: 0xbb
[ 82696.930]     WinAAttributes: 0x7
[ 82696.930]     WinBAttributes: 0x0
[ 82696.930]     WinGranularity: 64
[ 82696.930]     WinSize: 64
[ 82696.930]     WinASegment: 0xa000
[ 82696.930]     WinBSegment: 0xa000
[ 82696.930]     WinFuncPtr: 0xc0005406
[ 82696.930]     BytesPerScanline: 1280
[ 82696.930]     XResolution: 320
[ 82696.930]     YResolution: 240
[ 82696.930]     XCharSize: 8
[ 82696.930]     YCharSize: 8
[ 82696.930]     NumberOfPlanes: 1
[ 82696.930]     BitsPerPixel: 32
[ 82696.931]     NumberOfBanks: 1
[ 82696.931]     MemoryModel: 6
[ 82696.931]     BankSize: 0
[ 82696.931]     NumberOfImages: 50
[ 82696.931]     RedMaskSize: 8
[ 82696.931]     RedFieldPosition: 16
[ 82696.931]     GreenMaskSize: 8
[ 82696.931]     GreenFieldPosition: 8
[ 82696.931]     BlueMaskSize: 8
[ 82696.931]     BlueFieldPosition: 0
[ 82696.931]     RsvdMaskSize: 0
[ 82696.931]     RsvdFieldPosition: 0
[ 82696.931]     DirectColorModeInfo: 0
[ 82696.931]     PhysBasePtr: 0xe8000000
[ 82696.938] Mode: 1a2 (400x300)
[ 82696.938]     ModeAttributes: 0xbb
[ 82696.938]     WinAAttributes: 0x7
[ 82696.939]     WinBAttributes: 0x0
[ 82696.939]     WinGranularity: 64
[ 82696.939]     WinSize: 64
[ 82696.939]     WinASegment: 0xa000
[ 82696.939]     WinBSegment: 0xa000
[ 82696.939]     WinFuncPtr: 0xc0005406
[ 82696.939]     BytesPerScanline: 400
[ 82696.939]     XResolution: 400
[ 82696.939]     YResolution: 300
[ 82696.939]     XCharSize: 8
[ 82696.939]     YCharSize: 16
[ 82696.939]     NumberOfPlanes: 1
[ 82696.939]     BitsPerPixel: 8
[ 82696.939]     NumberOfBanks: 1
[ 82696.939]     MemoryModel: 4
[ 82696.939]     BankSize: 0
[ 82696.939]     NumberOfImages: 127
[ 82696.939]     RedMaskSize: 0
[ 82696.939]     RedFieldPosition: 0
[ 82696.939]     GreenMaskSize: 0
[ 82696.939]     GreenFieldPosition: 0
[ 82696.939]     BlueMaskSize: 0
[ 82696.939]     BlueFieldPosition: 0
[ 82696.939]     RsvdMaskSize: 0
[ 82696.939]     RsvdFieldPosition: 0
[ 82696.939]     DirectColorModeInfo: 0
[ 82696.939]     PhysBasePtr: 0xe8000000
[ 82696.947] Mode: 1a3 (400x300)
[ 82696.951]     ModeAttributes: 0xbb
[ 82696.951]     WinAAttributes: 0x7
[ 82696.951]     WinBAttributes: 0x0
[ 82696.951]     WinGranularity: 64
[ 82696.951]     WinSize: 64
[ 82696.951]     WinASegment: 0xa000
[ 82696.951]     WinBSegment: 0xa000
[ 82696.951]     WinFuncPtr: 0xc0005406
[ 82696.951]     BytesPerScanline: 800
[ 82696.951]     XResolution: 400
[ 82696.951]     YResolution: 300
[ 82696.951]     XCharSize: 8
[ 82696.951]     YCharSize: 16
[ 82696.951]     NumberOfPlanes: 1
[ 82696.951]     BitsPerPixel: 15
[ 82696.951]     NumberOfBanks: 1
[ 82696.951]     MemoryModel: 6
[ 82696.951]     BankSize: 0
[ 82696.951]     NumberOfImages: 63
[ 82696.951]     RedMaskSize: 5
[ 82696.951]     RedFieldPosition: 10
[ 82696.951]     GreenMaskSize: 5
[ 82696.952]     GreenFieldPosition: 5
[ 82696.952]     BlueMaskSize: 5
[ 82696.952]     BlueFieldPosition: 0
[ 82696.952]     RsvdMaskSize: 0
[ 82696.952]     RsvdFieldPosition: 0
[ 82696.952]     DirectColorModeInfo: 0
[ 82696.952]     PhysBasePtr: 0xe8000000
[ 82696.960] Mode: 1a4 (400x300)
[ 82696.960]     ModeAttributes: 0xbb
[ 82696.960]     WinAAttributes: 0x7
[ 82696.960]     WinBAttributes: 0x0
[ 82696.960]     WinGranularity: 64
[ 82696.960]     WinSize: 64
[ 82696.960]     WinASegment: 0xa000
[ 82696.960]     WinBSegment: 0xa000
[ 82696.960]     WinFuncPtr: 0xc0005406
[ 82696.960]     BytesPerScanline: 800
[ 82696.960]     XResolution: 400
[ 82696.960]     YResolution: 300
[ 82696.960]     XCharSize: 8
[ 82696.960]     YCharSize: 16
[ 82696.960]     NumberOfPlanes: 1
[ 82696.960]     BitsPerPixel: 16
[ 82696.960]     NumberOfBanks: 1
[ 82696.960]     MemoryModel: 6
[ 82696.960]     BankSize: 0
[ 82696.960]     NumberOfImages: 63
[ 82696.960]     RedMaskSize: 5
[ 82696.960]     RedFieldPosition: 11
[ 82696.960]     GreenMaskSize: 6
[ 82696.960]     GreenFieldPosition: 5
[ 82696.960]     BlueMaskSize: 5
[ 82696.960]     BlueFieldPosition: 0
[ 82696.960]     RsvdMaskSize: 0
[ 82696.960]     RsvdFieldPosition: 0
[ 82696.960]     DirectColorModeInfo: 0
[ 82696.960]     PhysBasePtr: 0xe8000000
[ 82696.968] Mode: 1a5 (400x300)
[ 82696.968]     ModeAttributes: 0xbb
[ 82696.968]     WinAAttributes: 0x7
[ 82696.968]     WinBAttributes: 0x0
[ 82696.968]     WinGranularity: 64
[ 82696.968]     WinSize: 64
[ 82696.968]     WinASegment: 0xa000
[ 82696.968]     WinBSegment: 0xa000
[ 82696.968]     WinFuncPtr: 0xc0005406
[ 82696.968]     BytesPerScanline: 1200
[ 82696.968]     XResolution: 400
[ 82696.968]     YResolution: 300
[ 82696.968]     XCharSize: 8
[ 82696.968]     YCharSize: 16
[ 82696.968]     NumberOfPlanes: 1
[ 82696.968]     BitsPerPixel: 24
[ 82696.968]     NumberOfBanks: 1
[ 82696.968]     MemoryModel: 6
[ 82696.968]     BankSize: 0
[ 82696.968]     NumberOfImages: 41
[ 82696.968]     RedMaskSize: 8
[ 82696.968]     RedFieldPosition: 16
[ 82696.968]     GreenMaskSize: 8
[ 82696.969]     GreenFieldPosition: 8
[ 82696.969]     BlueMaskSize: 8
[ 82696.969]     BlueFieldPosition: 0
[ 82696.969]     RsvdMaskSize: 0
[ 82696.969]     RsvdFieldPosition: 0
[ 82696.969]     DirectColorModeInfo: 0
[ 82696.969]     PhysBasePtr: 0xe8000000
[ 82696.977] *Mode: 1a6 (400x300)
[ 82696.977]     ModeAttributes: 0xbb
[ 82696.977]     WinAAttributes: 0x7
[ 82696.977]     WinBAttributes: 0x0
[ 82696.977]     WinGranularity: 64
[ 82696.977]     WinSize: 64
[ 82696.977]     WinASegment: 0xa000
[ 82696.977]     WinBSegment: 0xa000
[ 82696.977]     WinFuncPtr: 0xc0005406
[ 82696.977]     BytesPerScanline: 1600
[ 82696.977]     XResolution: 400
[ 82696.977]     YResolution: 300
[ 82696.977]     XCharSize: 8
[ 82696.977]     YCharSize: 16
[ 82696.977]     NumberOfPlanes: 1
[ 82696.977]     BitsPerPixel: 32
[ 82696.977]     NumberOfBanks: 1
[ 82696.977]     MemoryModel: 6
[ 82696.977]     BankSize: 0
[ 82696.977]     NumberOfImages: 31
[ 82696.977]     RedMaskSize: 8
[ 82696.977]     RedFieldPosition: 16
[ 82696.977]     GreenMaskSize: 8
[ 82696.977]     GreenFieldPosition: 8
[ 82696.977]     BlueMaskSize: 8
[ 82696.977]     BlueFieldPosition: 0
[ 82696.977]     RsvdMaskSize: 0
[ 82696.977]     RsvdFieldPosition: 0
[ 82696.977]     DirectColorModeInfo: 0
[ 82696.977]     PhysBasePtr: 0xe8000000
[ 82696.981] Mode: 1b2 (512x384)
[ 82696.981]     ModeAttributes: 0xbb
[ 82696.981]     WinAAttributes: 0x7
[ 82696.981]     WinBAttributes: 0x0
[ 82696.981]     WinGranularity: 64
[ 82696.981]     WinSize: 64
[ 82696.981]     WinASegment: 0xa000
[ 82696.981]     WinBSegment: 0xa000
[ 82696.981]     WinFuncPtr: 0xc0005406
[ 82696.981]     BytesPerScanline: 512
[ 82696.981]     XResolution: 512
[ 82696.981]     YResolution: 384
[ 82696.981]     XCharSize: 8
[ 82696.981]     YCharSize: 16
[ 82696.981]     NumberOfPlanes: 1
[ 82696.981]     BitsPerPixel: 8
[ 82696.981]     NumberOfBanks: 1
[ 82696.981]     MemoryModel: 4
[ 82696.981]     BankSize: 0
[ 82696.981]     NumberOfImages: 84
[ 82696.981]     RedMaskSize: 0
[ 82696.981]     RedFieldPosition: 0
[ 82696.981]     GreenMaskSize: 0
[ 82696.981]     GreenFieldPosition: 0
[ 82696.981]     BlueMaskSize: 0
[ 82696.981]     BlueFieldPosition: 0
[ 82696.981]     RsvdMaskSize: 0
[ 82696.981]     RsvdFieldPosition: 0
[ 82696.981]     DirectColorModeInfo: 0
[ 82696.981]     PhysBasePtr: 0xe8000000
[ 82696.985] Mode: 1b3 (512x384)
[ 82696.985]     ModeAttributes: 0xbb
[ 82696.985]     WinAAttributes: 0x7
[ 82696.985]     WinBAttributes: 0x0
[ 82696.985]     WinGranularity: 64
[ 82696.985]     WinSize: 64
[ 82696.985]     WinASegment: 0xa000
[ 82696.985]     WinBSegment: 0xa000
[ 82696.985]     WinFuncPtr: 0xc0005406
[ 82696.985]     BytesPerScanline: 1024
[ 82696.985]     XResolution: 512
[ 82696.985]     YResolution: 384
[ 82696.985]     XCharSize: 8
[ 82696.985]     YCharSize: 16
[ 82696.985]     NumberOfPlanes: 1
[ 82696.985]     BitsPerPixel: 15
[ 82696.985]     NumberOfBanks: 1
[ 82696.985]     MemoryModel: 6
[ 82696.985]     BankSize: 0
[ 82696.985]     NumberOfImages: 41
[ 82696.985]     RedMaskSize: 5
[ 82696.985]     RedFieldPosition: 10
[ 82696.985]     GreenMaskSize: 5
[ 82696.985]     GreenFieldPosition: 5
[ 82696.985]     BlueMaskSize: 5
[ 82696.986]     BlueFieldPosition: 0
[ 82696.986]     RsvdMaskSize: 0
[ 82696.986]     RsvdFieldPosition: 0
[ 82696.986]     DirectColorModeInfo: 0
[ 82696.986]     PhysBasePtr: 0xe8000000
[ 82696.989] Mode: 1b4 (512x384)
[ 82696.989]     ModeAttributes: 0xbb
[ 82696.989]     WinAAttributes: 0x7
[ 82696.989]     WinBAttributes: 0x0
[ 82696.989]     WinGranularity: 64
[ 82696.989]     WinSize: 64
[ 82696.989]     WinASegment: 0xa000
[ 82696.989]     WinBSegment: 0xa000
[ 82696.989]     WinFuncPtr: 0xc0005406
[ 82696.989]     BytesPerScanline: 1024
[ 82696.989]     XResolution: 512
[ 82696.989]     YResolution: 384
[ 82696.989]     XCharSize: 8
[ 82696.989]     YCharSize: 16
[ 82696.989]     NumberOfPlanes: 1
[ 82696.989]     BitsPerPixel: 16
[ 82696.990]     NumberOfBanks: 1
[ 82696.990]     MemoryModel: 6
[ 82696.990]     BankSize: 0
[ 82696.990]     NumberOfImages: 41
[ 82696.990]     RedMaskSize: 5
[ 82696.990]     RedFieldPosition: 11
[ 82696.990]     GreenMaskSize: 6
[ 82696.990]     GreenFieldPosition: 5
[ 82696.990]     BlueMaskSize: 5
[ 82696.990]     BlueFieldPosition: 0
[ 82696.990]     RsvdMaskSize: 0
[ 82696.990]     RsvdFieldPosition: 0
[ 82696.990]     DirectColorModeInfo: 0
[ 82696.990]     PhysBasePtr: 0xe8000000
[ 82696.993] Mode: 1b5 (512x384)
[ 82696.993]     ModeAttributes: 0xbb
[ 82696.993]     WinAAttributes: 0x7
[ 82696.993]     WinBAttributes: 0x0
[ 82696.994]     WinGranularity: 64
[ 82696.994]     WinSize: 64
[ 82696.994]     WinASegment: 0xa000
[ 82696.994]     WinBSegment: 0xa000
[ 82696.994]     WinFuncPtr: 0xc0005406
[ 82696.994]     BytesPerScanline: 1536
[ 82696.994]     XResolution: 512
[ 82696.994]     YResolution: 384
[ 82696.994]     XCharSize: 8
[ 82696.994]     YCharSize: 16
[ 82696.994]     NumberOfPlanes: 1
[ 82696.994]     BitsPerPixel: 24
[ 82696.994]     NumberOfBanks: 1
[ 82696.994]     MemoryModel: 6
[ 82696.994]     BankSize: 0
[ 82696.994]     NumberOfImages: 27
[ 82696.994]     RedMaskSize: 8
[ 82696.994]     RedFieldPosition: 16
[ 82696.994]     GreenMaskSize: 8
[ 82696.994]     GreenFieldPosition: 8
[ 82696.994]     BlueMaskSize: 8
[ 82696.994]     BlueFieldPosition: 0
[ 82696.994]     RsvdMaskSize: 0
[ 82696.994]     RsvdFieldPosition: 0
[ 82696.994]     DirectColorModeInfo: 0
[ 82696.994]     PhysBasePtr: 0xe8000000
[ 82696.998] *Mode: 1b6 (512x384)
[ 82696.998]     ModeAttributes: 0xbb
[ 82696.998]     WinAAttributes: 0x7
[ 82696.998]     WinBAttributes: 0x0
[ 82696.998]     WinGranularity: 64
[ 82696.998]     WinSize: 64
[ 82696.998]     WinASegment: 0xa000
[ 82696.998]     WinBSegment: 0xa000
[ 82696.998]     WinFuncPtr: 0xc0005406
[ 82696.998]     BytesPerScanline: 2048
[ 82696.998]     XResolution: 512
[ 82696.998]     YResolution: 384
[ 82696.998]     XCharSize: 8
[ 82696.998]     YCharSize: 16
[ 82696.998]     NumberOfPlanes: 1
[ 82696.998]     BitsPerPixel: 32
[ 82696.998]     NumberOfBanks: 1
[ 82696.998]     MemoryModel: 6
[ 82696.998]     BankSize: 0
[ 82696.998]     NumberOfImages: 20
[ 82696.998]     RedMaskSize: 8
[ 82696.998]     RedFieldPosition: 16
[ 82696.998]     GreenMaskSize: 8
[ 82696.998]     GreenFieldPosition: 8
[ 82696.998]     BlueMaskSize: 8
[ 82696.998]     BlueFieldPosition: 0
[ 82696.998]     RsvdMaskSize: 0
[ 82696.998]     RsvdFieldPosition: 0
[ 82696.998]     DirectColorModeInfo: 0
[ 82696.998]     PhysBasePtr: 0xe8000000
[ 82697.002] Mode: 1c2 (640x350)
[ 82697.002]     ModeAttributes: 0xbb
[ 82697.002]     WinAAttributes: 0x7
[ 82697.002]     WinBAttributes: 0x0
[ 82697.002]     WinGranularity: 64
[ 82697.002]     WinSize: 64
[ 82697.002]     WinASegment: 0xa000
[ 82697.002]     WinBSegment: 0xa000
[ 82697.002]     WinFuncPtr: 0xc0005406
[ 82697.002]     BytesPerScanline: 640
[ 82697.002]     XResolution: 640
[ 82697.002]     YResolution: 350
[ 82697.002]     XCharSize: 8
[ 82697.002]     YCharSize: 14
[ 82697.002]     NumberOfPlanes: 1
[ 82697.002]     BitsPerPixel: 8
[ 82697.002]     NumberOfBanks: 1
[ 82697.002]     MemoryModel: 4
[ 82697.002]     BankSize: 0
[ 82697.003]     NumberOfImages: 63
[ 82697.003]     RedMaskSize: 0
[ 82697.003]     RedFieldPosition: 0
[ 82697.003]     GreenMaskSize: 0
[ 82697.003]     GreenFieldPosition: 0
[ 82697.003]     BlueMaskSize: 0
[ 82697.003]     BlueFieldPosition: 0
[ 82697.003]     RsvdMaskSize: 0
[ 82697.003]     RsvdFieldPosition: 0
[ 82697.003]     DirectColorModeInfo: 0
[ 82697.003]     PhysBasePtr: 0xe8000000
[ 82697.006] Mode: 1c3 (640x350)
[ 82697.006]     ModeAttributes: 0xbb
[ 82697.006]     WinAAttributes: 0x7
[ 82697.006]     WinBAttributes: 0x0
[ 82697.006]     WinGranularity: 64
[ 82697.006]     WinSize: 64
[ 82697.006]     WinASegment: 0xa000
[ 82697.006]     WinBSegment: 0xa000
[ 82697.007]     WinFuncPtr: 0xc0005406
[ 82697.007]     BytesPerScanline: 1280
[ 82697.007]     XResolution: 640
[ 82697.007]     YResolution: 350
[ 82697.007]     XCharSize: 8
[ 82697.007]     YCharSize: 14
[ 82697.007]     NumberOfPlanes: 1
[ 82697.007]     BitsPerPixel: 15
[ 82697.007]     NumberOfBanks: 1
[ 82697.007]     MemoryModel: 6
[ 82697.007]     BankSize: 0
[ 82697.007]     NumberOfImages: 35
[ 82697.007]     RedMaskSize: 5
[ 82697.007]     RedFieldPosition: 10
[ 82697.007]     GreenMaskSize: 5
[ 82697.007]     GreenFieldPosition: 5
[ 82697.007]     BlueMaskSize: 5
[ 82697.007]     BlueFieldPosition: 0
[ 82697.007]     RsvdMaskSize: 0
[ 82697.007]     RsvdFieldPosition: 0
[ 82697.007]     DirectColorModeInfo: 0
[ 82697.007]     PhysBasePtr: 0xe8000000
[ 82697.011] Mode: 1c4 (640x350)
[ 82697.011]     ModeAttributes: 0xbb
[ 82697.011]     WinAAttributes: 0x7
[ 82697.011]     WinBAttributes: 0x0
[ 82697.011]     WinGranularity: 64
[ 82697.011]     WinSize: 64
[ 82697.011]     WinASegment: 0xa000
[ 82697.011]     WinBSegment: 0xa000
[ 82697.011]     WinFuncPtr: 0xc0005406
[ 82697.011]     BytesPerScanline: 1280
[ 82697.011]     XResolution: 640
[ 82697.011]     YResolution: 350
[ 82697.011]     XCharSize: 8
[ 82697.011]     YCharSize: 14
[ 82697.011]     NumberOfPlanes: 1
[ 82697.011]     BitsPerPixel: 16
[ 82697.011]     NumberOfBanks: 1
[ 82697.011]     MemoryModel: 6
[ 82697.011]     BankSize: 0
[ 82697.011]     NumberOfImages: 35
[ 82697.011]     RedMaskSize: 5
[ 82697.011]     RedFieldPosition: 11
[ 82697.011]     GreenMaskSize: 6
[ 82697.011]     GreenFieldPosition: 5
[ 82697.011]     BlueMaskSize: 5
[ 82697.011]     BlueFieldPosition: 0
[ 82697.011]     RsvdMaskSize: 0
[ 82697.011]     RsvdFieldPosition: 0
[ 82697.011]     DirectColorModeInfo: 0
[ 82697.011]     PhysBasePtr: 0xe8000000
[ 82697.015] Mode: 1c5 (640x350)
[ 82697.015]     ModeAttributes: 0xbb
[ 82697.015]     WinAAttributes: 0x7
[ 82697.015]     WinBAttributes: 0x0
[ 82697.015]     WinGranularity: 64
[ 82697.015]     WinSize: 64
[ 82697.015]     WinASegment: 0xa000
[ 82697.015]     WinBSegment: 0xa000
[ 82697.015]     WinFuncPtr: 0xc0005406
[ 82697.015]     BytesPerScanline: 1920
[ 82697.015]     XResolution: 640
[ 82697.015]     YResolution: 350
[ 82697.015]     XCharSize: 8
[ 82697.015]     YCharSize: 14
[ 82697.015]     NumberOfPlanes: 1
[ 82697.015]     BitsPerPixel: 24
[ 82697.015]     NumberOfBanks: 1
[ 82697.015]     MemoryModel: 6
[ 82697.015]     BankSize: 0
[ 82697.015]     NumberOfImages: 22
[ 82697.015]     RedMaskSize: 8
[ 82697.015]     RedFieldPosition: 16
[ 82697.015]     GreenMaskSize: 8
[ 82697.015]     GreenFieldPosition: 8
[ 82697.015]     BlueMaskSize: 8
[ 82697.015]     BlueFieldPosition: 0
[ 82697.015]     RsvdMaskSize: 0
[ 82697.016]     RsvdFieldPosition: 0
[ 82697.016]     DirectColorModeInfo: 0
[ 82697.016]     PhysBasePtr: 0xe8000000
[ 82697.019] *Mode: 1c6 (640x350)
[ 82697.019]     ModeAttributes: 0xbb
[ 82697.019]     WinAAttributes: 0x7
[ 82697.019]     WinBAttributes: 0x0
[ 82697.019]     WinGranularity: 64
[ 82697.019]     WinSize: 64
[ 82697.019]     WinASegment: 0xa000
[ 82697.019]     WinBSegment: 0xa000
[ 82697.019]     WinFuncPtr: 0xc0005406
[ 82697.019]     BytesPerScanline: 2560
[ 82697.019]     XResolution: 640
[ 82697.019]     YResolution: 350
[ 82697.019]     XCharSize: 8
[ 82697.019]     YCharSize: 14
[ 82697.019]     NumberOfPlanes: 1
[ 82697.020]     BitsPerPixel: 32
[ 82697.020]     NumberOfBanks: 1
[ 82697.020]     MemoryModel: 6
[ 82697.020]     BankSize: 0
[ 82697.020]     NumberOfImages: 17
[ 82697.020]     RedMaskSize: 8
[ 82697.020]     RedFieldPosition: 16
[ 82697.020]     GreenMaskSize: 8
[ 82697.020]     GreenFieldPosition: 8
[ 82697.020]     BlueMaskSize: 8
[ 82697.020]     BlueFieldPosition: 0
[ 82697.020]     RsvdMaskSize: 0
[ 82697.020]     RsvdFieldPosition: 0
[ 82697.020]     DirectColorModeInfo: 0
[ 82697.020]     PhysBasePtr: 0xe8000000
[ 82697.023] Mode: 100 (640x400)
[ 82697.024]     ModeAttributes: 0xbb
[ 82697.024]     WinAAttributes: 0x7
[ 82697.024]     WinBAttributes: 0x0
[ 82697.024]     WinGranularity: 64
[ 82697.024]     WinSize: 64
[ 82697.024]     WinASegment: 0xa000
[ 82697.024]     WinBSegment: 0xa000
[ 82697.024]     WinFuncPtr: 0xc0005406
[ 82697.024]     BytesPerScanline: 640
[ 82697.024]     XResolution: 640
[ 82697.024]     YResolution: 400
[ 82697.024]     XCharSize: 8
[ 82697.024]     YCharSize: 16
[ 82697.024]     NumberOfPlanes: 1
[ 82697.024]     BitsPerPixel: 8
[ 82697.024]     NumberOfBanks: 1
[ 82697.024]     MemoryModel: 4
[ 82697.024]     BankSize: 0
[ 82697.024]     NumberOfImages: 63
[ 82697.024]     RedMaskSize: 0
[ 82697.024]     RedFieldPosition: 0
[ 82697.024]     GreenMaskSize: 0
[ 82697.024]     GreenFieldPosition: 0
[ 82697.024]     BlueMaskSize: 0
[ 82697.024]     BlueFieldPosition: 0
[ 82697.024]     RsvdMaskSize: 0
[ 82697.024]     RsvdFieldPosition: 0
[ 82697.024]     DirectColorModeInfo: 0
[ 82697.024]     PhysBasePtr: 0xe8000000
[ 82697.029] Mode: 183 (640x400)
[ 82697.029]     ModeAttributes: 0xbb
[ 82697.029]     WinAAttributes: 0x7
[ 82697.029]     WinBAttributes: 0x0
[ 82697.029]     WinGranularity: 64
[ 82697.029]     WinSize: 64
[ 82697.029]     WinASegment: 0xa000
[ 82697.029]     WinBSegment: 0xa000
[ 82697.029]     WinFuncPtr: 0xc0005406
[ 82697.029]     BytesPerScanline: 1280
[ 82697.029]     XResolution: 640
[ 82697.029]     YResolution: 400
[ 82697.029]     XCharSize: 8
[ 82697.029]     YCharSize: 16
[ 82697.029]     NumberOfPlanes: 1
[ 82697.029]     BitsPerPixel: 15
[ 82697.029]     NumberOfBanks: 1
[ 82697.029]     MemoryModel: 6
[ 82697.029]     BankSize: 0
[ 82697.029]     NumberOfImages: 31
[ 82697.029]     RedMaskSize: 5
[ 82697.029]     RedFieldPosition: 10
[ 82697.029]     GreenMaskSize: 5
[ 82697.029]     GreenFieldPosition: 5
[ 82697.029]     BlueMaskSize: 5
[ 82697.029]     BlueFieldPosition: 0
[ 82697.029]     RsvdMaskSize: 0
[ 82697.029]     RsvdFieldPosition: 0
[ 82697.029]     DirectColorModeInfo: 0
[ 82697.029]     PhysBasePtr: 0xe8000000
[ 82697.033] Mode: 184 (640x400)
[ 82697.033]     ModeAttributes: 0xbb
[ 82697.033]     WinAAttributes: 0x7
[ 82697.033]     WinBAttributes: 0x0
[ 82697.033]     WinGranularity: 64
[ 82697.033]     WinSize: 64
[ 82697.033]     WinASegment: 0xa000
[ 82697.033]     WinBSegment: 0xa000
[ 82697.033]     WinFuncPtr: 0xc0005406
[ 82697.033]     BytesPerScanline: 1280
[ 82697.033]     XResolution: 640
[ 82697.033]     YResolution: 400
[ 82697.033]     XCharSize: 8
[ 82697.033]     YCharSize: 16
[ 82697.033]     NumberOfPlanes: 1
[ 82697.033]     BitsPerPixel: 16
[ 82697.033]     NumberOfBanks: 1
[ 82697.033]     MemoryModel: 6
[ 82697.033]     BankSize: 0
[ 82697.033]     NumberOfImages: 31
[ 82697.033]     RedMaskSize: 5
[ 82697.033]     RedFieldPosition: 11
[ 82697.033]     GreenMaskSize: 6
[ 82697.033]     GreenFieldPosition: 5
[ 82697.033]     BlueMaskSize: 5
[ 82697.034]     BlueFieldPosition: 0
[ 82697.034]     RsvdMaskSize: 0
[ 82697.034]     RsvdFieldPosition: 0
[ 82697.034]     DirectColorModeInfo: 0
[ 82697.034]     PhysBasePtr: 0xe8000000
[ 82697.038] Mode: 185 (640x400)
[ 82697.038]     ModeAttributes: 0xbb
[ 82697.038]     WinAAttributes: 0x7
[ 82697.038]     WinBAttributes: 0x0
[ 82697.038]     WinGranularity: 64
[ 82697.038]     WinSize: 64
[ 82697.038]     WinASegment: 0xa000
[ 82697.038]     WinBSegment: 0xa000
[ 82697.038]     WinFuncPtr: 0xc0005406
[ 82697.038]     BytesPerScanline: 1920
[ 82697.038]     XResolution: 640
[ 82697.038]     YResolution: 400
[ 82697.038]     XCharSize: 8
[ 82697.038]     YCharSize: 16
[ 82697.038]     NumberOfPlanes: 1
[ 82697.038]     BitsPerPixel: 24
[ 82697.038]     NumberOfBanks: 1
[ 82697.038]     MemoryModel: 6
[ 82697.038]     BankSize: 0
[ 82697.038]     NumberOfImages: 20
[ 82697.038]     RedMaskSize: 8
[ 82697.038]     RedFieldPosition: 16
[ 82697.038]     GreenMaskSize: 8
[ 82697.038]     GreenFieldPosition: 8
[ 82697.038]     BlueMaskSize: 8
[ 82697.038]     BlueFieldPosition: 0
[ 82697.038]     RsvdMaskSize: 0
[ 82697.038]     RsvdFieldPosition: 0
[ 82697.038]     DirectColorModeInfo: 0
[ 82697.038]     PhysBasePtr: 0xe8000000
[ 82697.042] *Mode: 186 (640x400)
[ 82697.042]     ModeAttributes: 0xbb
[ 82697.042]     WinAAttributes: 0x7
[ 82697.042]     WinBAttributes: 0x0
[ 82697.042]     WinGranularity: 64
[ 82697.042]     WinSize: 64
[ 82697.042]     WinASegment: 0xa000
[ 82697.042]     WinBSegment: 0xa000
[ 82697.042]     WinFuncPtr: 0xc0005406
[ 82697.042]     BytesPerScanline: 2560
[ 82697.042]     XResolution: 640
[ 82697.042]     YResolution: 400
[ 82697.042]     XCharSize: 8
[ 82697.042]     YCharSize: 16
[ 82697.042]     NumberOfPlanes: 1
[ 82697.042]     BitsPerPixel: 32
[ 82697.042]     NumberOfBanks: 1
[ 82697.042]     MemoryModel: 6
[ 82697.042]     BankSize: 0
[ 82697.042]     NumberOfImages: 15
[ 82697.042]     RedMaskSize: 8
[ 82697.043]     RedFieldPosition: 16
[ 82697.043]     GreenMaskSize: 8
[ 82697.043]     GreenFieldPosition: 8
[ 82697.043]     BlueMaskSize: 8
[ 82697.043]     BlueFieldPosition: 0
[ 82697.043]     RsvdMaskSize: 0
[ 82697.043]     RsvdFieldPosition: 0
[ 82697.043]     DirectColorModeInfo: 0
[ 82697.043]     PhysBasePtr: 0xe8000000
[ 82697.050] Mode: 101 (640x480)
[ 82697.050]     ModeAttributes: 0xbb
[ 82697.050]     WinAAttributes: 0x7
[ 82697.050]     WinBAttributes: 0x0
[ 82697.050]     WinGranularity: 64
[ 82697.050]     WinSize: 64
[ 82697.050]     WinASegment: 0xa000
[ 82697.050]     WinBSegment: 0xa000
[ 82697.050]     WinFuncPtr: 0xc0005406
[ 82697.050]     BytesPerScanline: 640
[ 82697.050]     XResolution: 640
[ 82697.050]     YResolution: 480
[ 82697.050]     XCharSize: 8
[ 82697.050]     YCharSize: 16
[ 82697.050]     NumberOfPlanes: 1
[ 82697.050]     BitsPerPixel: 8
[ 82697.050]     NumberOfBanks: 1
[ 82697.050]     MemoryModel: 4
[ 82697.050]     BankSize: 0
[ 82697.051]     NumberOfImages: 50
[ 82697.051]     RedMaskSize: 0
[ 82697.051]     RedFieldPosition: 0
[ 82697.051]     GreenMaskSize: 0
[ 82697.051]     GreenFieldPosition: 0
[ 82697.051]     BlueMaskSize: 0
[ 82697.051]     BlueFieldPosition: 0
[ 82697.051]     RsvdMaskSize: 0
[ 82697.051]     RsvdFieldPosition: 0
[ 82697.051]     DirectColorModeInfo: 0
[ 82697.051]     PhysBasePtr: 0xe8000000
[ 82697.058] Mode: 110 (640x480)
[ 82697.058]     ModeAttributes: 0xbb
[ 82697.058]     WinAAttributes: 0x7
[ 82697.058]     WinBAttributes: 0x0
[ 82697.058]     WinGranularity: 64
[ 82697.058]     WinSize: 64
[ 82697.058]     WinASegment: 0xa000
[ 82697.058]     WinBSegment: 0xa000
[ 82697.058]     WinFuncPtr: 0xc0005406
[ 82697.058]     BytesPerScanline: 1280
[ 82697.058]     XResolution: 640
[ 82697.058]     YResolution: 480
[ 82697.058]     XCharSize: 8
[ 82697.058]     YCharSize: 16
[ 82697.058]     NumberOfPlanes: 1
[ 82697.059]     BitsPerPixel: 15
[ 82697.059]     NumberOfBanks: 1
[ 82697.059]     MemoryModel: 6
[ 82697.059]     BankSize: 0
[ 82697.059]     NumberOfImages: 24
[ 82697.059]     RedMaskSize: 5
[ 82697.059]     RedFieldPosition: 10
[ 82697.059]     GreenMaskSize: 5
[ 82697.059]     GreenFieldPosition: 5
[ 82697.059]     BlueMaskSize: 5
[ 82697.059]     BlueFieldPosition: 0
[ 82697.059]     RsvdMaskSize: 0
[ 82697.059]     RsvdFieldPosition: 0
[ 82697.059]     DirectColorModeInfo: 0
[ 82697.059]     PhysBasePtr: 0xe8000000
[ 82697.066] Mode: 111 (640x480)
[ 82697.067]     ModeAttributes: 0xbb
[ 82697.067]     WinAAttributes: 0x7
[ 82697.067]     WinBAttributes: 0x0
[ 82697.067]     WinGranularity: 64
[ 82697.067]     WinSize: 64
[ 82697.067]     WinASegment: 0xa000
[ 82697.067]     WinBSegment: 0xa000
[ 82697.067]     WinFuncPtr: 0xc0005406
[ 82697.067]     BytesPerScanline: 1280
[ 82697.067]     XResolution: 640
[ 82697.067]     YResolution: 480
[ 82697.067]     XCharSize: 8
[ 82697.067]     YCharSize: 16
[ 82697.067]     NumberOfPlanes: 1
[ 82697.067]     BitsPerPixel: 16
[ 82697.067]     NumberOfBanks: 1
[ 82697.067]     MemoryModel: 6
[ 82697.067]     BankSize: 0
[ 82697.067]     NumberOfImages: 24
[ 82697.067]     RedMaskSize: 5
[ 82697.067]     RedFieldPosition: 11
[ 82697.067]     GreenMaskSize: 6
[ 82697.067]     GreenFieldPosition: 5
[ 82697.067]     BlueMaskSize: 5
[ 82697.067]     BlueFieldPosition: 0
[ 82697.067]     RsvdMaskSize: 0
[ 82697.067]     RsvdFieldPosition: 0
[ 82697.067]     DirectColorModeInfo: 0
[ 82697.067]     PhysBasePtr: 0xe8000000
[ 82697.075] Mode: 112 (640x480)
[ 82697.075]     ModeAttributes: 0xbb
[ 82697.075]     WinAAttributes: 0x7
[ 82697.075]     WinBAttributes: 0x0
[ 82697.075]     WinGranularity: 64
[ 82697.075]     WinSize: 64
[ 82697.075]     WinASegment: 0xa000
[ 82697.075]     WinBSegment: 0xa000
[ 82697.075]     WinFuncPtr: 0xc0005406
[ 82697.075]     BytesPerScanline: 1920
[ 82697.075]     XResolution: 640
[ 82697.075]     YResolution: 480
[ 82697.075]     XCharSize: 8
[ 82697.075]     YCharSize: 16
[ 82697.075]     NumberOfPlanes: 1
[ 82697.075]     BitsPerPixel: 24
[ 82697.075]     NumberOfBanks: 1
[ 82697.075]     MemoryModel: 6
[ 82697.075]     BankSize: 0
[ 82697.075]     NumberOfImages: 16
[ 82697.075]     RedMaskSize: 8
[ 82697.075]     RedFieldPosition: 16
[ 82697.075]     GreenMaskSize: 8
[ 82697.075]     GreenFieldPosition: 8
[ 82697.075]     BlueMaskSize: 8
[ 82697.075]     BlueFieldPosition: 0
[ 82697.075]     RsvdMaskSize: 0
[ 82697.075]     RsvdFieldPosition: 0
[ 82697.075]     DirectColorModeInfo: 0
[ 82697.075]     PhysBasePtr: 0xe8000000
[ 82697.083] *Mode: 121 (640x480)
[ 82697.083]     ModeAttributes: 0xbb
[ 82697.083]     WinAAttributes: 0x7
[ 82697.083]     WinBAttributes: 0x0
[ 82697.083]     WinGranularity: 64
[ 82697.083]     WinSize: 64
[ 82697.083]     WinASegment: 0xa000
[ 82697.083]     WinBSegment: 0xa000
[ 82697.083]     WinFuncPtr: 0xc0005406
[ 82697.083]     BytesPerScanline: 2560
[ 82697.083]     XResolution: 640
[ 82697.083]     YResolution: 480
[ 82697.083]     XCharSize: 8
[ 82697.083]     YCharSize: 16
[ 82697.083]     NumberOfPlanes: 1
[ 82697.083]     BitsPerPixel: 32
[ 82697.083]     NumberOfBanks: 1
[ 82697.083]     MemoryModel: 6
[ 82697.083]     BankSize: 0
[ 82697.083]     NumberOfImages: 12
[ 82697.083]     RedMaskSize: 8
[ 82697.083]     RedFieldPosition: 16
[ 82697.083]     GreenMaskSize: 8
[ 82697.083]     GreenFieldPosition: 8
[ 82697.083]     BlueMaskSize: 8
[ 82697.084]     BlueFieldPosition: 0
[ 82697.084]     RsvdMaskSize: 0
[ 82697.084]     RsvdFieldPosition: 0
[ 82697.084]     DirectColorModeInfo: 0
[ 82697.084]     PhysBasePtr: 0xe8000000
[ 82697.091] Mode: 103 (800x600)
[ 82697.091]     ModeAttributes: 0xbb
[ 82697.091]     WinAAttributes: 0x7
[ 82697.091]     WinBAttributes: 0x0
[ 82697.092]     WinGranularity: 64
[ 82697.092]     WinSize: 64
[ 82697.092]     WinASegment: 0xa000
[ 82697.092]     WinBSegment: 0xa000
[ 82697.092]     WinFuncPtr: 0xc0005406
[ 82697.092]     BytesPerScanline: 800
[ 82697.092]     XResolution: 800
[ 82697.092]     YResolution: 600
[ 82697.092]     XCharSize: 8
[ 82697.092]     YCharSize: 14
[ 82697.092]     NumberOfPlanes: 1
[ 82697.092]     BitsPerPixel: 8
[ 82697.092]     NumberOfBanks: 1
[ 82697.092]     MemoryModel: 4
[ 82697.092]     BankSize: 0
[ 82697.092]     NumberOfImages: 31
[ 82697.092]     RedMaskSize: 0
[ 82697.092]     RedFieldPosition: 0
[ 82697.092]     GreenMaskSize: 0
[ 82697.092]     GreenFieldPosition: 0
[ 82697.092]     BlueMaskSize: 0
[ 82697.092]     BlueFieldPosition: 0
[ 82697.092]     RsvdMaskSize: 0
[ 82697.092]     RsvdFieldPosition: 0
[ 82697.092]     DirectColorModeInfo: 0
[ 82697.092]     PhysBasePtr: 0xe8000000
[ 82697.100] Mode: 113 (800x600)
[ 82697.100]     ModeAttributes: 0xbb
[ 82697.100]     WinAAttributes: 0x7
[ 82697.100]     WinBAttributes: 0x0
[ 82697.100]     WinGranularity: 64
[ 82697.100]     WinSize: 64
[ 82697.100]     WinASegment: 0xa000
[ 82697.100]     WinBSegment: 0xa000
[ 82697.100]     WinFuncPtr: 0xc0005406
[ 82697.100]     BytesPerScanline: 1600
[ 82697.100]     XResolution: 800
[ 82697.100]     YResolution: 600
[ 82697.100]     XCharSize: 8
[ 82697.100]     YCharSize: 14
[ 82697.100]     NumberOfPlanes: 1
[ 82697.100]     BitsPerPixel: 15
[ 82697.100]     NumberOfBanks: 1
[ 82697.100]     MemoryModel: 6
[ 82697.100]     BankSize: 0
[ 82697.100]     NumberOfImages: 16
[ 82697.100]     RedMaskSize: 5
[ 82697.100]     RedFieldPosition: 10
[ 82697.100]     GreenMaskSize: 5
[ 82697.100]     GreenFieldPosition: 5
[ 82697.100]     BlueMaskSize: 5
[ 82697.100]     BlueFieldPosition: 0
[ 82697.101]     RsvdMaskSize: 0
[ 82697.101]     RsvdFieldPosition: 0
[ 82697.101]     DirectColorModeInfo: 0
[ 82697.101]     PhysBasePtr: 0xe8000000
[ 82697.108] Mode: 114 (800x600)
[ 82697.108]     ModeAttributes: 0xbb
[ 82697.108]     WinAAttributes: 0x7
[ 82697.108]     WinBAttributes: 0x0
[ 82697.108]     WinGranularity: 64
[ 82697.108]     WinSize: 64
[ 82697.108]     WinASegment: 0xa000
[ 82697.108]     WinBSegment: 0xa000
[ 82697.108]     WinFuncPtr: 0xc0005406
[ 82697.108]     BytesPerScanline: 1600
[ 82697.108]     XResolution: 800
[ 82697.108]     YResolution: 600
[ 82697.108]     XCharSize: 8
[ 82697.109]     YCharSize: 14
[ 82697.109]     NumberOfPlanes: 1
[ 82697.109]     BitsPerPixel: 16
[ 82697.109]     NumberOfBanks: 1
[ 82697.109]     MemoryModel: 6
[ 82697.109]     BankSize: 0
[ 82697.109]     NumberOfImages: 16
[ 82697.109]     RedMaskSize: 5
[ 82697.109]     RedFieldPosition: 11
[ 82697.109]     GreenMaskSize: 6
[ 82697.109]     GreenFieldPosition: 5
[ 82697.109]     BlueMaskSize: 5
[ 82697.109]     BlueFieldPosition: 0
[ 82697.109]     RsvdMaskSize: 0
[ 82697.109]     RsvdFieldPosition: 0
[ 82697.109]     DirectColorModeInfo: 0
[ 82697.109]     PhysBasePtr: 0xe8000000
[ 82697.117] Mode: 115 (800x600)
[ 82697.117]     ModeAttributes: 0xbb
[ 82697.117]     WinAAttributes: 0x7
[ 82697.117]     WinBAttributes: 0x0
[ 82697.117]     WinGranularity: 64
[ 82697.117]     WinSize: 64
[ 82697.117]     WinASegment: 0xa000
[ 82697.117]     WinBSegment: 0xa000
[ 82697.117]     WinFuncPtr: 0xc0005406
[ 82697.117]     BytesPerScanline: 2400
[ 82697.117]     XResolution: 800
[ 82697.117]     YResolution: 600
[ 82697.117]     XCharSize: 8
[ 82697.117]     YCharSize: 14
[ 82697.117]     NumberOfPlanes: 1
[ 82697.117]     BitsPerPixel: 24
[ 82697.117]     NumberOfBanks: 1
[ 82697.117]     MemoryModel: 6
[ 82697.117]     BankSize: 0
[ 82697.117]     NumberOfImages: 10
[ 82697.117]     RedMaskSize: 8
[ 82697.117]     RedFieldPosition: 16
[ 82697.117]     GreenMaskSize: 8
[ 82697.117]     GreenFieldPosition: 8
[ 82697.117]     BlueMaskSize: 8
[ 82697.117]     BlueFieldPosition: 0
[ 82697.117]     RsvdMaskSize: 0
[ 82697.117]     RsvdFieldPosition: 0
[ 82697.117]     DirectColorModeInfo: 0
[ 82697.117]     PhysBasePtr: 0xe8000000
[ 82697.125] *Mode: 122 (800x600)
[ 82697.125]     ModeAttributes: 0xbb
[ 82697.125]     WinAAttributes: 0x7
[ 82697.125]     WinBAttributes: 0x0
[ 82697.125]     WinGranularity: 64
[ 82697.125]     WinSize: 64
[ 82697.125]     WinASegment: 0xa000
[ 82697.125]     WinBSegment: 0xa000
[ 82697.125]     WinFuncPtr: 0xc0005406
[ 82697.125]     BytesPerScanline: 3200
[ 82697.125]     XResolution: 800
[ 82697.125]     YResolution: 600
[ 82697.126]     XCharSize: 8
[ 82697.126]     YCharSize: 14
[ 82697.126]     NumberOfPlanes: 1
[ 82697.126]     BitsPerPixel: 32
[ 82697.126]     NumberOfBanks: 1
[ 82697.126]     MemoryModel: 6
[ 82697.126]     BankSize: 0
[ 82697.126]     NumberOfImages: 7
[ 82697.126]     RedMaskSize: 8
[ 82697.126]     RedFieldPosition: 16
[ 82697.126]     GreenMaskSize: 8
[ 82697.126]     GreenFieldPosition: 8
[ 82697.126]     BlueMaskSize: 8
[ 82697.126]     BlueFieldPosition: 0
[ 82697.126]     RsvdMaskSize: 0
[ 82697.126]     RsvdFieldPosition: 0
[ 82697.126]     DirectColorModeInfo: 0
[ 82697.126]     PhysBasePtr: 0xe8000000
[ 82697.134] Mode: 105 (1024x768)
[ 82697.134]     ModeAttributes: 0xbb
[ 82697.134]     WinAAttributes: 0x7
[ 82697.134]     WinBAttributes: 0x0
[ 82697.134]     WinGranularity: 64
[ 82697.134]     WinSize: 64
[ 82697.134]     WinASegment: 0xa000
[ 82697.134]     WinBSegment: 0xa000
[ 82697.134]     WinFuncPtr: 0xc0005406
[ 82697.134]     BytesPerScanline: 1024
[ 82697.134]     XResolution: 1024
[ 82697.134]     YResolution: 768
[ 82697.134]     XCharSize: 8
[ 82697.134]     YCharSize: 16
[ 82697.134]     NumberOfPlanes: 1
[ 82697.134]     BitsPerPixel: 8
[ 82697.134]     NumberOfBanks: 1
[ 82697.134]     MemoryModel: 4
[ 82697.134]     BankSize: 0
[ 82697.134]     NumberOfImages: 20
[ 82697.134]     RedMaskSize: 0
[ 82697.134]     RedFieldPosition: 0
[ 82697.134]     GreenMaskSize: 0
[ 82697.134]     GreenFieldPosition: 0
[ 82697.134]     BlueMaskSize: 0
[ 82697.134]     BlueFieldPosition: 0
[ 82697.134]     RsvdMaskSize: 0
[ 82697.134]     RsvdFieldPosition: 0
[ 82697.135]     DirectColorModeInfo: 0
[ 82697.135]     PhysBasePtr: 0xe8000000
[ 82697.143] Mode: 116 (1024x768)
[ 82697.143]     ModeAttributes: 0xbb
[ 82697.143]     WinAAttributes: 0x7
[ 82697.143]     WinBAttributes: 0x0
[ 82697.143]     WinGranularity: 64
[ 82697.143]     WinSize: 64
[ 82697.143]     WinASegment: 0xa000
[ 82697.143]     WinBSegment: 0xa000
[ 82697.143]     WinFuncPtr: 0xc0005406
[ 82697.143]     BytesPerScanline: 2048
[ 82697.143]     XResolution: 1024
[ 82697.143]     YResolution: 768
[ 82697.143]     XCharSize: 8
[ 82697.143]     YCharSize: 16
[ 82697.143]     NumberOfPlanes: 1
[ 82697.143]     BitsPerPixel: 15
[ 82697.143]     NumberOfBanks: 1
[ 82697.143]     MemoryModel: 6
[ 82697.143]     BankSize: 0
[ 82697.143]     NumberOfImages: 9
[ 82697.143]     RedMaskSize: 5
[ 82697.143]     RedFieldPosition: 10
[ 82697.143]     GreenMaskSize: 5
[ 82697.143]     GreenFieldPosition: 5
[ 82697.143]     BlueMaskSize: 5
[ 82697.143]     BlueFieldPosition: 0
[ 82697.143]     RsvdMaskSize: 0
[ 82697.143]     RsvdFieldPosition: 0
[ 82697.143]     DirectColorModeInfo: 0
[ 82697.143]     PhysBasePtr: 0xe8000000
[ 82697.151] Mode: 117 (1024x768)
[ 82697.151]     ModeAttributes: 0xbb
[ 82697.151]     WinAAttributes: 0x7
[ 82697.151]     WinBAttributes: 0x0
[ 82697.151]     WinGranularity: 64
[ 82697.152]     WinSize: 64
[ 82697.152]     WinASegment: 0xa000
[ 82697.152]     WinBSegment: 0xa000
[ 82697.152]     WinFuncPtr: 0xc0005406
[ 82697.152]     BytesPerScanline: 2048
[ 82697.152]     XResolution: 1024
[ 82697.152]     YResolution: 768
[ 82697.152]     XCharSize: 8
[ 82697.152]     YCharSize: 16
[ 82697.152]     NumberOfPlanes: 1
[ 82697.152]     BitsPerPixel: 16
[ 82697.152]     NumberOfBanks: 1
[ 82697.152]     MemoryModel: 6
[ 82697.152]     BankSize: 0
[ 82697.152]     NumberOfImages: 9
[ 82697.152]     RedMaskSize: 5
[ 82697.152]     RedFieldPosition: 11
[ 82697.152]     GreenMaskSize: 6
[ 82697.152]     GreenFieldPosition: 5
[ 82697.152]     BlueMaskSize: 5
[ 82697.152]     BlueFieldPosition: 0
[ 82697.152]     RsvdMaskSize: 0
[ 82697.152]     RsvdFieldPosition: 0
[ 82697.152]     DirectColorModeInfo: 0
[ 82697.152]     PhysBasePtr: 0xe8000000
[ 82697.160] Mode: 118 (1024x768)
[ 82697.160]     ModeAttributes: 0xbb
[ 82697.160]     WinAAttributes: 0x7
[ 82697.160]     WinBAttributes: 0x0
[ 82697.160]     WinGranularity: 64
[ 82697.160]     WinSize: 64
[ 82697.160]     WinASegment: 0xa000
[ 82697.160]     WinBSegment: 0xa000
[ 82697.160]     WinFuncPtr: 0xc0005406
[ 82697.160]     BytesPerScanline: 3072
[ 82697.160]     XResolution: 1024
[ 82697.160]     YResolution: 768
[ 82697.160]     XCharSize: 8
[ 82697.161]     YCharSize: 16
[ 82697.161]     NumberOfPlanes: 1
[ 82697.161]     BitsPerPixel: 24
[ 82697.161]     NumberOfBanks: 1
[ 82697.161]     MemoryModel: 6
[ 82697.161]     BankSize: 0
[ 82697.161]     NumberOfImages: 6
[ 82697.161]     RedMaskSize: 8
[ 82697.161]     RedFieldPosition: 16
[ 82697.161]     GreenMaskSize: 8
[ 82697.161]     GreenFieldPosition: 8
[ 82697.161]     BlueMaskSize: 8
[ 82697.161]     BlueFieldPosition: 0
[ 82697.161]     RsvdMaskSize: 0
[ 82697.161]     RsvdFieldPosition: 0
[ 82697.161]     DirectColorModeInfo: 0
[ 82697.161]     PhysBasePtr: 0xe8000000
[ 82697.169] *Mode: 123 (1024x768)
[ 82697.169]     ModeAttributes: 0xbb
[ 82697.169]     WinAAttributes: 0x7
[ 82697.169]     WinBAttributes: 0x0
[ 82697.169]     WinGranularity: 64
[ 82697.169]     WinSize: 64
[ 82697.169]     WinASegment: 0xa000
[ 82697.169]     WinBSegment: 0xa000
[ 82697.169]     WinFuncPtr: 0xc0005406
[ 82697.169]     BytesPerScanline: 4096
[ 82697.169]     XResolution: 1024
[ 82697.169]     YResolution: 768
[ 82697.169]     XCharSize: 8
[ 82697.169]     YCharSize: 16
[ 82697.169]     NumberOfPlanes: 1
[ 82697.169]     BitsPerPixel: 32
[ 82697.169]     NumberOfBanks: 1
[ 82697.169]     MemoryModel: 6
[ 82697.169]     BankSize: 0
[ 82697.169]     NumberOfImages: 4
[ 82697.169]     RedMaskSize: 8
[ 82697.169]     RedFieldPosition: 16
[ 82697.169]     GreenMaskSize: 8
[ 82697.169]     GreenFieldPosition: 8
[ 82697.169]     BlueMaskSize: 8
[ 82697.169]     BlueFieldPosition: 0
[ 82697.169]     RsvdMaskSize: 0
[ 82697.170]     RsvdFieldPosition: 0
[ 82697.170]     DirectColorModeInfo: 0
[ 82697.170]     PhysBasePtr: 0xe8000000
[ 82697.178] Mode: 107 (1280x1024)
[ 82697.178]     ModeAttributes: 0xbb
[ 82697.178]     WinAAttributes: 0x7
[ 82697.178]     WinBAttributes: 0x0
[ 82697.178]     WinGranularity: 64
[ 82697.178]     WinSize: 64
[ 82697.178]     WinASegment: 0xa000
[ 82697.178]     WinBSegment: 0xa000
[ 82697.178]     WinFuncPtr: 0xc0005406
[ 82697.178]     BytesPerScanline: 1280
[ 82697.178]     XResolution: 1280
[ 82697.178]     YResolution: 1024
[ 82697.178]     XCharSize: 8
[ 82697.179]     YCharSize: 16
[ 82697.179]     NumberOfPlanes: 1
[ 82697.179]     BitsPerPixel: 8
[ 82697.179]     NumberOfBanks: 1
[ 82697.179]     MemoryModel: 4
[ 82697.179]     BankSize: 0
[ 82697.179]     NumberOfImages: 11
[ 82697.179]     RedMaskSize: 0
[ 82697.179]     RedFieldPosition: 0
[ 82697.179]     GreenMaskSize: 0
[ 82697.179]     GreenFieldPosition: 0
[ 82697.179]     BlueMaskSize: 0
[ 82697.179]     BlueFieldPosition: 0
[ 82697.179]     RsvdMaskSize: 0
[ 82697.179]     RsvdFieldPosition: 0
[ 82697.179]     DirectColorModeInfo: 0
[ 82697.179]     PhysBasePtr: 0xe8000000
[ 82697.188] Mode: 119 (1280x1024)
[ 82697.188]     ModeAttributes: 0xbb
[ 82697.188]     WinAAttributes: 0x7
[ 82697.188]     WinBAttributes: 0x0
[ 82697.188]     WinGranularity: 64
[ 82697.188]     WinSize: 64
[ 82697.188]     WinASegment: 0xa000
[ 82697.188]     WinBSegment: 0xa000
[ 82697.188]     WinFuncPtr: 0xc0005406
[ 82697.188]     BytesPerScanline: 2560
[ 82697.188]     XResolution: 1280
[ 82697.188]     YResolution: 1024
[ 82697.188]     XCharSize: 8
[ 82697.188]     YCharSize: 16
[ 82697.188]     NumberOfPlanes: 1
[ 82697.188]     BitsPerPixel: 15
[ 82697.188]     NumberOfBanks: 1
[ 82697.188]     MemoryModel: 6
[ 82697.188]     BankSize: 0
[ 82697.188]     NumberOfImages: 5
[ 82697.188]     RedMaskSize: 5
[ 82697.188]     RedFieldPosition: 10
[ 82697.188]     GreenMaskSize: 5
[ 82697.188]     GreenFieldPosition: 5
[ 82697.188]     BlueMaskSize: 5
[ 82697.188]     BlueFieldPosition: 0
[ 82697.188]     RsvdMaskSize: 0
[ 82697.188]     RsvdFieldPosition: 0
[ 82697.188]     DirectColorModeInfo: 0
[ 82697.188]     PhysBasePtr: 0xe8000000
[ 82697.197] Mode: 11a (1280x1024)
[ 82697.197]     ModeAttributes: 0xbb
[ 82697.197]     WinAAttributes: 0x7
[ 82697.197]     WinBAttributes: 0x0
[ 82697.197]     WinGranularity: 64
[ 82697.197]     WinSize: 64
[ 82697.197]     WinASegment: 0xa000
[ 82697.197]     WinBSegment: 0xa000
[ 82697.197]     WinFuncPtr: 0xc0005406
[ 82697.197]     BytesPerScanline: 2560
[ 82697.197]     XResolution: 1280
[ 82697.197]     YResolution: 1024
[ 82697.197]     XCharSize: 8
[ 82697.197]     YCharSize: 16
[ 82697.197]     NumberOfPlanes: 1
[ 82697.197]     BitsPerPixel: 16
[ 82697.197]     NumberOfBanks: 1
[ 82697.197]     MemoryModel: 6
[ 82697.197]     BankSize: 0
[ 82697.197]     NumberOfImages: 5
[ 82697.197]     RedMaskSize: 5
[ 82697.197]     RedFieldPosition: 11
[ 82697.197]     GreenMaskSize: 6
[ 82697.197]     GreenFieldPosition: 5
[ 82697.197]     BlueMaskSize: 5
[ 82697.197]     BlueFieldPosition: 0
[ 82697.197]     RsvdMaskSize: 0
[ 82697.198]     RsvdFieldPosition: 0
[ 82697.198]     DirectColorModeInfo: 0
[ 82697.198]     PhysBasePtr: 0xe8000000
[ 82697.206] Mode: 11b (1280x1024)
[ 82697.206]     ModeAttributes: 0xbb
[ 82697.206]     WinAAttributes: 0x7
[ 82697.206]     WinBAttributes: 0x0
[ 82697.206]     WinGranularity: 64
[ 82697.206]     WinSize: 64
[ 82697.206]     WinASegment: 0xa000
[ 82697.206]     WinBSegment: 0xa000
[ 82697.206]     WinFuncPtr: 0xc0005406
[ 82697.206]     BytesPerScanline: 3840
[ 82697.206]     XResolution: 1280
[ 82697.206]     YResolution: 1024
[ 82697.206]     XCharSize: 8
[ 82697.206]     YCharSize: 16
[ 82697.206]     NumberOfPlanes: 1
[ 82697.206]     BitsPerPixel: 24
[ 82697.206]     NumberOfBanks: 1
[ 82697.206]     MemoryModel: 6
[ 82697.206]     BankSize: 0
[ 82697.206]     NumberOfImages: 3
[ 82697.207]     RedMaskSize: 8
[ 82697.207]     RedFieldPosition: 16
[ 82697.207]     GreenMaskSize: 8
[ 82697.207]     GreenFieldPosition: 8
[ 82697.207]     BlueMaskSize: 8
[ 82697.207]     BlueFieldPosition: 0
[ 82697.207]     RsvdMaskSize: 0
[ 82697.207]     RsvdFieldPosition: 0
[ 82697.207]     DirectColorModeInfo: 0
[ 82697.207]     PhysBasePtr: 0xe8000000
[ 82697.215] *Mode: 124 (1280x1024)
[ 82697.215]     ModeAttributes: 0xbb
[ 82697.215]     WinAAttributes: 0x7
[ 82697.215]     WinBAttributes: 0x0
[ 82697.215]     WinGranularity: 64
[ 82697.215]     WinSize: 64
[ 82697.215]     WinASegment: 0xa000
[ 82697.215]     WinBSegment: 0xa000
[ 82697.215]     WinFuncPtr: 0xc0005406
[ 82697.215]     BytesPerScanline: 5120
[ 82697.215]     XResolution: 1280
[ 82697.215]     YResolution: 1024
[ 82697.215]     XCharSize: 8
[ 82697.215]     YCharSize: 16
[ 82697.215]     NumberOfPlanes: 1
[ 82697.215]     BitsPerPixel: 32
[ 82697.215]     NumberOfBanks: 1
[ 82697.215]     MemoryModel: 6
[ 82697.215]     BankSize: 0
[ 82697.215]     NumberOfImages: 2
[ 82697.216]     RedMaskSize: 8
[ 82697.216]     RedFieldPosition: 16
[ 82697.216]     GreenMaskSize: 8
[ 82697.216]     GreenFieldPosition: 8
[ 82697.216]     BlueMaskSize: 8
[ 82697.216]     BlueFieldPosition: 0
[ 82697.216]     RsvdMaskSize: 0
[ 82697.216]     RsvdFieldPosition: 0
[ 82697.216]     DirectColorModeInfo: 0
[ 82697.216]     PhysBasePtr: 0xe8000000
[ 82697.216] Mode: 109 (132x25)
[ 82697.216]     ModeAttributes: 0xf
[ 82697.216]     WinAAttributes: 0x6
[ 82697.216]     WinBAttributes: 0x0
[ 82697.216]     WinGranularity: 0
[ 82697.216]     WinSize: 0
[ 82697.216]     WinASegment: 0xb800
[ 82697.216]     WinBSegment: 0x0
[ 82697.216]     WinFuncPtr: 0x0
[ 82697.216]     BytesPerScanline: 264
[ 82697.216]     XResolution: 132
[ 82697.216]     YResolution: 25
[ 82697.216]     XCharSize: 8
[ 82697.216]     YCharSize: 16
[ 82697.216]     NumberOfPlanes: 1
[ 82697.216]     BitsPerPixel: 4
[ 82697.216]     NumberOfBanks: 1
[ 82697.217]     MemoryModel: 0
[ 82697.217]     BankSize: 0
[ 82697.217]     NumberOfImages: 0
[ 82697.217]     RedMaskSize: 0
[ 82697.217]     RedFieldPosition: 0
[ 82697.217]     GreenMaskSize: 0
[ 82697.217]     GreenFieldPosition: 0
[ 82697.217]     BlueMaskSize: 0
[ 82697.217]     BlueFieldPosition: 0
[ 82697.217]     RsvdMaskSize: 0
[ 82697.217]     RsvdFieldPosition: 0
[ 82697.217]     DirectColorModeInfo: 0
[ 82697.217]     PhysBasePtr: 0x0
[ 82697.217] Mode: 10a (132x43)
[ 82697.217]     ModeAttributes: 0xf
[ 82697.217]     WinAAttributes: 0x6
[ 82697.217]     WinBAttributes: 0x0
[ 82697.217]     WinGranularity: 0
[ 82697.217]     WinSize: 0
[ 82697.217]     WinASegment: 0xb800
[ 82697.217]     WinBSegment: 0x0
[ 82697.217]     WinFuncPtr: 0x0
[ 82697.217]     BytesPerScanline: 264
[ 82697.217]     XResolution: 132
[ 82697.217]     YResolution: 43
[ 82697.217]     XCharSize: 8
[ 82697.217]     YCharSize: 8
[ 82697.217]     NumberOfPlanes: 1
[ 82697.217]     BitsPerPixel: 4
[ 82697.218]     NumberOfBanks: 1
[ 82697.218]     MemoryModel: 0
[ 82697.218]     BankSize: 0
[ 82697.218]     NumberOfImages: 0
[ 82697.218]     RedMaskSize: 0
[ 82697.218]     RedFieldPosition: 0
[ 82697.218]     GreenMaskSize: 0
[ 82697.218]     GreenFieldPosition: 0
[ 82697.218]     BlueMaskSize: 0
[ 82697.218]     BlueFieldPosition: 0
[ 82697.218]     RsvdMaskSize: 0
[ 82697.218]     RsvdFieldPosition: 0
[ 82697.218]     DirectColorModeInfo: 0
[ 82697.218]     PhysBasePtr: 0x0
[ 82697.218] Mode: 130 (132x44)
[ 82697.218]     ModeAttributes: 0xf
[ 82697.218]     WinAAttributes: 0x6
[ 82697.218]     WinBAttributes: 0x0
[ 82697.218]     WinGranularity: 0
[ 82697.218]     WinSize: 0
[ 82697.218]     WinASegment: 0xb800
[ 82697.218]     WinBSegment: 0x0
[ 82697.218]     WinFuncPtr: 0x0
[ 82697.218]     BytesPerScanline: 264
[ 82697.218]     XResolution: 132
[ 82697.218]     YResolution: 44
[ 82697.218]     XCharSize: 8
[ 82697.218]     YCharSize: 8
[ 82697.218]     NumberOfPlanes: 1
[ 82697.218]     BitsPerPixel: 4
[ 82697.219]     NumberOfBanks: 1
[ 82697.219]     MemoryModel: 0
[ 82697.219]     BankSize: 0
[ 82697.219]     NumberOfImages: 0
[ 82697.219]     RedMaskSize: 0
[ 82697.219]     RedFieldPosition: 0
[ 82697.219]     GreenMaskSize: 0
[ 82697.219]     GreenFieldPosition: 0
[ 82697.219]     BlueMaskSize: 0
[ 82697.219]     BlueFieldPosition: 0
[ 82697.219]     RsvdMaskSize: 0
[ 82697.219]     RsvdFieldPosition: 0
[ 82697.219]     DirectColorModeInfo: 0
[ 82697.219]     PhysBasePtr: 0x0
[ 82697.219] 
[ 82697.219] (II) VESA(1): Total Memory: 256 64KB banks (16384kB)
[ 82697.219] (II) VESA(1): <default monitor>: Using hsync range of 30.00-80.00 kHz
[ 82697.219] (II) VESA(1): <default monitor>: Using vrefresh range of 56.00-75.00 Hz
[ 82697.219] (II) VESA(1): <default monitor>: Using maximum pixel clock of 145.00 MHz
[ 82697.219] (WW) VESA(1): Unable to estimate virtual size
[ 82697.220] (II) VESA(1): Not using built-in mode "640x400" (no mode of this name)
[ 82697.220] (II) VESA(1): Not using built-in mode "640x350" (no mode of this name)
[ 82697.220] (II) VESA(1): Not using built-in mode "512x384" (no mode of this name)
[ 82697.220] (II) VESA(1): Not using built-in mode "400x300" (no mode of this name)
[ 82697.220] (II) VESA(1): Not using built-in mode "320x240" (no mode of this name)
[ 82697.220] (II) VESA(1): Not using built-in mode "320x200" (no mode of this name)
[ 82697.220] (--) VESA(1): Virtual size is 1280x1024 (pitch 1280)
[ 82697.220] (**) VESA(1): *Built-in mode "1280x1024"
[ 82697.220] (**) VESA(1): *Built-in mode "1024x768"
[ 82697.220] (**) VESA(1): *Built-in mode "800x600"
[ 82697.220] (**) VESA(1): *Built-in mode "640x480"
[ 82697.220] (**) VESA(1): Display dimensions: (340, 270) mm
[ 82697.220] (**) VESA(1): DPI set to (95, 96)
[ 82697.220] (**) VESA(1): Using "Shadow Framebuffer"
[ 82697.220] (II) Loading sub module "shadow"
[ 82697.220] (II) LoadModule: "shadow"
[ 82697.221] (II) Loading /usr/lib/xorg/modules/libshadow.so
[ 82697.221] (II) Module shadow: vendor="X.Org Foundation"
[ 82697.221]     compiled for 1.11.3, module version = 1.1.0
[ 82697.221]     ABI class: X.Org ANSI C Emulation, version 0.4
[ 82697.221] (II) Loading sub module "fb"
[ 82697.221] (II) LoadModule: "fb"
[ 82697.222] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 82697.243] (II) Module fb: vendor="X.Org Foundation"
[ 82697.243]     compiled for 1.11.3, module version = 1.0.0
[ 82697.243]     ABI class: X.Org ANSI C Emulation, version 0.4
[ 82697.244] (II) UnloadModule: "radeon"
[ 82697.244] (II) Unloading radeon
[ 82697.244] (II) UnloadModule: "fbdev"
[ 82697.244] (II) Unloading fbdev
[ 82697.244] (II) UnloadModule: "fbdevhw"
[ 82697.244] (II) Unloading fbdevhw
[ 82697.244] (==) Depth 24 pixmap format is 32 bpp
[ 82697.244] (II) Loading sub module "int10"
[ 82697.244] (II) LoadModule: "int10"
[ 82697.245] (II) Loading /usr/lib/xorg/modules/libint10.so
[ 82697.245] (II) Module int10: vendor="X.Org Foundation"
[ 82697.245]     compiled for 1.11.3, module version = 1.0.0
[ 82697.245]     ABI class: X.Org Video Driver, version 11.0
[ 82697.245] (II) VESA(0): initializing int10
[ 82697.249] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[ 82697.250] (II) VESA(0): VESA BIOS detected
[ 82697.250] (II) VESA(0): VESA VBE Version 2.0
[ 82697.250] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[ 82697.250] (II) VESA(0): VESA VBE OEM: ATI RADEON 9200
[ 82697.250] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[ 82697.250] (II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
[ 82697.250] (II) VESA(0): VESA VBE OEM Product: V280
[ 82697.250] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[ 82697.255] (II) VESA(0): virtual address = 0xb55cb000,
    physical address = 0xe8000000, size = 16777216
[ 82697.264] (II) VESA(0): Setting up VESA Mode 0x124 (1280x1024)
[ 82697.265] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[ 82697.802] (==) VESA(0): Default visual is TrueColor
[ 82697.802] (==) VESA(0): Backing store disabled
[ 82697.802] (==) VESA(0): DPMS enabled
[ 82697.802] (==) RandR enabled
[ 82697.802] (II) Found 2 VGA devices: arbiter wrapping enabled
[ 82697.802] (II) Initializing built-in extension Generic Event Extension
[ 82697.802] (II) Initializing built-in extension SHAPE
[ 82697.802] (II) Initializing built-in extension MIT-SHM
[ 82697.802] (II) Initializing built-in extension XInputExtension
[ 82697.802] (II) Initializing built-in extension XTEST
[ 82697.802] (II) Initializing built-in extension BIG-REQUESTS
[ 82697.802] (II) Initializing built-in extension SYNC
[ 82697.803] (II) Initializing built-in extension XKEYBOARD
[ 82697.803] (II) Initializing built-in extension XC-MISC
[ 82697.803] (II) Initializing built-in extension SECURITY
[ 82697.803] (II) Initializing built-in extension XINERAMA
[ 82697.803] (II) Initializing built-in extension XFIXES
[ 82697.803] (II) Initializing built-in extension RENDER
[ 82697.803] (II) Initializing built-in extension RANDR
[ 82697.803] (II) Initializing built-in extension COMPOSITE
[ 82697.803] (II) Initializing built-in extension DAMAGE
[ 82697.826] (II) AIGLX: Screen 0 is not DRI2 capable
[ 82697.826] (II) AIGLX: Screen 0 is not DRI capable
[ 82697.957] (II) AIGLX: Loaded and initialized swrast
[ 82697.957] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[ 82698.197] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 82698.223] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 82698.224] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 82698.224] (II) LoadModule: "evdev"
[ 82698.224] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 82698.278] (II) Module evdev: vendor="X.Org Foundation"
[ 82698.278]     compiled for 1.11.3, module version = 2.7.0
[ 82698.278]     Module class: X.Org XInput Driver
[ 82698.278]     ABI class: X.Org XInput driver, version 16.0
[ 82698.278] (II) Using input driver 'evdev' for 'Power Button'
[ 82698.278] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 82698.278] (**) Power Button: always reports core events
[ 82698.278] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 82698.279] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 82698.279] (--) evdev: Power Button: Found keys
[ 82698.279] (II) evdev: Power Button: Configuring as keyboard
[ 82698.279] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[ 82698.279] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 82698.279] (**) Option "xkb_rules" "evdev"
[ 82698.279] (**) Option "xkb_model" "pc105"
[ 82698.279] (**) Option "xkb_layout" "us"
[ 82698.279] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[ 82698.287] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[ 82698.298] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 82698.298] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 82698.298] (II) Using input driver 'evdev' for 'Power Button'
[ 82698.298] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 82698.298] (**) Power Button: always reports core events
[ 82698.298] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 82698.299] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 82698.299] (--) evdev: Power Button: Found keys
[ 82698.299] (II) evdev: Power Button: Configuring as keyboard
[ 82698.299] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[ 82698.299] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[ 82698.299] (**) Option "xkb_rules" "evdev"
[ 82698.299] (**) Option "xkb_model" "pc105"
[ 82698.299] (**) Option "xkb_layout" "us"
[ 82698.299] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[ 82698.301] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
[ 82698.301] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[ 82698.301] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[ 82698.301] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 82698.302] (**) Logitech USB Optical Mouse: always reports core events
[ 82698.302] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event3"
[ 82698.302] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[ 82698.302] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[ 82698.302] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[ 82698.302] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[ 82698.302] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[ 82698.302] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[ 82698.302] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[ 82698.302] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[ 82698.302] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 82698.302] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:01.2/usb1/1-1/1-1:1.0/input/input3/event3"
[ 82698.302] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 8)
[ 82698.302] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[ 82698.303] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[ 82698.303] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[ 82698.303] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[ 82698.303] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[ 82698.304] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[ 82698.304] (II) No input driver specified, ignoring this device.
[ 82698.304] (II) This device may have been added with another device file.
[ 82698.305] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[ 82698.305] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 82698.306] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 82698.306] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 82698.306] (**) AT Translated Set 2 keyboard: always reports core events
[ 82698.306] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[ 82698.306] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[ 82698.306] (--) evdev: AT Translated Set 2 keyboard: Found keys
[ 82698.306] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[ 82698.306] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[ 82698.306] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[ 82698.306] (**) Option "xkb_rules" "evdev"
[ 82698.306] (**) Option "xkb_model" "pc105"
[ 82698.306] (**) Option "xkb_layout" "us"
[ 82698.306] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
```


The working console only session produces the same responses to these commands except [FONT=lucida console]lsmod[/FONT] which is the same as the 10.04 session save the radeon module shows "in use" by "0" instead of "2".

Here are those same commands under the 10.04.4 LiveCD session which seems to work just fine:

```
uname -a
Linux ubuntu 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
```

File versions
```

ii  libdrm-radeon1                       2.4.18-1ubuntu3                                 Userspace interface to radeon-specific kerne
ii  radeontool                           1.6.1-0ubuntu1                                  utility to control ATI Radeon backlight func
ii  xserver-xorg-video-radeon            1:6.13.0-1ubuntu5                               X.Org X server -- AMD/ATI Radeon display dri
ii  xorg                                 1:7.5+5ubuntu1.1                                X.Org X Window System
ii  xorg-docs-core                       1:1.5-1                                         Core documentation for the X.org X Window Sy
ii  xserver-xorg                         1:7.5+5ubuntu1.1                                the X.Org X server
ii  xserver-xorg-core                    2:1.7.6-2ubuntu7.10                             Xorg X server - core server
ii  xserver-xorg-input-all               1:7.5+5ubuntu1.1                                the X.Org X server -- input driver metapacka
ii  xserver-xorg-input-evdev             1:2.3.2-5ubuntu1                                X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse             1:1.5.0-1                                       X.Org X server -- mouse input driver
ii  xserver-xorg-video-all               1:7.5+5ubuntu1.1                                the X.Org X server -- output driver metapack
ii  xserver-xorg-video-ati               1:6.13.0-1ubuntu5                               X.Org X server -- AMD/ATI display driver wra
ii  xserver-xorg-video-fbdev             1:0.4.1-1ubuntu1                                X.Org X server -- fbdev display driver
ii  xserver-xorg-video-sis               1:0.10.2-2                                      X.Org X server -- SiS display driver
ii  xserver-xorg-video-vesa              1:2.3.0-1ubuntu1                                X.Org X server -- VESA display driver
```

```
sudo lspci -nnk -vvv -s 00:0d
00:0d.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)
    Subsystem: Hightech Information System Ltd. Device [1787:2020]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Region 1: I/O ports at 9400 [size=256]
    Region 2: Memory at bd000000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at 40020000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
**[COLOR=#ff0000]    Kernel driver in use: radeon[/COLOR]**
    Kernel modules: radeonfb, radeon

00:0d.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) [1002:5940] (rev 01)
    Subsystem: Hightech Information System Ltd. Device [1787:2021]
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 32 bytes
    Region 0: Memory at d8000000 (32-bit, prefetchable) [disabled] [size=128M]
    Region 1: Memory at bc800000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```

```
sudo lshw -c display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 630/730 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 21
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff(prefetchable) memory:bd800000-bd81ffff ioport:a800(size=128)
  *-display:0
       description: VGA compatible controller
       product: RV280 [Radeon 9200 PRO]
       vendor: ATI Technologies Inc
       physical id: d
       bus info: pci@0000:00:0d.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       [COLOR=#ff0000]**configuration: driver=radeon**[/COLOR] latency=32 mingnt=8
       resources: irq:11 memory:e8000000-efffffff(prefetchable) ioport:9400(size=256) memory:bd000000-bd00ffff memory:40020000-4003ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 PRO] (Secondary)
       vendor: ATI Technologies Inc
       physical id: d.1
       bus info: pci@0000:00:0d.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 mingnt=8
       resources: memory:d8000000-dfffffff(prefetchable) memory:bc800000-bc80ffff
```

```
lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
lp                      7028  0 
dm_crypt               11331  0 
snd_ice1724            95837  2 
snd_ice17xx_ak4xxx      2547  1 snd_ice1724
snd_ac97_codec        100646  1 snd_ice1724
snd_cmipci             30437  2 
ac97_bus                1002  1 snd_ac97_codec
snd_ak4xxx_adda         7364  2 snd_ice1724,snd_ice17xx_ak4xxx
gameport                9089  1 snd_cmipci
snd_ak4114              7450  1 snd_ice1724
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  5 snd_ice1724,snd_ac97_codec,snd_cmipci,snd_ak4114,snd_pcm_oss
snd_page_alloc          7076  1 snd_pcm
snd_opl3_lib            8966  1 snd_cmipci
snd_pt2258              2911  1 snd_ice1724
snd_hwdep               5412  1 snd_opl3_lib
snd_mpu401_uart         5617  1 snd_cmipci
snd_i2c                 4398  2 snd_ice1724,snd_pt2258
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  3 snd_ice1724,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ppdev                   5259  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          5700  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  26 snd_ice1724,snd_ac97_codec,snd_cmipci,snd_ak4xxx_adda,snd_ak4114,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_pt2258,snd_hwdep,snd_mpu401_uart,snd_i2c,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
parport                32635  3 lp,ppdev,parport_pc
shpchp                 28835  0 
i2c_sis630              4757  0 
soundcore               6620  1 snd
squashfs               20744  1 
aufs                  149050  1 
nls_cp437               4919  1 
isofs                  29250  1 
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
[COLOR=#ff0000][B]radeon                678831  2 
ttm                    49847  1 radeon[/B][/COLOR]
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
**[COLOR=#ff0000]drm_kms_helper         29329  1 radeon[/COLOR]**
softcursor              1189  1 bitblit
usbhid                 36110  0 
**[COLOR=#ff0000]drm                   163747  5 radeon,ttm,drm_kms_helper[/COLOR]**
sis_agp                 4015  1 
sis900                 17048  0 
vga16fb                11385  1 
hid                    67288  1 usbhid
**[COLOR=#ff0000]i2c_algo_bit            5028  1 radeon[/COLOR]**
e1000                  97435  0 
vgastate                8961  1 vga16fb
mii                     4381  1 sis900
agpgart                31724  3 ttm,drm,sis_agp
```

The Xorg.0.log from the LiveCD working session:
```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Build Date: 20 October 2011  03:05:54PM
xorg-server 2:1.7.6-2ubuntu7.10 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 15 23:47:22 2013
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
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:13:0) 1002:5960:1787:2020 ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xe8000000/134217728, 0xbd000000/65536, I/O @ 0x00009400/256, BIOS @ 0x????????/131072
(--) PCI: (0:0:13:1) 1002:5940:1787:2021 ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) rev 1, Mem @ 0xd8000000/134217728, 0xbc800000/65536
(--) PCI: (0:1:0:0) 1039:6300:1043:80e1 Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter rev 33, Mem @ 0xf0000000/134217728, 0xbd800000/131072, I/O @ 0x0000a800/128
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
(==) Matched ati as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 6.13.0
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
(II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
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
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
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
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
    CEDAR
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:0d:0
(II) [KMS] Kernel modesetting enabled.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
(II) RADEON(0): PCI card detected
(II) RADEON(0): KMS Color Tiling: disabled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:0d.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:0d.0
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: CTX  Model: 202a  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 46
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing not preferred mode in violation of standard!
(II) RADEON(0): redX: 0.637 redY: 0.348   greenX: 0.290 greenY: 0.610
(II) RADEON(0): blueX: 0.137 blueY: 0.080   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Serial No: LE554601055
(II) RADEON(0): Monitor name: X782
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff000e982a2000000000
(II) RADEON(0):     2e0f010308221b78e80526a3594a9c23
(II) RADEON(0):     144f54afcf0001010101010101010101
(II) RADEON(0):     010101010101302a009851002a403070
(II) RADEON(0):     1300520e1100001e000000fd00384b1e
(II) RADEON(0):     500e000a202020202020000000ff004c
(II) RADEON(0):     453535343630313035350a20000000fc
(II) RADEON(0):     00583738320a2020202020202020007e
(II) RADEON(0): EDID vendor "CTX", prod id 8234
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output VGA-0 using initial mode 1280x1024
(II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:7ac0000
(II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
(**) RADEON(0): Display dimensions: (340, 270) mm
(**) RADEON(0): DPI set to (95, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.5.0
    ABI class: X.Org Video Driver, version 6.0
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) RADEON(0): [DRI2] Setup complete
(II) RADEON(0): Front buffer size: 5120K
(II) RADEON(0): VRAM usage limit set to 108518K
(==) RADEON(0): Backing store disabled
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R200 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) EXA(0): Driver allocated offscreen pixmaps
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Set up textured video
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 338 x 270
(II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
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
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event4)
(**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Found relative axes
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
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
(II) RADEON(0): EDID vendor "CTX", prod id 8234
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): EDID vendor "CTX", prod id 8234
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): EDID vendor "CTX", prod id 8234
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): EDID vendor "CTX", prod id 8234
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): EDID vendor "CTX", prod id 8234
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): EDID vendor "CTX", prod id 8234
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
```

*I also don't understand why the modelines generated by DDC here in the log are different in their timings and flags from the ones generated by [FONT=lucida console]gtf[/FONT]. Could that be a problem?

---

### Post by Yellow Pasque on 2013-08-19
Chances are that this is fixed in newer kernel/X.

>  I also opted for sticking with the 12.04.1 hardware stack because the 12.04.2 (quantal) stack refused to produce a working gui at all using the onboard SiS chipset. I didn't want to roll that forward again unless necessary.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464)

---

### Post by EarlsFurniture on 2013-08-19
That bug report is where I gave up trying to get the quantal stack working and re-installed with a 12.04.1 CD.

But now I'm trying to get the Radeon working so...

---

### Post by Yellow Pasque on 2013-08-19
Well, you can try a liveUSB of 13.04 (I'd recommend Xubuntu or Lubuntu as they're lighter) to see if the issue has been fixed.

---

### Post by EarlsFurniture on 2013-08-19
Sorry, I should have included that info in my OP.

I have already tried the LiveCD route as you suggest.

I get the same results as the one with modesetting turned on - a blank screen.  Turning modesetting off in the boot parameters with a LiveCD gives me a usable system on Xubuntu 12.04.2 for only a few seconds and then it locks up as soon as I move the mouse. It was this testing with LiveCD's which allowed me to find out that the older 10.04.4 worked just fine.

Right now, it seems what I need is to find out why I get to the point of "screens found but none have a usable configuration" that is causing X to crash when as far as I know, my modelines should be appropriate for both the video card and the monitor, or failing that, why without an xorg.conf file, X can't seem to autoconfigure and use the radeon driver like it did back in 10.04.  But thanks anyway.

---

### Post by Yellow Pasque on 2013-08-19
> I have already tried the LiveCD route as you suggest.
But did you try 13.04?

---

### Post by Yellow Pasque on 2013-08-19
> Right now, it seems what I need is to find out why I get to the point of "screens found but none have a usable configuration" that is causing X to crash when as far as I know, my modelines should be appropriate for both the video card and the monitor, or failing that, why without an xorg.conf file, X can't seem to autoconfigure and use the radeon driver like it did back in 10.04

The problem goes deeper than xorg.conf or modelines.
```
[ 82695.420] (II) [KMS] drm report modesetting isn't supported.
```
Need to get that right first.

---

### Post by EarlsFurniture on 2013-08-20
> **Temüjin said:**
> The problem goes deeper than xorg.conf or modelines. ```
[ 82695.420] (II) [KMS] drm report modesetting isn't supported.
``` Need to get that right first.  Yes, Im not surprised it says that because in that session (where VESA is the driver which ends up being used) I have radeon.modeset=0 set in my /etc/default/grub. Note I mention that leaving this option out, or setting it to "1" results in a blank screen, a dead keyboard, and a system I can't SSH into, which I presume means the kernel is not loading in those cases.  The only way to get the kernel loading and any kind of usable system is to use nomodeset or radeon.modeset=0.  Hence, the message you see. Note also, in the 10.04.4 LiveCD session log - you don't see that message because modesetting is turned on by default on a LiveCD.  As well, from my understanding of how all this works, I can turn kernel modesetting off and specify the modes I want to use via xorg.conf, which I've done, but which produce the error "screens found but none have a usable configuration."  I'm not sure why I'm getting this error because the modes I've setup in xorg are straight out of my EDID from the logs and the modelines are generated by gtf and I've used the format for the xorg.conf straight from the xorg wiki. My initial suspicion is that something might be slightly off in my xorg.conf file, but if not, then I'm at a loss for the moment.

---

### Post by EarlsFurniture on 2013-08-22
> **Temüjin said:**
> But did you try 13.04?  Sorry for not replying to this specifically.  YES I did try 13.04 - the result:  with modesetting = bad display mode (odd graphic pattern on screen) without modesetting = vesa driver gets used  I'm not sure what "problem" you anticipated being fixed since I haven't exactly identified a "problem" yet other than generically, it won't use the radeon driver with the card on its own, and if I force it, it doesn't like any of the modes generated that allegedly the card and monitory can handle, yet an older kernel and xorg seemed to have no problems at all with this.  If an older kernel/xorg worked, and a newer one doesn't, I can't imagine the point of trying even newer kernel/xorg combos if we haven't even isolated what the actual problem is yet.  So no, the 13.04 versions don't work any better than the 12.04 set.  Somewhere between 10.04 and 12.04, they borked this up. (automatic modesetting) I should think it shouldn't be that difficult to figure out what and where. Certainly, my first inclination is that my config is wrong and that if it was corrected, then all should be just fine.  Unfortunately, I don't know enough about the guts of Xorg to see where my mistake is.  I would think the most likely solution lies in figuring out why my xorg.conf doesn't work at all since presumably, there's no good reason for that method of booting to fail.

---

### Post by EarlsFurniture on 2013-08-24
Technically, this isn't solved at all, but I saw no way to close the thread otherwise.

I've returned the Radeon s9250 card in exchange for a GeForce 6200 which I've tested to work properly from another machine.

I was never able to track down exactly why the 12.04 series kernel/xorg refuses to use the radeon driver or the generated modes, while the 10.04 series has no problem doing so automatically.

---

