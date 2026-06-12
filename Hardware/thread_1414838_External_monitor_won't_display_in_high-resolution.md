---
title: "External monitor won't display in high-resolution"
date: 2010-02-24
forum: Hardware
---

### Post by sparky2 on 2010-02-24
Is there a general problem in Karmic when using external monitors in high resolution on laptops??

I posted below twice before under other sections, but not 1 response...

I can boot into Windows XP on my Thinkpad (Lenovo) X60 and display to my external Dell 22" monitor at full resolution just fine. But when I boot Ubuntu Karmic I can only get the external monitor to mimic the thinkpad display resolution 1024 x 768.

Using the Fn-F7 keys to toggle through the three display modes:

1) Thinkpad only
2) Thinkpad and External monitor simultaneusly (1024 x 768 )
3) External monitor only

I can get modes 1) and 2) but third mode displays nothing on either screen and I even have to do a power-off restart! ugly

Any suggestions ??

---

### Post by wanchai on 2010-02-27
I don't think it's a general problem in Karmic. I tested 9.10 with my HP Elitebook 6930p and a Samsung SyncMaster 172b monitor. I can toggle through all three monitor modes using the function key. The Gnome display properties panel recognizes the monitor properly, and it allows me to select modes "mirrored", "extended" and "off". 

Have you tried the Gnome display properties panel? Does is recognize your monitor properly? I think the function key will only select mirror mode and will try to match the resolution of your laptop and your external monitor somehow.

---

### Post by efflandt on 2010-02-28
For laptops I have with VGA output, when I boot with an external monitor connected X seems to try to find a matching resolution for both (typically 1024x768 ).  I use scripts with xrandr commands to add a mode for the external display, switch to it, and turn off the laptop display.  This is an example for 1080p HDTV for Intel video [names of outputs may vary for ATI (VGA-0), nVidia (?), etc.]:

```
#!/bin/bash
xrandr --newmode "1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output LVDS1 --off
xrandr --output VGA1 --mode 1920x1080_60.00
exit
```

---

### Post by desmane on 2010-03-01
can you post the output of 

```
xrandr 
```


you might have to install it first, its in repos

---

