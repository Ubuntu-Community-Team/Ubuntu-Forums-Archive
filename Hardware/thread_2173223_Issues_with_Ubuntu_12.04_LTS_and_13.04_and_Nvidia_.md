---
title: "Issues with Ubuntu 12.04 LTS and 13.04 and Nvidia GTS 450"
date: 2013-09-08
forum: Hardware
---

### Post by Silviu_Caragea on 2013-09-08
Hello, 

I receintly done some updates on my Ubuntu 12.04 instalation and now I cannot use a resolution bigger than 1360 x 768. I tried to reinstall Ubuntu again and I have the same problem. Also on 13.04 or Cent OS I have similar issues. 

Something happened because I used Ubuntu 12.04 without any issues on this hardware configuration with 3 months ago. 

I also tried to add a new resolution with xrandr but is failing. Also I tried to pick another driver but the problem was not solved. 

Any suggestions ?

---

### Post by papibe on 2013-09-08
Hi Silviu_Caragea. Welcome to the forum ):P

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

xrandr

xvidtune -show

lsmod | grep -iE 'nvidia|nouveau'
```
Regards.

---

### Post by Silviu_Caragea on 2013-09-08
**lspci -nnk | grep -iA2 vga**

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF106 [GeForce GTS 450] [10de:0dc4] (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:3503]
    Kernel driver in use: nvidia

**xrandr**

Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
DVI-I-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   512x384       120.0  
   400x300       144.4  
   320x240       120.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)

**xvidtune -show**

"1360x768"     72.00   1360 1408 1440 1520    768  771  781  790 +hsync -vsync

**lsmod | grep -iE 'nvidia|nouveau'**

nvidia               9425761  38

---

### Post by Silviu_Caragea on 2013-09-08
In the past I could use without any issue 1920x1080 (the same resolution that I'm using it on Windows 7).

---

### Post by papibe on 2013-09-08
Thanks.

Let's see what version of the driver is installed, and what meta modes you have available. Could you post the result of these commands?
```
dpkg -l | grep nvidia

nvidia-settings --version

xrandr -q --q1
```
Regards.

---

### Post by Silviu_Caragea on 2013-09-09
> **papibe said:**
> Thanks.

Let's see what version of the driver is installed, and what meta modes you have available. Could you post the result of these commands?
```
dpkg -l | grep nvidia

nvidia-settings --version

xrandr -q --q1
```
Regards.

**dpkg -l | grep nvidia**

ii  nvidia-304              304.88-0ubuntu0.0.3      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-319              319.32-0ubuntu0.0.1      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-319-updates      319.32-0ubuntu0.0.1      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common           1:0.2.44.2               Find obsolete NVIDIA drivers
ii  nvidia-settings-304     304.88-0ubuntu0.0.3      Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-319     319.32-0ubuntu0.0.1      Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-319-updates 319.32-0ubuntu0.0.1      Tool for configuring the NVIDIA graphics driver

**nvidia-settings --version**

nvidia-settings:  version 304.88  (buildd@roseapple)  Fri Aug  9 00:37:47 UTC 2013
  The NVIDIA X Server Settings tool.

  This program is used to configure the NVIDIA Linux graphics driver.
  For more detail, please see the nvidia-settings(1) man page.

  Copyright (C) 2004 - 2010 NVIDIA Corporation.

**xrandr -q --q1**

 SZ:    Pixels          Physical       Refresh
*0   1360 x 768    ( 460mm x 260mm )  *50   52  
 1   1024 x 768    ( 346mm x 260mm )   51  
 2   1152 x 864    ( 390mm x 292mm )   53  
 3    800 x 600    ( 270mm x 203mm )   54   55   56  
 4    680 x 384    ( 230mm x 130mm )   57   58  
 5    640 x 480    ( 216mm x 162mm )   59  
 6    512 x 384    ( 173mm x 130mm )   60  
 7    400 x 300    ( 135mm x 101mm )   61  
 8    320 x 240    ( 108mm x  81mm )   62  
 9   1024 x 576    ( 346mm x 195mm )   63  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis

---

### Post by papibe on 2013-09-20
Thanks.

I see that the driver doesn't read higher resolution than 1360x768. If you are sure that your monitor supports higher resolutions, this is what I recommend:

[LIST=1]
[*]**Clean the house:**


[LIST]
[*][*]There are 2 drivers installed (from dpkg), so I would uninstall them both and make a clean install again. To do that close all your graphic applications and press Ctrl+Alt+F1 to go to text mode. Login in there and purge all Nvidia packages except nvdia-common:
```
sudo apt-get purge nvidia-304
sudo apt-get purge nvidia-319
sudo apt-get purge nvidia-319-updates
sudo apt-get purge nvidia-settings-304
sudo apt-get purge nvidia-settings-319
sudo apt-get purge nvidia-settings-319-updates
```
[*][*]Then reconfigure nvidia-common:
```
sudo dpkg-reconfigure nvidia-common 
```
[*][*]Now restart your machine:
```
sudo reboot
```
[/LIST]
[*]**Install the current driver.**


[LIST]
[*][*]Go to text mode again:
```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```
[*][*]Restart again:
```
sudo reboot
```
[*][*]That should do it.


[/LIST]
[*]**Upgrade your driver if necessary.**


[LIST]
[*][*]If you are still experiencing problems, you may try an upstream driver. First upgrade to the swat's ppa:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
sudo nvidia-xconfig
```
[*][*]Reboot again.


[*][*]Then if that doesn't work either, there's another ppa with bleeding-edge versions:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo nvidia-xconfig
```
[*][*]Restart again.
[/LIST]
[/LIST]

I hope that helps, and tell us how it goes.
Regards.

---

### Post by Silviu_Caragea on 2013-09-21
Hello,

I have updated the Ubuntu before doing what you told me and after the update (wasn't updated since 1 week ago) guess what ?
Is working :) and is detecing my monitor corectly . In the past was Unknown now I can se Samsung :)

Anyway thanks a lot for your support !!
I really appreciate !

Kind regards,
Silviu

---

