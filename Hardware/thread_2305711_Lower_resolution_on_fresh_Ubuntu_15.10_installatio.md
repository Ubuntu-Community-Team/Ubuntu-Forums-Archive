---
title: "Lower resolution on fresh Ubuntu 15.10 installation, Samsung TV and Nvidia GF108"
date: 2015-12-08
forum: Hardware
---

### Post by Rafael_Soto on 2015-12-08
Hello. I've been a long time Ubuntu user, since about 2008 as a secondary OS and since 2012 my main OS.

I have an Ubuntu box that's my main PC, that until last weekend, it had 13.10. I just installed it 15.10 and everything's so much better. Except the screen resolution...

I'm stuck at 1366x768, with 1920x1080 as another option, which looks awful: the pixels are not crips and the screen is cropped as it can't fit the whole canvas.
I've tried everything: a lot of xrandr options, even modifying the xorg conf file. I remember having the same issues back in the other installation, however everything was solved promptly. Thing is, the fix is gone with the new installation.

I remember I could test modes with ```
xrandr -s
```, however it seems that now I have to add a new mode, which either doesn't change much or crops my screen, maintaining the 1366 resolution, but a larger canvas outside the window.

I'm a bit desperate, here's the lspci output:

```
&#10140;  ~  lspci| grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 630] (rev a1)

```

xrandr:

```
&#10140;  ~  xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1366x768      59.79*+
   1920x1080     60.00    59.94    30.00    24.00    29.97    23.98  
   1920x1080i    60.00    59.94  
   1280x720      60.00    59.94  
   1024x768      75.08    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  

```

My display is a 27" Samsung HD TV, I don't quite remember the exact resolution I had previously, but it has to be at least 1920x1080. Also, one weird thing is that in the displays settings, the display is detected as 7"?

[IMG]http://i.imgur.com/yfCCWxI.png[/IMG]

Thanks for reading, I'd appreciate if you guys can bring any light into this issue. Please don't make me buy another screen.. or worse, going back to Windows/OSX!

---

### Post by fafabone on 2015-12-21
I have an intel video processor and the same problem.  Nuc5cpyh connected via hdmi to Samsung Hd Ready LE32S71B (32").I installed Gnome Ubuntu 14.04, with 4.2 Linux Kernel (Wireless driver for NUC needs Linux 4.2).
Monitor is detected as 7".
Have you installed Nvidia drivers? Nvidia-settings doesn't fix your problem?

---

