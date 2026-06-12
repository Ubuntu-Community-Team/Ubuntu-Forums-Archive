---
title: "Ubuntu 17.10 HDMI monitor not detected"
date: 2017-10-22
forum: Hardware
---

### Post by fh-faraz-hussain on 2017-10-22
Hi, I just upgraded to Ubuntu 17.10 and within a couple of days my external monitor (Dell U2717) is not being detected. Bizarre that it seemed to work for a day or two (maybe I installed something that broke it.)

I am not using Wayland. I am running i3wm on X11.

```
$ echo $XDG_SESSION_TYPE 
x11
```

```
$ echo $XDG_SESSION_DESKTOP 
i3
```

```
$ lspci -v | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06) (prog-if 00 [VGA controller])
```

```

fhussain@machine0:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 310mm x 170mm
   1920x1080     60.00*+  59.93    48.00  
   1680x1050     59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```



I thought it may have to do with xorg.conf, so I added one for Intel:

```
$ cat /usr/share/X11/xorg.conf.d/20-intel.conf
# /etc/X11/xorg.conf.d/20-intel.conf
Section "Device"
  Identifier  "IntelGraphics"
  Driver      "intel"
  Option      "AccelMethod" "sna"
  Option      "TearFree" "true"
EndSection
# end of 20-intel.conf
```

Thanks,
Faraz.

---

### Post by fh-faraz-hussain on 2017-10-22
Update: the external monitor on HDMI was detected after yet another reboot. I think it was either adding the file /usr/share/X11/xorg.conf.d/20-intel.conf or making sure  /etc/X11/xorg.conf.d was symlinked to  /usr/share/X11/xorg.conf.d that made it work.  I'm still not able to control it effectively using xrandr, but at least it always shows up  and controlling it using arandr works.

---

