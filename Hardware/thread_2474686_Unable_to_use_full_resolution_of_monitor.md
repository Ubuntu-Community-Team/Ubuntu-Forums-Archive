---
title: "Unable to use full resolution of monitor"
date: 2022-05-05
forum: Hardware
---

### Post by asb3 on 2022-05-05
I have an HP 32Q monitor, with maximum resolution 2560x1440.
My graphics card is an Intel Xeon E3-1200:
> lshw -numeric -C display
[FONT=monospace][COLOR=#000000]  *-display                  [/COLOR]
       description: VGA compatible controller 
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [8086:162] 
       vendor: Intel Corporation [8086] 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 09 
       width: 64 bits 
       clock: 33MHz 
       capabilities: msi pm vga_controller bus_master cap_list rom 
       configuration: driver=i915 latency=0 
       resources: irq:37 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory
:c0000-dffff

In the display settings, the maximum resolution is 1920x1080.
Is there any way to get the full resolution?
I can get full resolution when I attach the monitor to a windows laptop, which I used to get the modeline.
I tried using xrandr to add a mode:
>[/FONT][FONT=monospace][FONT=monospace][COLOR=#000000] xrandr --newmode "2560x1440" 241.500 2560 2608 2640 2720 1440 1443 1448 1481 +hsync -vsync 
[/COLOR][/FONT][/FONT]
[FONT=monospace][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]> xrandr --addmode HDMI-3 "2560x1440"
[/COLOR]
[/FONT][/COLOR][/FONT][/FONT]When I try to change the mode using the command
[FONT=monospace][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][COLOR=#000000]> xrandr --output HDMI-3 --mode "2560x1440"
[/COLOR] or selecting the new 2560x1440 option in settings, the resolution doesn't change, and I get the error message:
[/FONT][/FONT][/COLOR][/FONT][/FONT]
[FONT=monospace][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][FONT=monospace][COLOR=#000000]xrandr: Configure crtc 1 failed[/COLOR]

I've seen other threads with this problem, but no solution that works.
[/FONT][/FONT][/FONT][/COLOR][/FONT][/FONT]

---

### Post by TheFu on 2022-05-05
If the monitor connection isn't providing the correct EDID, then that is the root problem to be solved.  Once it is solved, then the available, correct, resolutions will be in the list and available.  There are some EDID tools available in Ubuntu packages. Install them. See what they show.

Also, if using Wayland, then xrandr won't work. You have to use Wayland resolution tools, whatever those are, not tools for X/Windows.

---

### Post by Yellow Pasque on 2022-05-06
[https://community.intel.com/t5/Graphics/Intel-HD-4000-HDMI-2560x1440-resolution/m-p/375085/highlight/true#M27171](https://community.intel.com/t5/Graphics/Intel-HD-4000-HDMI-2560x1440-resolution/m-p/375085/highlight/true#M27171)
The GPU may not be capable of 2560x1440 at 60Hz through HDMI. You might try a 30Hz modeline to see if that works.

---

### Post by asb3 on 2022-05-06
There are no 30Hz modelines.

---

### Post by asb3 on 2022-05-06
I installed and ran read-edid.  There are two modelines with 2560x1440 resolution:
[FONT=monospace][COLOR=#000000] Modeline        "Mode 0" 241.50 2560 2608 2640 2720 1440 1443 1448 1481 +hsync -vsync [/COLOR]
[/FONT][FONT=monospace][FONT=monospace][COLOR=#000000]Modeline        "Mode 12" 274.70 2560 2568 2600 2640 1440 1474 1482 1488 +hsync -vsync 

The first is the modeline I got from the windows machine.
I tried using xrandr to switch to both of them. Neither worked.

Strange result: the output off get_edid includes the line
[/COLOR][/FONT][/FONT]
[FONT=monospace][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]Option "PreferredMode" "Mode 10"

Mode 10 is 1920x1080:
[/COLOR][/FONT][/COLOR][/FONT][/FONT][FONT=monospace][FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][COLOR=#000000]Modeline        "Mode 10" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
[/COLOR]
When the monitor powers up, it displays a text box that includes the lines
Current mode 1920x1080
Optimal mode 256x1440


[/FONT] 
[/FONT][/COLOR]


[/FONT][/FONT]

---

### Post by TheFu on 2022-05-06
Have you tried creating a valid xorg.conf file with the information?  I'm on a different release and using X/Windows, but the location for those files are: /etc/X11/xorg.conf.d/

If you use an nvidia GPU, there's a program with the proprietary drivers that creates the file. **nvidia-xconfig**.  Use that to save the file to your $HOME first, then copy it to the directory above and modify as needed.

---

### Post by Yellow Pasque on 2022-05-06
> **asb3 said:**
> There are no 30Hz modelines.
Try making one (and using --newmode and --addmode as you did in the first thread):
```
cvt 2560 1440 30
```

---

