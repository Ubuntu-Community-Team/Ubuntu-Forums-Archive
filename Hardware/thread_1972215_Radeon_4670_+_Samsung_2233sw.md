---
title: "Radeon 4670 + Samsung 2233sw"
date: 2012-05-03
forum: Hardware
---

### Post by axelmasok on 2012-05-03
Hi team, I like to share some success I have had with these 2 combos of hardware.  Hope it helps someone someday.

Hardware:
HIS ATI/AMD Radeon 4670 AGP (using radeon driver/module)
Samsung SyncMaster 2233sw (1920x1080)

Software:
Kubuntu 12.04 LTS Precise (or older really)

Fault: 
Using VGA-0/DVI-0 the resolution is always 1600x1200.  Drove me nuts.  If I used the HDMI output I would get the full 1920x1080.

Solution:
EDID information not received by the video card.
I have another PC with Nvidia graphics and nvidia driver module.  I used the Nvidia Setup GUI to export the EDID info for the monitor.
Because the default install of Kubuntu has no xor.conf I made one with "Xorg -configure". Copy the resultant file to /etc/X11/xorg.conf.  Test to make sure it works (reboot or logout/kill X).  Then add this to the appropriate "Device" section just under Driver "radeon" :

```
Option  "NoLogo"        "True"
Option "CustomEDID" "VGA-0:/etc/X11/Samsung_2233sw_edid.bin"
```

Edit VGA-0 to DVI-0 or whatever connector you are using.  The Samsung file is obviously the EDID file I exported.

For the radeon driver module this is required so the above CustomEDID is recogised by X.  Place on the kernel boot line in grub:

```
radeon.modeset=0
```

Note: The kernel boot line above basically stops AIGLX from working because it turns KMS off.

If you want full 3D then use the FGLRX driver.  All the above steps don't apply to fglrx.  It won't accept a customer EDID.  
For FGLRX you have a couple options.  

1)  Use xrandr to show you the name of the output your using (e.g CRT2).  Copy the .edid file you have to /etc/ati/crt2.edid.  Restart X server and check the X.org.0.log and see if it accepts the edid file (mine would not).  More info see [http://ati.cchtml.com/show_bug.cgi?id=41]("http://ati.cchtml.com/show_bug.cgi?id=415")5

2) Make an initial xorg.conf that works (e.g amdconfig --initial).  Make sure it works.  Add Virtual   3000 2000 to the Screen section of xorg.conf.  This avoids an error you will encounter later.  The next 3 commands you can put into a script:

```
xrandr --newmode "1920x1080_60" 138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync +vsync
xrandr --addmode CRT2 "1920x1080_60"
xrandr --output CRT2 --mode 1920x1080_60
```

IMPORTANT! The modeline above applied to my Samsung.  Find your own modeline details for your monitor!

Good luck!

---

