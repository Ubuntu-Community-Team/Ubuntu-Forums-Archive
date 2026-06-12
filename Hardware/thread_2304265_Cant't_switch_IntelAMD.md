---
title: "Cant't switch Intel/AMD"
date: 2015-11-25
forum: Hardware
---

### Post by stanislav7 on 2015-11-25
Hi there!
I'm using a laptop HP Pavilion DV6 with hybrid graphics on it.
(ubuntu 14.04 lts, kernel 3.19, x86_64 architecture)
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] (rev ff)

```I'm using the open source drivers for my graphics.
```
cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0

```
```
echo ON > /sys/kernel/debug/vgaswitcheroo/switch

```Returning me the same:
```
cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0

```Looks like I can't put the power on discrenete card. But after
```
echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch

```and restarting X I've got a black screen. (i can write my pass and start the session complitely blind) So it change the card, but without power on it.
I'm not sure that vgaswitcheroo should work with 14.04, but looks like DRI_PRIME=1 work only with glxgears:
```
glxgears
308 frames in 5.0 seconds = 61.527 FPS
DRI_PRIME=1 glxgears
22939 frames in 5.0 seconds = 4587.401 FPS


```
But 
```
glxinfo | grep "OpenGL renderer"
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
**DRI_PRIME=1 **glxinfo | grep "OpenGL renderer"
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 

```
I need to use the discrete card on some apps, wine, playonlinux etc...
Any ideas how to change the cards on open source drivers?
--------------------------------
Tried to add DRI_PRIME=1 to glxheads. So Within I've got just rotating (very fast) triangle...
```
glxheads
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0xcda010
  Window:      0x4800002
  Context:     0xce8fa0
  GL_VERSION:  3.0 Mesa 10.5.9
  GL_VENDOR:   Intel Open Source Technology Center
  GL_RENDERER: Mesa DRI Intel(R) Sandybridge Mobile 
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 4913 requests (4913 known processed) with 0 events remaining.

```
```

DRI_PRIME=1 glxheads 
glxheads: exercise multiple GLX connections (any key = exit)
Usage:
  glxheads xdisplayname ...
Example:
  glxheads :0 mars:0 venus:1
Name: :0
  Display:     0x1ddf010
  Window:      0x4800002
  Context:     0x1dedfa0
  GL_VERSION:  3.0 Mesa 10.5.9
  GL_VENDOR:   Intel Open Source Technology Center
  GL_RENDERER: Mesa DRI Intel(R) Sandybridge Mobile 

```

---

### Post by stanislav7 on 2015-12-07
Ok, so I've change the GRUB. At [COLOR=#000000][FONT=Ubuntu Beta]/etc/default/grub I've added at the [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Beta]GRUB_CMDLINE_LINUX_DEFAULT I put -  [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Beta]radeon.runpm=0. So now I've got at cat /sys/kernel/debug/vgaswitcheroo/switch  both cards witch "PWR". But when I trying to change the card witch echo - still the black screen... 
Another problem is with the drivers. I complitely removed intel and radeon drivers. After the Unity start's working without some stuff like transparent etc. So I've installed the xserver-xorg-video-ati - nothing... xserver-xorg-video-radeon - nothing... xserver-xorg-video-intel - Unity start normally working, so look's like the driver radeon is not installed... At the Xorg log file - nothing about radeon driver. At the drivers config folder the same - I have intel driver config file, but radeon is missing... 
Somebody have ideas how to fix it?[/FONT][/COLOR]

---

### Post by stanislav7 on 2015-12-08
Ok, so I've found the problem. I forgot that I've change the config file of intel driver, cause my brightness hotkeys didn't work. So now I just removed from 20-intel.conf 2 lines:
```
Driver      "intel"
BusID       "PCI:0:2:0"
```
Reboot - and now Xorg see the radeon driver, Xrandr list me 3 providers (2 of them is radeon;) ) and DRI_PRIME=1 is working!!

---

