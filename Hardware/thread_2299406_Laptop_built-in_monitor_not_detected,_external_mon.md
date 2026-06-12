---
title: "Laptop built-in monitor not detected, external monitor working fine. Dual GPU."
date: 2015-10-18
forum: Hardware
---

### Post by seppukusayonara on 2015-10-18
Hi everyone. The built-in monitor of my laptop seems to be not recognized by  Ubuntu. The screen is black though illuminated (and the illumination can be adjusted with function keys). External monitor  connected through HDMI works just fine. Doesn't matter if plugged in  during bootup.
  
My laptop is Samsung 670Z5E (AMD HD8850M + integrated Intel GPU). It  runs Ubuntu 14.04 installed alongside Windows 8.1.  Immediately after Ubuntu installation it was using Intel driver only. I've installed  proprietary driver (fglrx) and Catalyst Control Center from AMD website in order to use switchable graphics but it's  made no difference. Previously I was tinkering with packages from "Additional Drivers" which left me reinstalling the whole system.

Also, setting GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to "quiet splash nomodeset" makes the built-in screen operable after boot-up but then I am unable to log in with Unity. Setting it to "quiet splash fglrx.modeset=1" on the other hand seems to have no effect.

I would be grateful for any help.

I'm new to Linux and Ubuntu so my knowledge is very limited. Anyway, here are some details:

lshw -c display
  ```
  *-display               
       description: Display controller
       product: Venus XT [Radeon HD 8870M / R9 M270X/M370X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:50 memory:e0000000-efffffff memory:f7d00000-f7d3ffff ioport:e000(size=256) memory:f7d40000-f7d5ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64)

```xrandr -q:
  ```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     72.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)

```

xorg.conf
 ```
Section "ServerLayout"
    Identifier "amd-layout"
    Screen 0 "amd-screen" 0 0
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    Option "AccelMethod" "uxa"
    BusID "PCI:0@0:2:0"
EndSection

Section "Device"
    Identifier "amd-device"
    Driver "fglrx"
    BusID "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier "amd-monitor"
    Option "VendorName" "ATI Proprietary Driver"
    Option "ModelName" "Generic Autodetecting Monitor"
    Option "DPMS" "true"
EndSection

Section "Screen"
    Identifier "amd-screen"
    Device "amd-device"
    Monitor "amd-monitor"
    DefaultDepth 24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

lspci
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus XT [Radeon HD 8870M / R9 M270X/M370X]
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
```


fglrxinfo
```
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon R9 M200X Series 
OpenGL version string: 4.5.13399 Compatibility Profile Context 15.20.1013
```

lsmod | grep fglrx
```
fglrx               13510291  231 
amd_iommu_v2           18916  1 fglrx
```

---

### Post by TheFu on 2015-10-18
Cannot help much, but downloading drivers directly from any website is the last choice of desperation with Ubuntu. In order:
a) Use the pre-installed drivers
b) Use "get more drivers" offered thru the update manager (or something like that)
c) Use a reputable, maintained, PPA
d) Download a .DEB file, but understand the risks when you do this. It could lock other system libraries to the current level forever.
e) Get an install package from the vendor

The last option is what I think you've done.

---

### Post by seppukusayonara on 2015-10-24
So I decided to reinstall Ubuntu since I had problems purging fglrx and I noticed that the issue of built-in screen not working occurs from the very beginning i.e. from the point of starting the installation (and monitor connected through HDMI port works). My biggest concern is the lack of LVDS when using xrandr. How can this be?

Anyway, below I present how things look after fresh installation, so if anyone has some idea of what I could do to get laptop's screen detected please let me know.

Also, how likely it is that my hardware would work properly with Ubuntu 15.10 or Mint?

sudo lshw -c display
```

  *-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:32 memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64)

```

xrandr -q
```

Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     72.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```
(no LVDS and some weird looking VIRTUAL1)

lspci (relevant lines)
```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus XT [Radeon HD 8870M] (rev ff)

```

I wonder why it is using driver for HD 8870M when my discrete GPU is actually HD 8850m. I don't know whether such detail could affect its behaviour. "Additional Drivers" utility says it is open source X.Org X server driver for HD 8800M series.

No xorg.conf in /etc/X11/ this time.

---

### Post by TheFu on 2015-10-24
15.10  doesn't support the fglrx driver according to the release notes.

This is just one of the important reasons to always, always, always review the release notes *before* even bothering to downlaod the installation packages.

---

### Post by seppukusayonara on 2015-10-24
Yes, I am aware of fglrx not being supported in 15.10. As for now, I just want to get my laptop's screen operating, no matter the driver. I would like to know beforehand whether a newer version of Ubuntu or even Mint would detect the screen or if it is something distribution independent.

---

### Post by seppukusayonara on 2015-10-24
Success!
I switched from UEFI to UEFI/BIOS and the screen is working great! Also, LVDS is now being detected by xrandr.

Thank you, @TheFu, for your support anyway!

---

