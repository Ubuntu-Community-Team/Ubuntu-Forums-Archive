---
title: "How to enable HDMI output with the new X.org?"
date: 2011-03-04
forum: Hardware
---

### Post by Hyvok on 2011-03-04
So I have a HP Pavilion Dv7 laptop with an Ati Radon 4200 (I think) GPU and I'd want to enable the HDMI output to use with my fullhd television. I'm using ubuntu 10.10 so the X.org defaults to kernel modesetting and I cannot find any solid information on what I need to do to enable the HDMI output.

If I attach the television to the laptop there is no signs of life on the television at any point. I've tried the radeon and the proprietary fglrx drivers to no avail. One thing I'm not 100% sure of is the function button on the laptop that apparently toggles the external display, not sure if its just a software shortcut or if it does something hardware wise... Here is my lspci output related to the GPU:

```
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]

```

Here is my "dmesg|grep drm" output:

```
[    1.286112] [drm] Initialized drm 1.1.0 20060810
[    2.313179] [drm] radeon defaulting to kernel modesetting.
[    2.313183] [drm] radeon kernel modesetting enabled.
[    2.322228] [drm] initializing kernel modesetting (RS880 0x1002:0x9712).
[    2.322349] [drm] register mmio base: 0xF0400000
[    2.322351] [drm] register mmio size: 65536
[    2.323073] [drm] Clocks initialized !
[    2.323308] [drm] Detected VRAM RAM=336M, BAR=256M
[    2.323313] [drm] RAM width 32bits DDR
[    2.323405] [drm] radeon: 336M of VRAM memory ready
[    2.323406] [drm] radeon: 512M of GTT memory ready.
[    2.323441] [drm] radeon: irq initialized.
[    2.323444] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    2.324657] [drm] Loading RS780 Microcode
[    2.365013] [drm] ring test succeeded in 1 usecs
[    2.365134] [drm] radeon: ib pool ready.
[    2.365196] [drm] ib test succeeded in 0 usecs
[    2.365198] [drm] Enabling audio support
[    2.365408] [drm] Unknown TV standard; defaulting to NTSC
[    2.365513] [drm] Radeon Display Connectors
[    2.365515] [drm] Connector 0:
[    2.365516] [drm]   VGA
[    2.365519] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    2.365520] [drm]   Encoders:
[    2.365522] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.365523] [drm] Connector 1:
[    2.365524] [drm]   LVDS
[    2.365526] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    2.365528] [drm]   Encoders:
[    2.365529] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[    2.421391] [drm] radeon: power management initialized
[    2.512186] [drm] fb mappable at 0xD0141000
[    2.512190] [drm] vram apper at 0xD0000000
[    2.512191] [drm] size 5763072
[    2.512193] [drm] fb depth is 24
[    2.512194] [drm]    pitch is 6400
[    3.519753] fb0: radeondrmfb frame buffer device
[    3.519755] drm: registered panic notifier
[    3.519901] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[    3.521992] [drm] initializing kernel modesetting (CEDAR 0x1002:0x68E0).
[    3.522114] [drm] register mmio base: 0xF0200000
[    3.522116] [drm] register mmio size: 131072
[    3.657999] [drm] Clocks initialized !
[    3.658183] [drm] Detected VRAM RAM=512M, BAR=256M
[    3.658187] [drm] RAM width 64bits DDR
[    3.658201] [drm] radeon: 256M of VRAM memory ready
[    3.658204] [drm] radeon: 512M of GTT memory ready.
[    3.658297] [drm] radeon: irq initialized.
[    3.658300] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    3.659348] [drm] Loading CEDAR Microcode
[    3.681977] [drm] ring test succeeded in 1 usecs
[    3.682097] [drm] radeon: ib pool ready.
[    3.682123] [drm] ib test succeeded in 0 usecs
[    3.682467] [drm] Radeon Display Connectors
[    3.682469] [drm] Connector 0:
[    3.682470] [drm]   LVDS
[    3.682473] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[    3.682474] [drm]   Encoders:
[    3.682475] [drm]     LCD1: INTERNAL_UNIPHY
[    3.682477] [drm] Connector 1:
[    3.682478] [drm]   HDMI-A
[    3.682479] [drm]   HPD1
[    3.682481] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    3.682482] [drm]   Encoders:
[    3.682484] [drm]     DFP1: INTERNAL_UNIPHY1
[    3.682485] [drm] Connector 2:
[    3.682486] [drm]   VGA
[    3.682487] [drm]   DDC: no ddc bus - possible BIOS bug - please report to xorg-driver-ati@lists.x.org
[    3.682489] [drm]   Encoders:
[    3.682490] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    3.686635] [drm] Internal thermal controller without fan control
[    3.686645] [drm] radeon: power management initialized
[    3.703248] [drm] fb mappable at 0xE0140000
[    3.703251] [drm] vram apper at 0xE0000000
[    3.703252] [drm] size 5763072
[    3.703254] [drm] fb depth is 24
[    3.703255] [drm]    pitch is 6400
[    3.703336] fb1: radeondrmfb frame buffer device
[    3.703343] [drm] Initialized radeon 2.5.0 20080528 for 0000:02:00.0 on minor 1

```

What do I need to do with the new KMS-enabled X.org to enable the HDMI output?

---

### Post by Hyvok on 2011-03-11
So this is impossible?

---

### Post by grahammechanical on 2011-03-11
I do not know for certain but I think that button on the keyboard that you mention is a hardware switch. I have a desktop machine and I am connected to my TV/monitor by DVI. I could use HDMI as my graphic adapter has a HDMI output but I would not need to activate anything in software. Oh, by the way, I do need to have the TV/monitor switched from TV/DVT to DVI as the source of the image. I do that through the remote control and there are buttons on the monitor.

Regards.

---

### Post by Hyvok on 2011-03-11
> **grahammechanical said:**
> I do not know for certain but I think that button on the keyboard that you mention is a hardware switch. I have a desktop machine and I am connected to my TV/monitor by DVI. I could use HDMI as my graphic adapter has a HDMI output but I would not need to activate anything in software.

Regards.

The keyboard button is behind a function "fn" + f5 button, but the combination does not seem to do anything. I wonder how I can enable the function button...?

---

### Post by dannet on 2013-01-22
Hi Hyvok, have you had success trying to run HDMI?

I have exactly the same graphics hardware on a HP DV7 and it seems to be impossible. I've tried with the open source drivers, disper, etc, with no results.

Regards,
Daniel

---

