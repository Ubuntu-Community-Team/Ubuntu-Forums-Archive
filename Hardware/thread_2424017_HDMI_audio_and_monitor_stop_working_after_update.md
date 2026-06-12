---
title: "HDMI audio and monitor stop working after update"
date: 2019-08-01
forum: Hardware
---

### Post by jonzuccaro on 2019-08-01
This is my dual monitor setup:

Ubuntu 16.04 xenial

x86_64 Linux 4.4.0-157-generic

GeForce GTX 750 Ti

Asus Z170-A

Everything was working fine, then, after some update that I can't pinpoint my HDMI monitor stopped working giving a blank screen.

After changing the screen resolution from 1680x1050 to 1600x1000 the image came back. I now have no HDMI audio (it disappeared from the Sound Settings) and am unable to change the resolution back to 1680x1050 as this causes the screen to go blank and have to revert to the previous configuration.

Previously, the login screen appeared on both screens, now it only shows on the DVI monitor.

I am currently using NVIDIA binary driver 384.130.

I've purged and installed several different NVIDIA drivers from ppa:graphics-drivers/ppa to no avail, some of them actually cause the system to boot to a blank screen with a blinking cursor. I've purged everything and went back to the distro proprietary tested one.

The cable and monitor work perfectly (video and audio) on another computer.

If I try to boot from a live 18.04 USB drive the boot fails and only shows a blank screen without the blinking cursor.

I paid no attention to the packages that were being updated since every update has worked flawlessly for years, but something broke this time.

Any help would be appreciated.

```
Screen 0: minimum 8 x 8, current 2880 x 1154, maximum 16384 x 16384
DVI-I-0 connected primary 1280x1024+1600+130 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024     60.02*+  75.02  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1600x1000+0+0 (normal left inverted right x axis y axis) 470mm x 300mm
   1680x1050     59.95 +
   1920x1080     59.94    50.00    60.05    50.04  
   1600x1000     60.00* 
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1280x720      59.94    50.00  
   1152x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
DP-1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by spacey2 on 2019-08-02
I have a similar problem. I cannot detect any HDMI monitor anymore with my Dell Inspiron 14 5458. I believe I have GeForce 920M with the nvidia-390 driver, which apparently was last updated on 29.7.2019


EDIT: I got the external monitor to work again by booting to 4.15.0-54-generic kernel. So, it seems like 4.15.0-55-generic broke something for me. @[**[COLOR=#000000]jonzuccaro[/COLOR]**]("https://ubuntuforums.org/member.php?u=781568") you can select a different kernel in the GRUB menu at boot time.

---

### Post by jonzuccaro on 2019-08-02
I tried booting with a previous kernel  to no avail.

My monitor is actually detected but, out of the blue, it can no longer display the recommended resolution of  1680x1050, it just goes blank.

I also thought about finally updating to 18.04 but trying to boot to a live USB causes both my monitors to go blank.

---

### Post by spacey2 on 2019-08-02
Seems like booting with an older kernel fixed something and 4.15.0-55-generic is working now too with an external monitor for me.

---

