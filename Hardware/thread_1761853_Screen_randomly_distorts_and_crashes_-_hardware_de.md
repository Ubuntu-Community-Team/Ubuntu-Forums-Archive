---
title: "Screen randomly distorts and crashes - hardware defect?"
date: 2011-05-18
forum: Hardware
---

### Post by vinx on 2011-05-18
At random moments my laptop locks up completely. I assumed it was a heating problem, so I replaced the thermal compound thoroughly and checked the temperature which did not increase on the moment of bad behaviour (unresponsive system, screen flashes a few times with 5 second interval, screen starts to corrupt, reboot only solution).
[IMG]http://vincent.hindriksen.nl/files/GPU-crash.jpg[/IMG]

The moment the system starts getting unresponsive, this is in my syslog:
```
May 18 20:01:35 truus-laptop kernel: [ 4101.349479] NVRM: Xid (0000:01:00): 13, 0004 00000000 00008297 00001458 00000006 00000140
May 18 20:01:35 truus-laptop kernel: [ 4101.493755] NVRM: Xid (0000:01:00): 13, 0004 00000000 00008297 000015e0 00000000 00000040
```

I upgraded tot 11.04 and again to the latest NVIDIA-drivers, which I think is the problem. My video is an on-board NVIDIA 320M.

Does anybody have a clue?

---

### Post by mpaget on 2011-06-14
same issue

dmesg
```
[ 1849.203009] NVRM: Xid (0000:01:00): 13, 0003 00000000 00008297 00001640 00000000 00000040
[ 1857.375281] NVRM: Xid (0000:01:00): 13, 0003 00000000 00008297 00001458 00000006 00000140
[ 1865.492474] NVRM: Xid (0000:01:00): 13, 0003 00000000 00008297 00001458 00000006 00000140
[ 1873.614229] NVRM: Xid (0000:01:00): 13, 0003 00000000 00008297 00001458 00000006 00000140
[ 1881.724492] NVRM: Xid (0000:01:00): 13, 0003 00000000 00008297 00001458 00000006 00000140
```

lspci -v
```

01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300 GE] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: nVidia Corporation Device 060c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at dc80 [size=128]
	[virtual] Expansion ROM at fde00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

```

I have had the pixel screen ( kinda fun for about a minute then annoying ) reboot fixes it.
now when changing workspaces the UI is unresponsive, but ctrl-alt-f1 does still work to get to a terminal.  sometimes if compiz is 99% on a cpu I can kill it and get back to the desktop, but most of the time a reboot is needed.

~/.nvidia-settings-rc
```
#
# /home/mpaget/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Fri May 13 09:56:04 2011
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = No
Timer = Graphics_Card_(GPU_0),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000

# Attributes:

0/CursorShadow=0
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/SyncToVBlank=0
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/AllowFlipping=1
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=0
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/DigitalVibrance[DFP-0]=0
0/DigitalVibrance[DFP-1]=0
0/GPUScaling[DFP-0]=131073
0/GPUScaling[DFP-1]=131073
0/OverscanCompensation[DFP-0]=0
0/OverscanCompensation[DFP-1]=0
0/ColorSpace[DFP-0]=0
0/ColorSpace[DFP-1]=0
0/ColorRange[DFP-0]=0
0/ColorRange[DFP-1]=0
0/XVideoTextureBrightness=0
0/XVideoTextureContrast=0
0/XVideoTextureHue=180
0/XVideoTextureSaturation=0
0/XVideoTextureSyncToVBlank=1
0/XVideoSyncToDisplay=65536

```

using NVIDIA GLX Module  270.41.06

---

