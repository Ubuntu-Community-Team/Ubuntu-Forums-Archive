---
title: "HDMI issue with ATI Radeon HD5650 Acer 3820tg"
date: 2012-10-12
forum: Hardware
---

### Post by ninetentwelve on 2012-10-12
This is my first post, so I'm not sure if I posted to the right section.

I am having problems getting the HDMI to work on my laptop running 12.04 LTS.
[U]
Background[/U]
I got it to work for a while using the opensource radeon drivers. But seeing the the temperature was running at 80++ degrees, I decided to install fglrx drivers to see if it improved. However after I installed fglrx, it stopped working. So, I uninstall the fglrx drivers and now I'm stuck with the HDMI not working.

I've tested VGA on both drivers and it seems to work fine.

There is hybrid graphics on this laptop. I'm using vgaswitcheroo and it seems to be the same configuration before and now. i.e Discrete graphics with Integrated disabled.

Below are some output I've obtained from my computer.

sudo lshw -c video
```
  *-display               
       description: VGA compatible controller
       product: Madison [Radeon HD 5000M Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:47 memory:b0000000-bfffffff memory:afee0000-afefffff ioport:2000(size=256) memory:afe00000-afe1ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8)

```xrandr
```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS-1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1366x768       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-1 disconnected (normal left inverted right x axis y axis)

```dmesg | egrep -i "radeon|hdmi|vga"
```
[    0.718351] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.718361] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
[    0.718366] vgaarb: loaded
[    0.718368] vgaarb: bridge control possible 0000:02:00.0
[    0.718370] vgaarb: no bridge control possible 0000:00:02.0
[   21.139319] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   21.139322] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:02:00.0
[   22.301006] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   22.301200] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:02:00.1/sound/card1/input11
[   23.022036] [drm] radeon defaulting to kernel modesetting.
[   23.022039] [drm] radeon kernel modesetting enabled.
[   23.022060] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[   23.022107] radeon 0000:02:00.0: enabling device (0104 -> 0107)
[   23.022115] radeon 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.022119] radeon 0000:02:00.0: setting latency timer to 64
[   23.022331] vga_switcheroo: enabled
[   23.022393] radeon atpx: version is 1
[   23.750487] radeon 0000:02:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   23.750489] radeon 0000:02:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[   23.751981] [drm] radeon: 1024M of VRAM memory ready
[   23.751983] [drm] radeon: 512M of GTT memory ready.
[   23.752042] radeon 0000:02:00.0: irq 47 for MSI/MSI-X
[   23.752047] radeon 0000:02:00.0: radeon: using MSI.
[   23.752086] [drm] radeon: irq initialized.
[   23.787130] radeon 0000:02:00.0: WB enabled
[   23.803651] [drm] radeon: ib pool ready.
[   23.804207] [drm] Radeon Display Connectors
[   23.804219] [drm]   HDMI-A
[   23.804227] [drm]   VGA
[   23.804317] [drm] radeon: power management initialized
[   24.104997] fb1: radeondrmfb frame buffer device
[   24.105007] [drm] Initialized radeon 2.12.0 20080528 for 0000:02:00.0 on minor 1
[   24.106205] radeon: switched off
[   24.777914] radeon: switched on
[   24.793696] radeon 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[   24.793711] radeon 0000:02:00.0: restoring config space at offset 0x8 (was 0x1, writing 0x2001)
[   24.793718] radeon 0000:02:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xafee0004)
[   24.793726] radeon 0000:02:00.0: restoring config space at offset 0x4 (was 0xc, writing 0xb000000c)
[   24.793732] radeon 0000:02:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[   24.793739] radeon 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[   24.793776] radeon 0000:02:00.0: setting latency timer to 64
[   24.816475] radeon 0000:02:00.0: WB enabled

```_Specifications_
Acer Aspire 3820tg
Ubuntu 12.04 LTS
ATI Radeon 5650

---

### Post by ninetentwelve on 2012-10-15
bump.
anyone have ideas? any input would be greatly appreciated =)

---

