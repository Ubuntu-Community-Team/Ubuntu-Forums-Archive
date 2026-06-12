---
title: "ati 7400m LAGGY"
date: 2012-07-02
forum: Hardware
---

### Post by z3nhakr on 2012-07-02
whenever i run a game or even some fullscreen applications like xbmc my video lags. especially the cursor. Cube2 works the best out of all the games ive tried but even then i only get about 10 fps or less fullscreen. any ideas?
here's the specs:
lenovo u400
ubuntu 12.04 64 bit
2nd gen i7 (2.7 ghz)
radeon HD 7400m
8gb ram

oh and i attached the card specs in the screenshot

p.s. its one of those new switchable cards :s
TIA

---

### Post by gordintoronto on 2012-07-02
How odd: the Lenovo site does not suggest that the U400 has switchable graphics.

[http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/builder.workflow:Enter?mtm-item=%3A000001C9%3A0000179E%3A](http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/builder.workflow:Enter?mtm-item=%3A000001C9%3A0000179E%3A)

What version of Ubuntu do you use? Did you install the FGLRX driver using Additional Drivers?

---

### Post by typhoon_tip on 2012-07-02
There are tens of threads about laggyness of AMD/ATI in this forum, just do a bit of search and you will find plenty. Just tweak vsync settings in compiz and other few things, and it will work perfectly. :popcorn:

---

### Post by z3nhakr on 2012-07-15
> **gordintoronto said:**
> How odd: the Lenovo site does not suggest that the U400 has switchable graphics.

[http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/builder.workflow:Enter?mtm-item=%3A000001C9%3A0000179E%3A](http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/builder.workflow:Enter?mtm-item=%3A000001C9%3A0000179E%3A)

What version of Ubuntu do you use? Did you install the FGLRX driver using Additional Drivers?

says so here: [http://www.lenovo.com/products/us/laptop/ideapad/u-series/u400/IdeaPad_U400_Datasheet_US.pdf]("http://www.lenovo.com/products/us/laptop/ideapad/u-series/u400/IdeaPad_U400_Datasheet_US.pdf")

first i used additional hardware but it would only let me install the release version and i got an error whenever i tried to install the post release updates. currently it shows non of the drivers as active because i installed it through software center (still not post release update). atm it's switched to the intel card because it runs smoother but the intel chipset doesnt support acceleration so i cant play most games including minecraft :( and im stuck on unity 2D.

---

### Post by z3nhakr on 2012-07-15
> **typhoon_tip said:**
> There are tens of threads about laggyness of AMD/ATI in this forum, just do a bit of search and you will find plenty. Just tweak vsync settings in compiz and other few things, and it will work perfectly. :popcorn:

TBH i hadnt considered compiz.but would that affect how it runs in a fullscreen game?

---

### Post by z3nhakr on 2012-07-19
i install the compiz settings gui and disable "force sync vblank" and enable some fglrx option under workarounds but it didnt change anything.

---

### Post by typhoon_tip on 2012-07-19
Post your config file:
```
sudo cat /etc/X11/xorg.conf
```

---

### Post by z3nhakr on 2012-07-20
> **typhoon_tip said:**
> Post your config file:
```
sudo cat /etc/X11/xorg.conf
```

```
Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection


```

---

### Post by typhoon_tip on 2012-07-23
Are you using Gnome Shell or Unity ?

By the way, please try XBMC by entering it from the login panel instead of launching it as an app. It should make a big difference. That'll help identifying the issue (together with question above !).

---

### Post by z3nhakr on 2012-07-24
> **typhoon_tip said:**
> Are you using Gnome Shell or Unity ?

I'm using unity
> **typhoon_tip said:**
> By the way, please try XBMC by entering it from the login panel instead of launching it as an app. It should make a big difference. That'll help identifying the issue (together with question above !).et
tried it and it runs faster than before but the mouse is still a bit delayed and im only getting 44 fps, thats double what i was getting before but still nowhere near what i should be getting with a 1gb graphics card

---

### Post by typhoon_tip on 2012-07-25
> **z3nhakr said:**
> I'm using unity
et
tried it and it runs faster than before but the mouse is still a bit delayed and im only getting 44 fps, thats double what i was getting before but still nowhere near what i should be getting with a 1gb graphics card

OK. Now, can you go to XBMC video driver settings (System/Settings/System again): where is set "Video Sync", should be set to "let driver choose video sync", or "enabled" and "disabled". Can you play around with those options and see if you notice any improvement ?

By the way, how do you know you get 44 fps ? From reported frame rate of XBMC ?

---

### Post by z3nhakr on 2012-07-25
i got the fps from system info in xbmc. i tried every vsync setting on xbmc but nothing changed. it almost makes me think that vsync is stuck on.

---

### Post by typhoon_tip on 2012-07-25
OK, please now try this: login to Unity, in AMD Catalyst Control Center, untick "Tear free desktop", and click apply.

Then, logoff and try XBMC again, leaving that option to "Let driver choose", the frame rate should jump to 90 or more fps.

---

### Post by z3nhakr on 2012-07-25
i don't have that option in CCC. can i change that manually? maybe in /etc/ati/amdpcsdb ?

---

### Post by typhoon_tip on 2012-07-26
> **z3nhakr said:**
> i don't have that option in CCC. can i change that manually? maybe in /etc/ati/amdpcsdb ?

??? that's impossible... how did you install the drivers ? Trough "Additional Drivers" interface or manually with ATI installer ?

---

### Post by z3nhakr on 2012-07-26
yep i installed it with jockey. i attached a screenshot of my CCC gui
[IMG]http://ubuntuone.com/3JlAg491vRriKlBoSRYMX2[/IMG]

---

### Post by typhoon_tip on 2012-07-27
Is very weird indeed... Switchable Graphic working fine, but no tear free option. You could try to update the driver with the one from AMD website.

Follow closely the instructions here:
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Especially:
"Removing Catalyst/fglrx": follow this procedure totally, including restoring radeon driver. Do not skip any command, and pay attention to the 64/32 bit variant !!

"Installing Catalyst Manually (from AMD/ATI's site)": pay attention to Before you start for pre-requisites and do all commands as instructed !!

---

### Post by z3nhakr on 2012-08-03
i followed the instructions but it locked me out and i had to go back to the older drivers.  strangely at the bottom of the xorg log vsync is mentioned. does that mean it's enabled?

```
[    11.437] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    11.437] X Protocol Version 11, Revision 0
[    11.437] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[    11.437] Current Operating System: Linux ubuntu 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64
[    11.437] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic root=UUID=c5400253-fe9a-4d2c-86be-44ac51dab510 ro quiet splash vt.handoff=7
[    11.437] Build Date: 16 July 2012  08:06:31PM
[    11.437] xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see http://www.ubuntu.com/support) 
[    11.437] Current version of pixman: 0.24.4
[    11.437]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    11.437] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.437] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  3 20:06:56 2012
[    11.448] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.448] (==) No Layout section.  Using the first Screen section.
[    11.448] (==) No screen section available. Using defaults.
[    11.448] (**) |-->Screen "Default Screen Section" (0)
[    11.448] (**) |   |-->Monitor "<default monitor>"
[    11.448] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    11.448] (==) Automatically adding devices
[    11.448] (==) Automatically enabling devices
[    11.448] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.448]     Entry deleted from font path.
[    11.448] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.448]     Entry deleted from font path.
[    11.448] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.448]     Entry deleted from font path.
[    11.448] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.448]     Entry deleted from font path.
[    11.448] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.448]     Entry deleted from font path.
[    11.448] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    11.448]     Entry deleted from font path.
[    11.448] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    11.448] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.448] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.448] (II) Loader magic: 0x7f3b52da9b00
[    11.448] (II) Module ABI versions:
[    11.448]     X.Org ANSI C Emulation: 0.4
[    11.448]     X.Org Video Driver: 11.0
[    11.448]     X.Org XInput driver : 16.0
[    11.448]     X.Org Server Extension : 6.0
[    11.449] (--) PCI:*(0:0:2:0) 8086:0126:17aa:3976 rev 9, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x00003000/64
[    11.449] (--) PCI: (0:1:0:0) 1002:6760:17aa:3976 rev 0, Mem @ 0xd0000000/268435456, 0xf0600000/131072, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    11.449] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.449] (II) LoadModule: "extmod"
[    11.470] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.471] (II) Module extmod: vendor="X.Org Foundation"
[    11.471]     compiled for 1.11.3, module version = 1.0.0
[    11.471]     Module class: X.Org Server Extension
[    11.471]     ABI class: X.Org Server Extension, version 6.0
[    11.471] (II) Loading extension MIT-SCREEN-SAVER
[    11.471] (II) Loading extension XFree86-VidModeExtension
[    11.471] (II) Loading extension XFree86-DGA
[    11.471] (II) Loading extension DPMS
[    11.471] (II) Loading extension XVideo
[    11.471] (II) Loading extension XVideo-MotionCompensation
[    11.471] (II) Loading extension X-Resource
[    11.471] (II) LoadModule: "dbe"
[    11.471] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.471] (II) Module dbe: vendor="X.Org Foundation"
[    11.471]     compiled for 1.11.3, module version = 1.0.0
[    11.471]     Module class: X.Org Server Extension
[    11.471]     ABI class: X.Org Server Extension, version 6.0
[    11.471] (II) Loading extension DOUBLE-BUFFER
[    11.471] (II) LoadModule: "glx"
[    11.471] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    11.471] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    11.471]     compiled for 6.9.0, module version = 1.0.0
[    11.471] (II) Loading extension GLX
[    11.471] (II) LoadModule: "record"
[    11.471] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.471] (II) Module record: vendor="X.Org Foundation"
[    11.471]     compiled for 1.11.3, module version = 1.13.0
[    11.471]     Module class: X.Org Server Extension
[    11.471]     ABI class: X.Org Server Extension, version 6.0
[    11.471] (II) Loading extension RECORD
[    11.471] (II) LoadModule: "dri"
[    11.472] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.472] (II) Module dri: vendor="X.Org Foundation"
[    11.472]     compiled for 1.11.3, module version = 1.0.0
[    11.472]     ABI class: X.Org Server Extension, version 6.0
[    11.472] (II) Loading extension XFree86-DRI
[    11.472] (II) LoadModule: "dri2"
[    11.472] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.472] (II) Module dri2: vendor="X.Org Foundation"
[    11.472]     compiled for 1.11.3, module version = 1.2.0
[    11.472]     ABI class: X.Org Server Extension, version 6.0
[    11.472] (II) Loading extension DRI2
[    11.472] (==) Matched intel as autoconfigured driver 0
[    11.472] (==) Matched vesa as autoconfigured driver 1
[    11.472] (==) Matched fbdev as autoconfigured driver 2
[    11.472] (==) Assigned the driver to the xf86ConfigLayout
[    11.472] (II) LoadModule: "intel"
[    11.472] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.472] (II) Module intel: vendor="X.Org Foundation"
[    11.472]     compiled for 1.11.3, module version = 2.17.0
[    11.472]     Module class: X.Org Video Driver
[    11.472]     ABI class: X.Org Video Driver, version 11.0
[    11.472] (II) LoadModule: "vesa"
[    11.472] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.472] (II) Module vesa: vendor="X.Org Foundation"
[    11.472]     compiled for 1.11.3, module version = 2.3.0
[    11.472]     Module class: X.Org Video Driver
[    11.472]     ABI class: X.Org Video Driver, version 11.0
[    11.472] (II) LoadModule: "fbdev"
[    11.473] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.473] (II) Module fbdev: vendor="X.Org Foundation"
[    11.473]     compiled for 1.11.3, module version = 0.4.2
[    11.473]     ABI class: X.Org Video Driver, version 11.0
[    11.473] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    11.473] (II) VESA: driver for VESA chipsets: vesa
[    11.473] (II) FBDEV: driver for framebuffer: fbdev
[    11.473] (++) using VT number 7

[    11.474] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    11.474] (WW) Falling back to old probe method for vesa
[    11.474] (WW) Falling back to old probe method for fbdev
[    11.474] (II) Loading sub module "fbdevhw"
[    11.474] (II) LoadModule: "fbdevhw"
[    11.474] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.474] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.474]     compiled for 1.11.3, module version = 0.0.2
[    11.474]     ABI class: X.Org Video Driver, version 11.0
[    11.474] drmOpenDevice: node name is /dev/dri/card0
[    11.474] drmOpenDevice: open result is 9, (OK)
[    11.474] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    11.474] drmOpenDevice: node name is /dev/dri/card0
[    11.474] drmOpenDevice: open result is 9, (OK)
[    11.474] drmOpenByBusid: drmOpenMinor returns 9
[    11.474] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    11.474] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    11.474] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    11.474] (==) intel(0): RGB weight 888
[    11.474] (==) intel(0): Default visual is TrueColor
[    11.474] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2+)
[    11.474] (--) intel(0): Chipset: "Sandybridge Mobile (GT2+)"
[    11.474] (**) intel(0): Relaxed fencing enabled
[    11.474] (**) intel(0): Wait on SwapBuffers? enabled
[    11.474] (**) intel(0): Triple buffering? enabled
[    11.474] (**) intel(0): Framebuffer tiled
[    11.474] (**) intel(0): Pixmaps tiled
[    11.474] (**) intel(0): 3D buffers tiled
[    11.474] (**) intel(0): SwapBuffers wait enabled
[    11.474] (==) intel(0): video overlay key set to 0x101fe
[    11.474] (II) intel(0): Output LVDS1 has no monitor section
[    11.475] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[    11.475] (II) intel(0): Output VGA1 has no monitor section
[    11.479] (II) intel(0): Output HDMI1 has no monitor section
[    11.528] (II) intel(0): Output DP1 has no monitor section
[    11.533] (II) intel(0): EDID for output LVDS1
[    11.533] (II) intel(0): Manufacturer: AUO  Model: 303c  Serial#: 0
[    11.533] (II) intel(0): Year: 2010  Week: 0
[    11.533] (II) intel(0): EDID Version: 1.3
[    11.533] (II) intel(0): Digital Display Input
[    11.533] (II) intel(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[    11.533] (II) intel(0): Gamma: 2.20
[    11.533] (II) intel(0): No DPMS capabilities specified
[    11.533] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    11.533] (II) intel(0): First detailed timing is preferred mode
[    11.533] (II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.340 greenY: 0.570
[    11.533] (II) intel(0): blueX: 0.150 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    11.533] (II) intel(0): Manufacturer's mask: 0
[    11.533] (II) intel(0): Supported detailed timing:
[    11.533] (II) intel(0): clock: 69.3 MHz   Image Size:  309 x 173 mm
[    11.533] (II) intel(0): h_active: 1366  h_sync: 1404  h_sync_end 1426 h_blank_end 1436 h_border: 0
[    11.533] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[    11.533] (II) intel(0): Unknown vendor-specific block f
[    11.533] (II) intel(0):  AUO
[    11.533] (II) intel(0):  B140XW03 V0
[    11.533] (II) intel(0): EDID (in hex):
[    11.533] (II) intel(0):     00ffffffffffff0006af3c3000000000
[    11.533] (II) intel(0):     00140103801f11780a10b59758579226
[    11.533] (II) intel(0):     1e505400000001010101010101010101
[    11.533] (II) intel(0):     010101010101121b5646500023302616
[    11.533] (II) intel(0):     360035ad100000180000000f00000000
[    11.533] (II) intel(0):     00000000000000000020000000fe0041
[    11.533] (II) intel(0):     554f0a202020202020202020000000fe
[    11.533] (II) intel(0):     004231343058573033205630200a002b
[    11.533] (II) intel(0): EDID vendor "AUO", prod id 12348
[    11.533] (II) intel(0): Printing DDC gathered Modelines:
[    11.533] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1404 1426 1436  768 771 777 803 -hsync -vsync (48.3 kHz)
[    11.533] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    11.533] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    11.533] (II) intel(0): Printing probed modes for output LVDS1
[    11.533] (II) intel(0): Modeline "1366x768"x60.1   69.30  1366 1404 1426 1436  768 771 777 803 -hsync -vsync (48.3 kHz)
[    11.533] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    11.533] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    11.534] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    11.534] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    11.534] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    11.534] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    11.534] (II) intel(0): EDID for output VGA1
[    11.538] (II) intel(0): EDID for output HDMI1
[    11.584] (II) intel(0): EDID for output DP1
[    11.584] (II) intel(0): Output LVDS1 connected
[    11.584] (II) intel(0): Output VGA1 disconnected
[    11.584] (II) intel(0): Output HDMI1 disconnected
[    11.584] (II) intel(0): Output DP1 disconnected
[    11.584] (II) intel(0): Using exact sizes for initial modes
[    11.584] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    11.584] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    11.584] (II) intel(0): Kernel page flipping support detected, enabling
[    11.584] (**) intel(0): Display dimensions: (310, 170) mm
[    11.584] (**) intel(0): DPI set to (111, 114)
[    11.584] (II) Loading sub module "fb"
[    11.584] (II) LoadModule: "fb"
[    11.584] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.584] (II) Module fb: vendor="X.Org Foundation"
[    11.584]     compiled for 1.11.3, module version = 1.0.0
[    11.584]     ABI class: X.Org ANSI C Emulation, version 0.4
[    11.584] (II) Loading sub module "dri2"
[    11.584] (II) LoadModule: "dri2"
[    11.584] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.584] (II) Module dri2: vendor="X.Org Foundation"
[    11.584]     compiled for 1.11.3, module version = 1.2.0
[    11.584]     ABI class: X.Org Server Extension, version 6.0
[    11.584] (II) UnloadModule: "vesa"
[    11.584] (II) Unloading vesa
[    11.584] (II) UnloadModule: "fbdev"
[    11.584] (II) Unloading fbdev
[    11.584] (II) UnloadModule: "fbdevhw"
[    11.584] (II) Unloading fbdevhw
[    11.584] (==) Depth 24 pixmap format is 32 bpp
[    11.584] (II) intel(0): [DRI2] Setup complete
[    11.584] (II) intel(0): [DRI2]   DRI driver: i965
[    11.584] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    11.585] (II) UXA(0): Driver registered support for the following operations:
[    11.585] (II)         solid
[    11.585] (II)         copy
[    11.585] (II)         composite (RENDER acceleration)
[    11.585] (II)         put_image
[    11.585] (II)         get_image
[    11.585] (==) intel(0): Backing store disabled
[    11.585] (==) intel(0): Silken mouse enabled
[    11.585] (II) intel(0): Initializing HW Cursor
[    11.644] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    11.645] (==) intel(0): DPMS enabled
[    11.645] (==) intel(0): Intel XvMC decoder enabled
[    11.645] (II) intel(0): Set up textured video
[    11.646] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    11.646] (II) intel(0): direct rendering: DRI2 Enabled
[    11.646] (==) intel(0): hotplug detection: "enabled"
[    11.646] (--) RandR disabled
[    11.646] (II) Initializing built-in extension Generic Event Extension
[    11.646] (II) Initializing built-in extension SHAPE
[    11.646] (II) Initializing built-in extension MIT-SHM
[    11.646] (II) Initializing built-in extension XInputExtension
[    11.646] (II) Initializing built-in extension XTEST
[    11.646] (II) Initializing built-in extension BIG-REQUESTS
[    11.646] (II) Initializing built-in extension SYNC
[    11.646] (II) Initializing built-in extension XKEYBOARD
[    11.646] (II) Initializing built-in extension XC-MISC
[    11.646] (II) Initializing built-in extension SECURITY
[    11.646] (II) Initializing built-in extension XINERAMA
[    11.646] (II) Initializing built-in extension XFIXES
[    11.646] (II) Initializing built-in extension RENDER
[    11.646] (II) Initializing built-in extension RANDR
[    11.646] (II) Initializing built-in extension COMPOSITE
[    11.646] (II) Initializing built-in extension DAMAGE
[    11.647] (EE) GLX error: Can not get required symbols.
[    11.649] (II) intel(0): Setting screen physical size to 361 x 203
[    11.653] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    11.654] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    11.654] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.654] (II) LoadModule: "evdev"
[    11.655] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.655] (II) Module evdev: vendor="X.Org Foundation"
[    11.655]     compiled for 1.11.3, module version = 2.7.0
[    11.655]     Module class: X.Org XInput Driver
[    11.655]     ABI class: X.Org XInput driver, version 16.0
[    11.655] (II) Using input driver 'evdev' for 'Power Button'
[    11.655] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.655] (**) Power Button: always reports core events
[    11.655] (**) evdev: Power Button: Device: "/dev/input/event2"
[    11.655] (--) evdev: Power Button: Vendor 0 Product 0x1
[    11.655] (--) evdev: Power Button: Found keys
[    11.655] (II) evdev: Power Button: Configuring as keyboard
[    11.655] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    11.655] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    11.655] (**) Option "xkb_rules" "evdev"
[    11.655] (**) Option "xkb_model" "pc105"
[    11.655] (**) Option "xkb_layout" "us"
[    11.655] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    11.655] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    11.655] (II) Using input driver 'evdev' for 'Video Bus'
[    11.655] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.655] (**) Video Bus: always reports core events
[    11.655] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    11.655] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    11.655] (--) evdev: Video Bus: Found keys
[    11.655] (II) evdev: Video Bus: Configuring as keyboard
[    11.655] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8/event8"
[    11.655] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    11.655] (**) Option "xkb_rules" "evdev"
[    11.655] (**) Option "xkb_model" "pc105"
[    11.655] (**) Option "xkb_layout" "us"
[    11.655] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    11.655] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    11.655] (II) Using input driver 'evdev' for 'Video Bus'
[    11.655] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.656] (**) Video Bus: always reports core events
[    11.656] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    11.656] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    11.656] (--) evdev: Video Bus: Found keys
[    11.656] (II) evdev: Video Bus: Configuring as keyboard
[    11.656] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:32/LNXVIDEO:00/input/input7/event7"
[    11.656] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    11.656] (**) Option "xkb_rules" "evdev"
[    11.656] (**) Option "xkb_model" "pc105"
[    11.656] (**) Option "xkb_layout" "us"
[    11.656] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    11.656] (II) No input driver specified, ignoring this device.
[    11.656] (II) This device may have been added with another device file.
[    11.656] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    11.656] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    11.656] (II) Using input driver 'evdev' for 'Sleep Button'
[    11.656] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.656] (**) Sleep Button: always reports core events
[    11.656] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    11.656] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    11.656] (--) evdev: Sleep Button: Found keys
[    11.656] (II) evdev: Sleep Button: Configuring as keyboard
[    11.656] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    11.656] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    11.656] (**) Option "xkb_rules" "evdev"
[    11.656] (**) Option "xkb_model" "pc105"
[    11.656] (**) Option "xkb_layout" "us"
[    11.656] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event5)
[    11.656] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    11.656] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    11.656] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.656] (**) Lenovo EasyCamera: always reports core events
[    11.656] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event5"
[    11.656] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x30c
[    11.656] (--) evdev: Lenovo EasyCamera: Found keys
[    11.656] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    11.656] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input5/event5"
[    11.656] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 10)
[    11.656] (**) Option "xkb_rules" "evdev"
[    11.656] (**) Option "xkb_model" "pc105"
[    11.656] (**) Option "xkb_layout" "us"
[    11.657] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    11.657] (II) No input driver specified, ignoring this device.
[    11.657] (II) This device may have been added with another device file.
[    11.657] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    11.657] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    11.657] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    11.657] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.657] (**) AT Translated Set 2 keyboard: always reports core events
[    11.657] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    11.657] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    11.657] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    11.657] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    11.657] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    11.657] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    11.657] (**) Option "xkb_rules" "evdev"
[    11.657] (**) Option "xkb_model" "pc105"
[    11.657] (**) Option "xkb_layout" "us"
[    11.657] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event6)
[    11.657] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    11.657] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    11.657] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.657] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    11.657] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event6"
[    11.657] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5
[    11.657] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    11.657] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    11.657] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes
[    11.657] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    11.657] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    11.657] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    11.657] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    11.657] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.657] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    11.657] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 12)
[    11.657] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    11.657] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    11.657] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    11.658] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    11.658] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    11.658] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    11.658] (II) No input driver specified, ignoring this device.
[    11.658] (II) This device may have been added with another device file.
[    11.658] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event4)
[    11.658] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    11.658] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    11.658] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.658] (**) Ideapad extra buttons: always reports core events
[    11.658] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event4"
[    11.658] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    11.658] (--) evdev: Ideapad extra buttons: Found keys
[    11.658] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    11.658] (**) Option "config_info" "udev:/sys/devices/platform/ideapad/input/input4/event4"
[    11.658] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 13)
[    11.658] (**) Option "xkb_rules" "evdev"
[    11.658] (**) Option "xkb_model" "pc105"
[    11.658] (**) Option "xkb_layout" "us"
[    13.874] (II) intel(0): EDID vendor "AUO", prod id 12348
[    13.874] (II) intel(0): Printing DDC gathered Modelines:
[    13.874] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1404 1426 1436  768 771 777 803 -hsync -vsync (48.3 kHz)
[    18.140] (II) intel(0): EDID vendor "AUO", prod id 12348
[    18.140] (II) intel(0): Printing DDC gathered Modelines:
[    18.140] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1404 1426 1436  768 771 777 803 -hsync -vsync (48.3 kHz)
[    24.140] (II) intel(0): EDID vendor "AUO", prod id 12348
[    24.140] (II) intel(0): Printing DDC gathered Modelines:
[    24.140] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1404 1426 1436  768 771 777 803 -hsync -vsync (48.3 kHz)
[    24.607] (II) intel(0): EDID vendor "AUO", prod id 12348
[    24.607] (II) intel(0): Printing DDC gathered Modelines:
[    24.607] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1404 1426 1436  768 771 777 803 -hsync -vsync (48.3 kHz)
[    25.567] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    31.101] (II) intel(0): EDID vendor "AUO", prod id 12348
[    31.101] (II) intel(0): Printing DDC gathered Modelines:
[    31.101] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1404 1426 1436  768 771 777 803 -hsync -vsync (48.3 kHz)
[    48.507] (II) intel(0): EDID vendor "AUO", prod id 12348
[    48.507] (II) intel(0): Printing DDC gathered Modelines:
[    48.507] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1404 1426 1436  768 771 777 803 -hsync -vsync (48.3 kHz)
```

---

### Post by z3nhakr on 2012-08-03
I just got it working by installing the latest drivers from amd WITHOUT making a deb package. Seems to be that the new drivers (12.6) don't work correctly when installed with a deb.

---

