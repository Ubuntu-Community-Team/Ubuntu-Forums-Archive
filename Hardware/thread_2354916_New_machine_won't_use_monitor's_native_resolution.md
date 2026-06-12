---
title: "New machine won't use monitor's native resolution"
date: 2017-03-07
forum: Hardware
---

### Post by mike-g2 on 2017-03-07
I've got a brand spankin' new computer with a NVIDIA NVS315 video card and an older Dell 3007WFP monitor.  I am using the non-proprietary xserver-xorg-video-nouveau-hwe-16.04.deb (I tried nvidia-367 package, but that didn't work either). As it stands, the only resolution available under System Settings -> Display is 1280 x 800 but the native resolution is twice that (2560 x 1600).  I have tried to use xrandr to allow this higher resolution setting, using the following commands
```

 $ sudo gtf 2560 1600 60                                    
  # 2560x1600 @ 60.00 Hz (GTF) hsync: 99.36 kHz; pclk: 348.16 MHz
  Modeline "2560x1600_60.00"  348.16  2560 2752 3032 3504  1600 1601 1604 1656  -HSync +Vsync
$ sudo xrandr --newmode "2560x1600_60.00"  348.16  2560 2752 3032 3504  1600 1601 1604 1656  -HSync +Vsync
$ sudo xrandr --addmode DP-1 "2560x1600_60.00"    

```
and the 2560x1600 option appears in the System Settings -> Display window, but if I highlight it, I get a black screen.


The file /var/log/Xorg.log doesn't seem to provde any clues for me
> 
[  1864.637] (II) NOUVEAU(0): EDID vendor "DEL", prod id 16406
[  1864.637] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1864.637] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1864.637] (II) NOUVEAU(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz e)
[  1864.693] resize called 2560 1600
[  1895.270] (II) NOUVEAU(0): EDID vendor "DEL", prod id 16406
[  1895.270] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1895.270] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1895.270] (II) NOUVEAU(0): Modeline "2560x1600"x0.0  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync +vsync (98.5 kHz e)
[  1895.327] resize called 1280 800


I've tried using xrandr with the output from 
```

sudo cvt 2560x1600 60                                   # 2560x60 51.40 Hz (CVT) hsync: 3.91 kHz; pclk: 12.50 MHz
Modeline "2560x60_60.00"   12.50  2560 2632 2880 3200  60 63 73 76 -hsync +vsync

```
as well, but get the same behavior (option appears but choosing it gives a blank screen)

Can anyone help me with this?

---

