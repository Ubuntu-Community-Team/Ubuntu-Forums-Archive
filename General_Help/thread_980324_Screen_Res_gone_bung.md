---
title: "Screen Res gone bung"
date: 2008-11-12
forum: General Help
---

### Post by clegends on 2008-11-12
Hi folks, having issues with my screen resolution and desktop size. Just changed my screen res from 1280x1024 to 1152x864. Even after exiting from X, and then a full system reboot, my screen is still 'larger' than what is shown. Firefox maximizes outside of the visible area, as do other windows when they're maximized. Problem is solved when I return to the 1280x0124 resolution. However, I really like 1152x864! Can someone tell me how to fix this? I'm on Hardy 8.04. Cheers!

~clegends

---

### Post by clegends on 2008-11-18
Bump

---

### Post by loomsen on 2008-11-18
There are a couple of possibilities to achieve a custom resolution.
But in any case I know, if you want to make it right, you have to write it down in your xorg.conf.

The pkg xutils ships with a handy little tool, which will calculate possible modlines for you, which you can add to your xorg.conf then.
The tool is used with:
```

cvt <vertsync> <horizsync> <refreshrate(optional)>

```

So, in you case you would run:
```

cvt 1152 864 50

```
And as possible refreshvalues are 50,60,75,85, you'll have to run it 4 times for each refreshrate. This will then generate you some kind of custom modeline, mine for instance looks like this:
> 
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
#    HorizSync       30.0 - 110.0
#    VertRefresh     50.0 - 150.0
# 1440x900 49.88 Hz (CVT 1.30MA) hsync: 46.34 kHz; pclk: 86.75 MHz
Modeline "1440x900_50.00"   86.75  1440 1512 1656 1872  900 903 909 929 -hsync +vsync
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
# 1440x900 74.98 Hz (CVT 1.30MA) hsync: 70.64 kHz; pclk: 136.75 MHz
Modeline "1440x900_75.00"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
# 1440x900 84.84 Hz (CVT 1.30MA) hsync: 80.43 kHz; pclk: 157.00 MHz
Modeline "1440x900_85.00"  157.00  1440 1544 1696 1952  900 903 909 948 -hsync +vsync
    Option         "DPMS"
EndSection


I had to run it cause nvidia-autoselect chose a wrong DPI which screwed up everything. This however should do the trick for you as well.

run
```
man xorg.conf
```
for information how to edit your xorg.

---

### Post by clegends on 2008-11-18
Thanks matey, I'll stick with 1268x1024. Though not ideal, it works. Part of the reason I installed Ubuntu was so I had a distro I didn't have to screw around with... I develop software on Puppy Linux for that. Cheers.
~clegends

---

