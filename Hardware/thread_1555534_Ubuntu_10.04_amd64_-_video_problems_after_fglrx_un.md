---
title: "Ubuntu 10.04 amd64 - video problems after fglrx uninstall"
date: 2010-08-18
forum: Hardware
---

### Post by satch5841 on 2010-08-18
Hello everybody!
I've got a problem since I uninstalled fglrx: the video is so sloooowly responding and even dragging a window is a big pain in the ...

I tried with the methods described here:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
but nothing helps.

Even tried to install the radeonhd driver but without success!

I've done a fresh Kubuntu 10.04 install (I need to set Multiseat, that's why I decided to uninstall fglrx before setting up kdm on ubuntu) on a different partition and all works fine without installing the proprietary driver.

What seems strange to me is this output:
```
dmesg | grep drm
[    0.000000] Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
[    1.173241] [drm] Initialized drm 1.1.0 20060810
[    1.799442] [drm] VGACON disable radeon kernel modesetting.
[    1.800064] [drm] Initialized radeon 1.32.0 20080528 for 0000:02:00.0 on minor 0
[    1.800283] [drm] Initialized radeon 1.32.0 20080528 for 0000:01:05.0 on minor 1

```while on the working Kubuntu it looks like this:
```
dmesg | grep drm
[    0.000000] Linux version 2.6.32-24-generic  (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu  SMP Wed Jul 28 05:14:15 UTC 2010 (Ubuntu 2.6.32-24.39-generic  2.6.32.15+drm33.5)
[    5.973138] [drm] Initialized drm 1.1.0 20060810
[    6.215752] [drm] radeon defaulting to kernel modesetting.
[    6.215754] [drm] radeon kernel modesetting enabled.
[    6.217107] [drm] radeon: Initializing kernel modesetting.
[    6.217166] [drm] register mmio base: 0xFDAE0000
[    6.217167] [drm] register mmio size: 65536
[    6.226601] [drm] Clocks initialized !
[    6.227852] [drm] Detected VRAM RAM=256M, BAR=256M
[    6.227856] [drm] RAM width 32bits DDR
[    6.227962] [drm] radeon: 256M of VRAM memory ready
[    6.227964] [drm] radeon: 512M of GTT memory ready.
[    6.227987] [drm] radeon: irq initialized.
[    6.227989] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    6.228336] [drm] Loading RS780 Microcode
[    6.515990] [drm] ring test succeeded in 1 usecs
[    6.516051] [drm] radeon: ib pool ready.
[    6.516101] [drm] ib test succeeded in 0 usecs
[    6.516102] [drm] Enabling audio support
[    6.516371] [drm] Radeon Display Connectors
[    6.516372] [drm] Connector 0:
[    6.516373] [drm]   VGA
[    6.516375] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    6.516376] [drm]   Encoders:
[    6.516377] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    6.516378] [drm] Connector 1:
[    6.516379] [drm]   DVI-D
[    6.516380] [drm]   HPD1
[    6.516381] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    6.516382] [drm]   Encoders:
[    6.516383] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[    6.632811] [drm] fb mappable at 0xC0141000
[    6.632813] [drm] vram apper at 0xC0000000
[    6.632814] [drm] size 5242880
[    6.632815] [drm] fb depth is 24
[    6.632815] [drm]    pitch is 5120
[    6.632860] fb1: radeondrmfb frame buffer device
[    6.632865] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[    6.634935] [drm] radeon: Initializing kernel modesetting.
[    6.634995] [drm] register mmio base: 0xFDFE0000
[    6.634995] [drm] register mmio size: 65536
[    6.635260] [drm] Clocks initialized !
[    6.636536] [drm] Detected VRAM RAM=256M, BAR=256M
[    6.636539] [drm] RAM width 64bits DDR
[    6.636550] [drm] radeon: 256M of VRAM memory ready
[    6.636551] [drm] radeon: 512M of GTT memory ready.
[    6.636590] [drm] radeon: using MSI.
[    6.636618] [drm] radeon: irq initialized.
[    6.636620] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    6.636986] [drm] Loading RV710 Microcode
[    7.021799] [drm] ring test succeeded in 1 usecs
[    7.021857] [drm] radeon: ib pool ready.
[    7.021877] [drm] ib test succeeded in 0 usecs
[    7.023093] [drm] Radeon Display Connectors
[    7.023095] [drm] Connector 0:
[    7.023096] [drm]   VGA
[    7.023098] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    7.023099] [drm]   Encoders:
[    7.023100] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    7.023101] [drm] Connector 1:
[    7.023102] [drm]   HDMI-A
[    7.023103] [drm]   HPD1
[    7.023104] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    7.023105] [drm]   Encoders:
[    7.023106] [drm]     DFP1: INTERNAL_UNIPHY
[    7.023107] [drm] Connector 2:
[    7.023107] [drm]   DVI-I
[    7.023108] [drm]   HPD4
[    7.023109] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[    7.023110] [drm]   Encoders:
[    7.023111] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    7.023112] [drm]     DFP2: INTERNAL_UNIPHY2
[    7.161108] [drm] fb mappable at 0xD0141000
[    7.161110] [drm] vram apper at 0xD0000000
[    7.161111] [drm] size 8294400
[    7.161112] [drm] fb depth is 24
[    7.161113] [drm]    pitch is 7680
[    7.161412] fb2: radeondrmfb frame buffer device
[    7.161416] [drm] Initialized radeon 2.0.0 20080528 for 0000:02:00.0 on minor 1
[   11.172985] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[   12.528752] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
```Any clue? What could I try?
I'm using kernel version 2.6.32-24-generic.
Thanks

---

