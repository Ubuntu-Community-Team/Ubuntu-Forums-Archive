---
title: "Random annoying glitch using Samsung C34J791 display"
date: 2021-09-05
forum: Hardware
---

### Post by daniel-diaz-quintero on 2021-09-05
[FONT=arial]Hello,

I would like your help with this issue i'm not able to solve. After replace my old screens by a new one (Samsung C34J791) display started to glitch randomly. Under Win10 works fine and I tried several changes as I have read in other posts but it's still present. 

Additional info:[/FONT]

[FONT=monospace][COLOR=#5454ff]**/etc/X11**[/COLOR][COLOR=#000000]$ xrandr -q [/COLOR]
Screen 0: minimum 320 x 200, current 3440 x 1440, maximum 16384 x 16384 
DisplayPort-0 disconnected (normal left inverted right x axis y axis) 
HDMI-0 connected primary 3440x1440+0+0 (normal left inverted right x axis y axis) 797mm x 333mm 
   3440x1440     59.97*+  49.99   
   2560x1440     59.95   
   2560x1080     60.00    59.94   
   1920x1080     60.00    50.00    59.94   
   1680x1050     59.88   
   1600x900      60.00   
   1280x1024     75.02    60.02   
   1440x900      59.90   
   1280x800      59.91   
   1152x864      75.00   
   1280x720      60.00    50.00    59.94   
   1024x768      75.03    70.07    60.00   
   832x624       74.55   
   800x600       72.19    75.00    60.32    56.25   
   720x576       50.00   
   720x480       60.00    59.94   
   640x480       75.00    72.81    66.67    60.00    59.94   
   720x400       70.08   
DVI-0 disconnected (normal left inverted right x axis y axis) 
DVI-1 disconnected (normal left inverted right x axis y axis)
[FONT=monospace]
[COLOR=#5454ff]**/etc/X11**[/COLOR][COLOR=#000000]$ inxi -G        [/COLOR]
[COLOR=#5454ff]**Graphics:  Device-1:**[/COLOR][COLOR=#000000] Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] radeon [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
           [COLOR=#5454ff]**Display:**[/COLOR][COLOR=#000000] x11 [/COLOR][COLOR=#5454ff]**server:**[/COLOR][COLOR=#000000] X.Org 1.20.11 [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] ati,fbdev [/COLOR][COLOR=#5454ff]**unloaded:**[/COLOR][COLOR=#000000] modesetting,radeon,vesa [/COLOR][COLOR=#5454ff]**resolution:**[/COLOR][COLOR=#000000] 3440x1440~60Hz  [/COLOR]
           [COLOR=#5454ff]**OpenGL:**[/COLOR][COLOR=#5454ff]**renderer:**[/COLOR][COLOR=#000000] AMD TAHITI (DRM 2.50.0 5.11.0-27-generic LLVM 12.0.0) [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 4.5 Mesa 21.0.3  [/COLOR]
[COLOR=#5454ff][B]
/etc/X11[/B][/COLOR][COLOR=#000000]$ sudo lshw -class display [/COLOR]
 *-display                  
       descripción: VGA compatible controller 
       producto: Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] 
       fabricante: Advanced Micro Devices, Inc. [AMD/ATI] 
       id físico: 0 
       información del bus: pci@0000:01:00.0 
       versión: 00 
       anchura: 64 bits 
       reloj: 33MHz 
       capacidades: pm pciexpress msi vga_controller bus_master cap_list rom 
       configuración: driver=radeon latency=0 
       recursos: irq:31 memoria:e0000000-efffffff memoria:f7e00000-f7e3ffff ioport:e000(size=256) memoria:c0000-dffff 

[/FONT][FONT=arial]Glitch example:[/FONT] [https://drive.google.com/file/d/1477EVXVD4uuekmHv0ST9R1B9Xmud29TH/view?usp=sharing](https://drive.google.com/file/d/1477EVXVD4uuekmHv0ST9R1B9Xmud29TH/view?usp=sharing)

[FONT=arial]Any suggestions are welcome[/FONT].

Thanks!

[/FONT]

---

### Post by daniel-diaz-quintero on 2021-10-16
Any idea?

---

