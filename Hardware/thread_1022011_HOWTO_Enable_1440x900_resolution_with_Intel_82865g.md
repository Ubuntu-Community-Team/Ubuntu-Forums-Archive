---
title: "HOWTO: Enable 1440x900 resolution with Intel 82865g integrated graphics on Intrepid"
date: 2008-12-26
forum: Hardware
---

### Post by Johnny Golden on 2008-12-26
This worked for me on an old Dell Optiplex GX270:

Launch a terminal window and enter the following command:
```
sudo gedit /etc/X11/xorg.conf
```

Enter your password if prompted.  The xorg.conf document will then launch in gedit.

Add the following line under Section "Monitor":
```
Modeline     "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
```

Add following lines under Section "Screen":
```
SubSection "Display"
     Viewport       0 0
     Depth         24
     Modes         "1440x900_60.00"
EndSubSection
```

Select "Save" from the file menu, then "Close".

Shut down any running programs and then restart X Server using Ctl+Alt+Backspace.  Log back in and go to System > Preferences > Screen Resolution.  Choose Resolution 1440x900 and then Apply.  You may need to restart the PC for the change to take effect without display errors.

This may work with other widescreen resolutions.  To generate modelines for different resolution/refresh rate combinations use the command gtf [hres] [vres] [refresh rate], e.g. for a monitor with 1680x1050 native resolution:
```
gtf 1680 1050 60
```

---

### Post by ditobarata on 2008-12-26
and how to enable 1680x1200 resolution with my acer 4520?

---

### Post by Johnny Golden on 2008-12-26
According to the Acer web site, the 4520 uses an integrated NVIDIA GeForce 7000M chipset.  Have you tried installing the proprietary NVIDIA drivers (using System > Administration > Hardware Drivers and then clicking Activate) and then checking supported resolutions in System > Administration > Nvidia X Server Settings under the X Server Display Configuration setting?

---

### Post by joemacnz on 2009-03-31
This worked a treat, thank you.

---

