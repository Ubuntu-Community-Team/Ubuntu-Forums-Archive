---
title: "Unable to push 4k 60hz on my TV in Ubuntu 20.04"
date: 2020-05-16
forum: Hardware
---

### Post by stripeyare on 2020-05-16
[COLOR=#1A1A1B][FONT=&amp]I have a 4k 60hz TV (Vizio V505-G9) and I am unable to push 60hz on Ubuntu 20.04. I have enabled “Full UHD Color” on my TV settings to allow the 60hz signal to go through, but I’m only receiving options to use 3840x2160 30hz at max. I tried forcing it through xandr, but with no luck. I know that my hardware supports it since I can run 4k 60hz on windows. For reference, I have an AMD RX570.
[/FONT][/COLOR]
$[HTML] cvt 3840 2160 60
# 3840x2160 59.98 Hz (CVT 8.29M9) hsync: 134.18 kHz; pclk: 712.75 MHz
Modeline "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsync

$ xrandr --newmode "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  43
  Current serial number in output stream:  43

$ xrandr --addmode HDMI-A-0 3840x2160_60
xrandr: cannot find mode "3840x2160_60"[/HTML]

When running the Xrandr command, I get this:

[HTML]$ xrandr
Screen 0: minimum 320 x 200, current 3840 x 2160, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
HDMI-A-0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 1096mm x 616mm
   3840x2160     30.00*+  25.00    24.00    29.97    23.98[/HTML]

Strangely enough, 4k 60hz only seems to work for me on linux so far when using Fedora’s gnome desktop environment, I have no idea why that would be the case either. Hopefully that helps somehow.
Here are some additional steps I tried:

[HTML]brandon@brandon-B450M-DS3H:~$ cvt 3840 2160 60
# 3840x2160 59.98 Hz (CVT 8.29M9) hsync: 134.18 kHz; pclk: 712.75 MHz
Modeline "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsync
brandon@brandon-B450M-DS3H:~$ xrandr --newmode "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsync
brandon@brandon-B450M-DS3H:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
HDMI-A-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 1096mm x 616mm
   3840x2160     30.00 +  25.00    24.00    29.97    23.98  
   1920x1200     30.00  
   1920x1080     60.00*   50.00    59.94    30.00    24.00    29.97    23.98  
   1600x1200     30.00  
   1680x1050     30.00  
   1280x1024     30.00  
   1440x900      30.00  
   1280x800      30.00  
   1280x720      60.00    50.00    30.00    59.94    29.97    24.00    23.98  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
HDMI-A-1 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
  3840x2160_60.00 (0x6e4) 712.750MHz -HSync +VSync
        h: width  3840 start 4160 end 4576 total 5312 skew    0 clock 134.18KHz
        v: height 2160 start 2163 end 2168 total 2237           clock  59.98Hz
brandon@brandon-B450M-DS3H:~$ xrandr --addmode HDMI-A-0 3840x2160_60.00
brandon@brandon-B450M-DS3H:~$ xrandr --output HDMI-A-0 3840x2160_60.00
xrandr: unrecognized option '3840x2160_60.00'
Try 'xrandr --help' for more information.
brandon@brandon-B450M-DS3H:~$ xrandr --output HDMI-A-0 --mode 3840x2160_60.00
xrandr: Configure crtc 0 failed
brandon@brandon-B450M-DS3H:~$ [/HTML]

[COLOR=#1A1A1B][FONT=&amp]Strangely enough, it does show me an option to choose “59.98hz” when I updated those settings. When I try selecting it; however, nothing seems to change.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR][IMG]https://preview.redd.it/t6wrvqed15z41.png?width=1190&format=png&auto=webp&7e11c21e[/IMG]
[COLOR=#1A1A1B][FONT=&amp][[IMG]https://preview.redd.it/t6wrvqed15z41.png?width=1190&format=png&auto=webp&7e11c21e[/IMG]]("https://preview.redd.it/t6wrvqed15z41.png?width=1190&format=png&auto=webp&7e11c21e")
[/FONT][/COLOR][IMG]https://forum.level1techs.com/uploads/default/optimized/4X/b/b/9/bb98f9427ddd43cdf53a8bc1e1b4c67cb4b9113f_2_720x446.png[/IMG]

[CENTER][COLOR=#1A1A1B][FONT=&amp]Showing as an option in the display settings, but selecting it and applying doesn't actually set it to 60hz unfortunately.[/FONT][/COLOR][/CENTER]
[COLOR=#1A1A1B][FONT=&amp]I tried performing the following steps:
[/FONT][/COLOR]
[HTML]brandon@brandon-B450M-DS3H:~$ cvt -r 3840 2160 60
# 3840x2160 59.97 Hz (CVT 8.29M9-R) hsync: 133.25 kHz; pclk: 533.00 MHz
Modeline "3840x2160R"  533.00  3840 3888 3920 4000  2160 2163 2168 2222 +hsync -vsync
brandon@brandon-B450M-DS3H:~$ cd /usr/share/X11/xorg.conf.d/
brandon@brandon-B450M-DS3H:/usr/share/X11/xorg.conf.d$ sudo nano

Section "Monitor"
   Modeline "3840x2160R"  533.00  3840 3888 3920 4000  2160 2163 2168 2222 +hsync -vsync
   Option         "UseEdid" "FALSE"
EndSection

Section "Device"
   Option         "ModeValidation" "AllowNonEdidModes"
EndSection[/HTML]

[COLOR=#1A1A1B][FONT=&amp]Then I saved it as “xorg.conf” then rebooted. By doing this, I accidentally crashed xorg. I had to do:
[/FONT][/COLOR]
[HTML]sudo rm /usr/share/X11/xorg.conf.d/[/HTML]
[COLOR=#1A1A1B][FONT=&amp]
from the TTY1 terminal thing by doing Ctrl Alt F2 from the login screen to be able to login again. I’m still having issues with 4k 60hz running under Ubuntu. Here’s a screenshot from my Windows partition using my TV’s menu to show that the hardware is capable in supporting 4k 60hz:[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR][IMG]https://forum.level1techs.com/uploads/default/original/4X/7/8/2/78229217afce6008f10c57737d8b136e38406b9c.jpeg[/IMG]
[COLOR=#1A1A1B][FONT=&amp][[IMG]https://preview.redd.it/6241j8i525z41.png?width=894&format=png&auto=webp&8dad6bc1[/IMG]]("https://preview.redd.it/6241j8i525z41.png?width=894&format=png&auto=webp&8dad6bc1")
[/FONT][/COLOR]
[CENTER][COLOR=#1A1A1B][FONT=&amp]This a screenshot of the "about" menu on my TV running on my Windows partition to show that this screen is capable of outputting a 60hz 4k signal.[/FONT][/COLOR][/CENTER]
[COLOR=#1A1A1B][FONT=&amp]Under Ubuntu, it can only go up to 4k 30hz still. Hopefully someone can give me some pointers. Thank you in advance.[/FONT][/COLOR]

---

