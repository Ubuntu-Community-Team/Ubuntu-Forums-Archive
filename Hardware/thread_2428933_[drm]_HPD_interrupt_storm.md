---
title: "[drm] HPD interrupt storm"
date: 2019-10-11
forum: Hardware
---

### Post by ubumonk on 2019-10-11
hello

I have problems with a new monitor and HDMI connection to the laptop, when I connect the external monitor AOC 22BH1 21.5" no signal, can be a problem with HD intel graphics :(
[B]
Hardware [/B]> Lenovo Laptop V110 15,4"

**External monito**r > AOC 22BH1 21.5"

**OS **> Xubuntu 16.04

**kernel version **> 4.15.0-65-generic

**kernel.log** >
drm] HPD interrupt storm detected on connector HDMI-A-1: switching from hotplug detection to polling

**glxinfo | grep "OpenGL version**" >
OpenGL version string: 3.0 Mesa 18.0.5

**lspci |grep VGA** >
VGA compatible controller: Intel Corporation HD Graphics 520 (rev 0a)

I have installed the latest intel drivers via > intel-graphics-update-tool_2.0.2_amd64.deb, intel you have abandoned them long ago

Any solution?

Thank you!

---

### Post by ubumonk on 2019-10-11
add info **xrandr** >

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
eDP-1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.02*+
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
HDMI-1 disconnected (normal left inverted right x axis y axis)

---

### Post by ubumonk on 2019-10-24
Upgraded Xenial to Bionic, installed the latest kernel 5.3.6.....not working

Today install the latest open graphics drivers for Bionic without success, probably another person can be useful

[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=xenial](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers?field.series_filter=xenial)

---

### Post by ubumonk on 2019-12-25
Tested with many distros, all with the same error, currently use Disco Dingo to try to solve the error, probably HDMI hardware port error

---

