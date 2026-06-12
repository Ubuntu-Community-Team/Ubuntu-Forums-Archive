---
title: "Unable to configure Ubuntu 12.04 to use external monitor at 2560x1600 resolution"
date: 2014-08-07
forum: Hardware
---

### Post by adrian35 on 2014-08-07
Hi all,

My configuration: Ubuntu 12.04 running on Lenovo T430 with Intel video. I have installed the latest version of the bios (2.64, 2014-04-15). I'm also running the latest stable Linux kernel (3.16).

I'm trying to set it up to use an external monitor Dell 3007WFP at 2560x1600 resolution. The laptop video output port is of type "mini displayport", and the monitor connects using Dual Link DVI. I have an adapter Mini DisplayPort -> Dual Link DVI (at least it was advertised as Dual Link DVI) that connects the two. (BTW, is there a way to test that the connector is indeed Dual Link DVI and not just single DVI?).

This exact same configuration was working about a year ago - somebody in IT managed to get it to work, with some difficulty using xrandr.

In the meantime I had to switch to another lower res monitor, but now I'm back to that original configuration, and somehow things are not working anymore. Also the IT person who managed to get it to work is no longer with the company.

The external display works fine at half res (1280x800), which is the only res shown as available in the settings.

Here's the xrandr command output before trying to change anything:

```
[COLOR=#000000][FONT=Arial]% xrandr[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Screen 0: minimum 320 x 200, current 2646 x 800, maximum 32767 x 32767[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 173mm[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   1366x768       60.1*+[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   1360x768       59.8     60.0  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   1024x768       60.0  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   800x600        60.3     56.2  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   640x480        59.9  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]VGA1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]HDMI1 connected 1280x800+1366+0 (normal left inverted right x axis y axis) 646mm x 406mm[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]   1280x800       59.9* [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]DP1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]HDMI2 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]HDMI3 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]DP2 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]DP3 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]
As you can see, for some reason the mini displayport (which should be DP1) is in fact called HDMI1 - I know that b/c the external screen is connected to that port. My laptop doesn't even have a HDMI port.

I ran the following commands:

```
% cvt 2560 1600 60
# 2560x1600 59.99 Hz (CVT 4.10MA) hsync: 99.46 kHz; pclk: 348.50 MHz
Modeline "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync
```

Then[/FONT][/COLOR]
```
% xrandr --newmode "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync
% xrandr --addmode HDMI1 "2560x1600_60.00"

```

then
```
[COLOR=#000000][FONT=Arial]% xrandr --output HDMI1 --mode "2560x1600_60.00" --verbose[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]screen 0: 3926x1600 1040x424 mm  95.85dpi[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]crtc 1: 2560x1600_60.00   60.0 +1366+0 "HDMI1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]xrandr: Configure crtc 1 failed[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]crtc 0: disable[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]crtc 1: disable[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]crtc 2: disable[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]screen 0: revert[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]crtc 0: revert[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]crtc 1: revert[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]crtc 2: revert[/FONT][/COLOR]
```

and the display returns to the previous resolution

After this step, if I open the GUI screen resolution settings window, I see an option for the 2560x1600 res, but when I select it, I get the error "The selected configuration for displays could not be applied. could not set the configuration for CRTC 64". Also, after this attempt the lcd screen starts acting out with parts of the screen flickering etc, and I need to reboot the system to get it back to a stable state.

I would appreciate any help figuring this out.

Thanks,

Adrian

---

### Post by adrian35 on 2014-08-11
This has been resolved - the issue was the cable. It was supposed to be a Mini DisplayPort -> Dual Link DVI but it turns out it was for Single Link DVI. I purchased a much more expensive one that's clearly marked Dual Link DVI and everything is working now.

---

