---
title: "second monitor via Displat Port not detected. new install of 22 with KDE"
date: 2024-03-22
forum: Hardware
---

### Post by Hachi-Roku on 2024-03-22
Hey peeps!

Running ubuntu studio 22 with KDE plasma. Got a second montior connected via a display port. Adapter cable to HDMI into the monitor.
Monitor works with the same HDMI cable on my other laptop running US 16.04 via hdmi.

Monitor is not detected at all. Not in the display settings gui, and terminal commands tell me Display port is empty (but it's plugged in and cable connections seem good)

Hunted for solutions but most seem to be for NVIDIA setups, which mine isn't.

I've disabled secure boot. No change.

Any ideas very much appreciated!!

(also interesting the system dump lists 2 DP's and 2 HDMI's, when physically there is only one DP.)

```

System:
  Kernel: 6.5.0-26-lowlatency x86_64 bits: 64 compiler: N/A
    Desktop: KDE Plasma 5.24.7 tk: Qt 5.15.3 wm: kwin_x11 vt: 1 dm: SDDM
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: HP product: HP EliteBook 840 G3 v: N/A
    serial: <superuser required> Chassis: type: 10 serial: <superuser required>
  Mobo: HP model: 8079 v: KBC Version 85.79 serial: <superuser required>
    UEFI: HP v: N75 Ver. 01.57 date: 07/28/2022

Graphics:
  Device-1: Intel Skylake GT2 [HD Graphics 520]
    vendor: Hewlett-Packard EliteBook 840 G3 driver: i915 v: kernel ports:
    active: eDP-1 empty: DP-1, DP-2, HDMI-A-1, HDMI-A-2 bus-ID: 00:02.0
    chip-ID: 8086:1916 class-ID: 0300
  Device-2: Chicony HP HD Camera type: USB driver: uvcvideo bus-ID: 1-9:5
    chip-ID: 04f2:b51c class-ID: 0e02
  Display: x11 server: X.Org v: 1.21.1.4 compositor: kwin_x11 driver: X:
    loaded: modesetting unloaded: fbdev,vesa gpu: i915 display-ID: :0
    screens: 1
  Screen-1: 0 s-res: 1366x768 s-dpi: 96 s-size: 361x203mm (14.2x8.0")
    s-diag: 414mm (16.3")
  Monitor-1: eDP-1 model: BOE Display res: 1366x768 hz: 60 dpi: 112
    size: 309x173mm (12.2x6.8") diag: 354mm (13.9") modes: 1366x768
  OpenGL: renderer: Mesa Intel HD Graphics 520 (SKL GT2)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2 direct render: Yes


*-display
       description: VGA compatible controller
       product: Skylake GT2 [HD Graphics 520]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1366,768
       resources: irq:126 memory:e0000000-e0ffffff memory:d0000000-dfffffff ioport:3000(size=64) memory:c0000-dffff

```

---

