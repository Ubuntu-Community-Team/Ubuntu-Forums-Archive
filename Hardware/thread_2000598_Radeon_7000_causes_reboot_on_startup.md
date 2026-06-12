---
title: "Radeon 7000 causes reboot on startup"
date: 2012-06-09
forum: Hardware
---

### Post by Ortzinator on 2012-06-09
Ubuntu 12.04 won't boot when I enable the card in the BIOS. Nothing appears onscreen it just reboots as soon as (I think) it would show the login screen.

My computer is an [Optiplex 210L]("http://support.dell.com/support/edocs/systems/op210l/en/index.htm")

Here's the lspci for both devices:

```
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
03:02.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
```

Sorry if this isn't enough info, I'll be happy to provide more. I just don't know where to look for error and such.

---

### Post by Ortzinator on 2012-06-11
```
brian@brian-opti:~$ dmesg | grep drm
[    5.608821] [drm] Initialized drm 1.1.0 20060810
[    5.798840] [drm] radeon defaulting to kernel modesetting.
[    5.798847] [drm] radeon kernel modesetting enabled.
[    5.868337] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.868343] [drm] Driver supports precise vblank timestamp query.
[    6.016999] [drm] initialized overlay support
[    6.192034] fbcon: inteldrmfb (fb0) is primary device
[    6.193619] fb0: inteldrmfb frame buffer device
[    6.193622] drm: registered panic notifier
[    6.193653] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    6.193979] [drm] initializing kernel modesetting (RV100 0x1002:0x5159 0x1092:0x0040).
[    6.194015] [drm] register mmio base: 0xDFBF0000
[    6.194018] [drm] register mmio size: 65536
[    6.291769] [drm] GPU not posted. posting now...
[    6.313595] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    6.313599] [drm] Driver supports precise vblank timestamp query.
[    6.313648] [drm] radeon: irq initialized.
[    6.313790] [drm] Detected VRAM RAM=128M, BAR=128M
[    6.313795] [drm] RAM width 64bits DDR
[    6.313927] [drm] radeon: 128M of VRAM memory ready
[    6.313931] [drm] radeon: 512M of GTT memory ready.
[    6.313966] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    6.337561] [drm] Loading R100 Microcode
[    6.341091] [drm] radeon: ring at 0x00000000B0001000
[    6.341114] [drm] ring test succeeded in 0 usecs
[    6.341309] [drm] radeon: ib pool ready.
[    6.342419] [drm] ib test succeeded in 0 usecs
[    6.342752] [drm] Radeon Display Connectors
[    6.342756] [drm] Connector 0:
[    6.342758] [drm]   VGA
[    6.342762] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    6.342765] [drm]   Encoders:
[    6.342767] [drm]     CRT1: INTERNAL_DAC1
[    6.342770] [drm] Connector 1:
[    6.342772] [drm]   DVI-I
[    6.342774] [drm]   HPD1
[    6.342777] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    6.342779] [drm]   Encoders:
[    6.342782] [drm]     CRT2: INTERNAL_DAC2
[    6.342784] [drm]     DFP1: INTERNAL_TMDS1
[    6.357228] [drm] Radeon display connector VGA-2: No monitor connected or invalid EDID
[    6.412706] [drm] Radeon display connector DVI-I-1: Found valid EDID
[    6.539275] [drm] fb mappable at 0xD0040000
[    6.539279] [drm] vram apper at 0xD0000000
[    6.539282] [drm] size 5242880
[    6.539284] [drm] fb depth is 24
[    6.539286] [drm]    pitch is 5120
[    6.539530] fb1: radeondrmfb frame buffer device
[    6.539544] [drm] Initialized radeon 2.10.0 20080528 for 0000:03:01.0 on minor 1

```

This seems to suggest that it is working despite not being selected in the BIOS, however the monitor is blank... Any ideas?

---

