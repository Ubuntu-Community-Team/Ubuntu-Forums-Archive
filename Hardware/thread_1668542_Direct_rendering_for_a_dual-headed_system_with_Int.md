---
title: "Direct rendering for a dual-headed system with Intel and ATI hardware"
date: 2011-01-16
forum: Hardware
---

### Post by sdstrowes on 2011-01-16
Hi,

I have been playing with the following for some time now, but can't quite get it right.

I am running a dual-card setup to drive two monitors, but neither card has dual outputs. To confuse matters, one card is Intel (VGA-out), one card is ATI (DVI-out). What I want is direct rendering so I can run Compiz.

It seems I can get direct rendering support with the proprietary ATI driver, but this is of no use: I am unable to configure X in any way that allows the simultaneous use of the ATI driver and the Intel hardware. It appears that I must use the open source radeon/ati driver bundled with X to achieve two screens.

I can successfully run two screens when I use the open drivers. However, the information I've seen on the web suggests that there should be some DRM support in the open driver, but DRM refuses to load. I have ensured that the correct kernel modules are loaded:
```

$ lsmod | grep radeon
radeon                827837  0 
ttm                    56633  1 radeon
drm_kms_helper         30168  2 radeon,i915
drm                   168054  5 radeon,ttm,i915,drm_kms_helper
i2c_algo_bit            5168  2 radeon,i915
$ lsmod | grep drm
drm_kms_helper         30168  2 radeon,i915
drm                   168054  5 radeon,ttm,i915,drm_kms_helper
agpgart                32011  3 ttm,drm,intel_agp
$

```

dmesg has the following promising information:
```
$ dmesg  | grep drm
[    6.537638] [drm] Initialized drm 1.1.0 20060810
[    6.603863] [drm] set up 31M of stolen space
[    6.604184] [drm] failed to find VBIOS tables
[    6.837700] fb0: inteldrmfb frame buffer device
[    6.837703] drm: registered panic notifier
[    6.840227] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[  597.167451] [drm] radeon defaulting to kernel modesetting.
[  597.167455] [drm] radeon kernel modesetting enabled.
```

If I disable basically everything in my xorg.conf apart from the Device section for the ATI card, just to get a single-screen running with direct rendering support, the following errors are contained within my Xorg.0.log:

```
[   883.422] (II) LoadModule: "dri"
[   883.423] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   883.423] (II) Module dri: vendor="X.Org Foundation"
[   883.423] 	compiled for 1.9.0, module version = 1.0.0
[   883.423] 	ABI class: X.Org Server Extension, version 4.0
[   883.423] (II) Loading extension XFree86-DRI
[   883.423] (II) LoadModule: "dri2"
[   883.424] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   883.424] (II) Module dri2: vendor="X.Org Foundation"
[   883.424] 	compiled for 1.9.0, module version = 1.2.0
[   883.424] 	ABI class: X.Org Server Extension, version 4.0
[   883.424] (II) Loading extension DRI2
[   883.424] (II) LoadModule: "ati"
[   883.424] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   883.424] (II) Module ati: vendor="X.Org Foundation"
[   883.424] 	compiled for 1.9.0, module version = 6.13.1
[   883.424] 	Module class: X.Org Video Driver
[   883.424] 	ABI class: X.Org Video Driver, version 8.0
[   883.424] (II) LoadModule: "radeon"
[   883.425] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   883.425] (II) Module radeon: vendor="X.Org Foundation"
[   883.425] 	compiled for 1.9.0, module version = 6.13.1
[   883.425] 	Module class: X.Org Video Driver
[   883.425] 	ABI class: X.Org Video Driver, version 8.0
[... snip ...]
[   883.447] drmOpenDevice: node name is /dev/dri/card0
[   883.447] drmOpenDevice: open result is 11, (OK)
[   883.447] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   883.447] drmOpenDevice: node name is /dev/dri/card0
[   883.447] drmOpenDevice: open result is 11, (OK)
[   883.447] drmOpenByBusid: drmOpenMinor returns 11
[   883.447] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   883.447] drmOpenDevice: node name is /dev/dri/card1
[   883.452] drmOpenByBusid: drmOpenMinor returns -1
[   883.452] drmOpenDevice: node name is /dev/dri/card2
[   883.456] drmOpenByBusid: drmOpenMinor returns -1
[   883.456] drmOpenDevice: node name is /dev/dri/card3
[   883.460] drmOpenByBusid: drmOpenMinor returns -1
[   883.460] drmOpenDevice: node name is /dev/dri/card4
[   883.464] drmOpenByBusid: drmOpenMinor returns -1
[   883.464] drmOpenDevice: node name is /dev/dri/card5
[   883.468] drmOpenByBusid: drmOpenMinor returns -1
[   883.468] drmOpenDevice: node name is /dev/dri/card6
[   883.473] drmOpenByBusid: drmOpenMinor returns -1
[   883.473] drmOpenDevice: node name is /dev/dri/card7
[   883.477] drmOpenByBusid: drmOpenMinor returns -1
[   883.477] drmOpenDevice: node name is /dev/dri/card8
[   883.481] drmOpenByBusid: drmOpenMinor returns -1
[   883.481] drmOpenDevice: node name is /dev/dri/card9
[   883.485] drmOpenByBusid: drmOpenMinor returns -1
[   883.485] drmOpenDevice: node name is /dev/dri/card10
[   883.489] drmOpenByBusid: drmOpenMinor returns -1
[   883.489] drmOpenDevice: node name is /dev/dri/card11
[   883.493] drmOpenByBusid: drmOpenMinor returns -1
[   883.493] drmOpenDevice: node name is /dev/dri/card12
[   883.497] drmOpenByBusid: drmOpenMinor returns -1
[   883.497] drmOpenDevice: node name is /dev/dri/card13
[   883.501] drmOpenByBusid: drmOpenMinor returns -1
[   883.502] drmOpenDevice: node name is /dev/dri/card14
[   883.506] drmOpenByBusid: drmOpenMinor returns -1
[   883.506] drmOpenDevice: node name is /dev/dri/card15
[   883.510] drmOpenByBusid: drmOpenMinor returns -1
[   883.510] drmOpenDevice: node name is /dev/dri/card0
[   883.510] drmOpenDevice: open result is 11, (OK)
[   883.510] drmOpenDevice: node name is /dev/dri/card0
[   883.510] drmOpenDevice: open result is 11, (OK)
[   883.510] drmOpenDevice: node name is /dev/dri/card1
[   883.514] drmOpenDevice: node name is /dev/dri/card2
[   883.518] drmOpenDevice: node name is /dev/dri/card3
[   883.522] drmOpenDevice: node name is /dev/dri/card4
[   883.527] drmOpenDevice: node name is /dev/dri/card5
[   883.531] drmOpenDevice: node name is /dev/dri/card6
[   883.535] drmOpenDevice: node name is /dev/dri/card7
[   883.539] drmOpenDevice: node name is /dev/dri/card8
[   883.543] drmOpenDevice: node name is /dev/dri/card9
[   883.547] drmOpenDevice: node name is /dev/dri/card10
[   883.551] drmOpenDevice: node name is /dev/dri/card11
[   883.555] drmOpenDevice: node name is /dev/dri/card12
[   883.560] drmOpenDevice: node name is /dev/dri/card13
[   883.564] drmOpenDevice: node name is /dev/dri/card14
[   883.568] drmOpenDevice: node name is /dev/dri/card15
[   883.572] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
```

So loading DRI fails, and glxinfo reports:
```
$ glxinfo 
name of display: :0.1
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13
```

What I can't tell from the errors above is *why* DRI failed to load. Has anybody else attempted to configure a tricky setup such as this?

My configuration is as follows:
[LIST]
[*]I am running the following hardware:
```
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450]
```
[*]I am running Ubuntu 10.10, and uname reports the kernel as follows: 2.6.35-23-generic #41-Ubuntu SMP
[*]My xorg.conf contains:```
## ONBOARD ###################################################################
Section "Device"
        Identifier      "Onboard Video Card"
        BusID           "PCI:0:2:0"
        Driver          "intel"
EndSection

Section "monitor"
        Identifier      "monitor1"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel"
EndSection

Section "screen"
        Identifier      "screen1"
        Device   "Onboard Video Card"
        Monitor  "monitor1"
EndSection

## PCI-E #####################################################################
Section "Device"
        Identifier      "PCIE Video Card"
        BusID           "PCI:1:0:0"
        Driver "ati"
EndSection

Section "monitor"
        Identifier      "Samsung"
        Vendorname      "Samsung"
        Modelname       "SyncMaster 940bw Plus"
EndSection

Section "screen"
        Identifier      "screen2"
        Device   "PCIE Video Card"
        Monitor  "Samsung"
EndSection

##############################################################################

Section "ServerLayout"
        Identifier      "Default Layout"
        screen 0 "screen1" 0 0
        screen 1 "screen2" 1441 0
EndSection

Section "ServerFlags"
        #Option "xinerama" "true"
        Option "DefaultServerLayout" "Default Layout"
EndSection
```
[/LIST]

---

