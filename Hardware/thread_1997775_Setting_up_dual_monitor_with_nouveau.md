---
title: "Setting up dual monitor with nouveau"
date: 2012-06-05
forum: Hardware
---

### Post by Arathorn on 2012-06-05
Hi,

I have a Dell XPS laptop and a Samsung external Samsung SyncMaster 2433 monitor that's connected with an HDMI cable and an HDMI to DVI-D adapter (the Samsung doesn't have an HDMI-input). The problem is that I can't get xrandr to detect it and set it up. Running xrandr in Konsole gives me this:

```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```There's no /etc/X11/xorg.conf I've checked how-to's and man pages, but I'm not Linux-savvy enough to make my own xorg.conf. I have Windows 7 in dual boot and the external monitor works just fine, so it isn't a problem with my monitor or cable. Can anyone help me

---

