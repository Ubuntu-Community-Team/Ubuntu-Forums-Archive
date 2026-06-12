---
title: "Ubuntu 20.04 LTS unable to detect second monitor"
date: 2021-04-12
forum: Hardware
---

### Post by lawrencekks88 on 2021-04-12
I have a desktop computer running on Ubuntu 20.04 LTS with the following hardware:
- 11th Gen Intel i5-11400
- H510I PRO WIFI MSI motherboard
- no graphics card


The motherboard has a DisplayPort and HDMI port. When I plug a monitor into either of the ports, the monitor works. However, when I plug my second monitor, only the monitor that is plugged into the HDMI port works.


Here is the output from `sudo lspci -v`:


    00:02.0 VGA compatible controller: Intel Corporation Device 4c8b (rev 04) (prog-if 00 [VGA controller])
    DeviceName: Onboard - Video
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7d16
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at a0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: [40] Vendor Specific Information: Len=0c <?>
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [ac] MSI: Enable- Count=1/1 Maskable+ 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [100] Process Address Space ID (PASID)
    Capabilities: [200] Address Translation Service (ATS)
    Capabilities: [300] Page Request Interface (PRI)


 
and from `sudo lshw -c video`:


    *-display UNCLAIMED       
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:a0000000-a0ffffff memory:90000000-9fffffff ioport:4000(size=64) memory:c0000-dffff


and from `xrandr --verbose`:


    xrandr: Failed to get size of gamma for output default
    Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
    default connected 1920x1080+0+0 (0x529) normal (normal) 0mm x 0mm
    Identifier: 0x528
    Timestamp:  943886
    Subpixel:   unknown
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    non-desktop: 0 
        supported: 0, 1
    1920x1080 (0x529) 159.667MHz *current
        h: width  1920 start    0 end    0 total 1920 skew    0 clock  83.16KHz
        v: height 1080 start    0 end    0 total 1080           clock  77.00Hz

and from `xrandr -q`:


    xrandr: Failed to get size of gamma for output default
    Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
    default connected primary 1920x1080+0+0 0mm x 0mm
    1920x1080     77.00* 


and from `inxi -G`:


    Graphics:  Device-1: Intel driver: N/A 
           Display: x11 server: X.Org 1.20.9 driver: fbdev unloaded: modesetting,vesa 
           resolution: 1920x1080~77Hz 
           OpenGL: renderer: llvmpipe (LLVM 11.0.0 256 bits) v: 4.5 Mesa 20.2.6 


I have tried the following:


- installing `mesa-utils`
- looking through various pages on the forums including [https://askubuntu.com/questions/1121132/hdmi-not-detected-on-ubuntu-18-04](https://askubuntu.com/questions/1121132/hdmi-not-detected-on-ubuntu-18-04) (but my problem appears to be different as I am not able to see "<display> disconnected" in my xrandr output)
- searching for the correct drivers on Intel and MSI website
- updating to the latest kernel (5.11.13)


It seems that my problem is due to a lack of the correct drivers for graphics? 
  
Pretty lost as I am fairly new to Linux and would greatly appreciate any help on what else I can do to troubleshoot this problem.

---

### Post by CelticWarrior on 2021-04-12
Welcome.

> [COLOR=#000000]It seems that my problem is due to a lack of the correct drivers for graphics?[/COLOR]


Yes, it is.

```
[COLOR=#000000]*-display UNCLAIMED[/COLOR]
```
Indicates just that, lack of drivers.
It should be running with Intel drivers that are opens source and installed automatically. Why they weren't in your case I'm not sure. It could be related to the lack of support for such new Intel, after all it's newer than the release you installed.

---

