---
title: "Cannot set 1280x1024 resolution on Nvidia card"
date: 2014-08-03
forum: Hardware
---

### Post by tuxmartin on 2014-08-03
Hi,
I have Nvidia 8500 GT card and Xubuntu 14.04.1 64bit:
```
$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8500 GT] (rev a1)

$ lsmod | grep nvidia
nvidia              10675249  40 
drm                   303102  3 nvidia

$ dpkg -l | grep nvidia
ii  nvidia-331                                  331.38-0ubuntu7                       amd64        NVIDIA binary driver - version 331.38
ii  nvidia-libopencl1-331                       331.38-0ubuntu7                       amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                       331.38-0ubuntu7                       amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.6.2                                 amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             331.20-0ubuntu8                       amd64        Tool for configuring the NVIDIA graphics driver
martin@martin:~$ 

```

I can't set 1280x1024 resolution. Monitor is Acer AL1715. On PC is dual-boot with WIndows 8.1. Win8 use 1280x1024 good.

In xrandr and gui tool I can't see 1280x1024:
```
$ xrandr 
Screen 0: minimum 8 x 8, current 1152 x 864, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0     59.8  
   1152x864       60.0* 
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
```

I try add resolution manually, but it fails:
```
$ cvt  1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

$ xrandr --addmode VGA-0 1280x1024_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30

$ xrandr 
Screen 0: minimum 8 x 8, current 1152 x 864, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0     59.8  
   1152x864       60.0* 
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0x27a)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
```

Mainboard is [Gigabyte GA-G31M-ES2L]("http://www.gigabyte.com/products/product-page.aspx?pid=3485#ov") with integrated Intel VGA. But I have monitor in Nvidia card.

Can you please help me?

---

