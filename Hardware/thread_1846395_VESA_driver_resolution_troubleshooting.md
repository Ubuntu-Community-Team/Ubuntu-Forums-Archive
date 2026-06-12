---
title: "VESA driver resolution troubleshooting"
date: 2011-09-18
forum: Hardware
---

### Post by lukeiamyourfather on 2011-09-18
I'm using Ubuntu 10.04 LTS (Lucid Lynx) to control a CNC machine. The software is called EMC2 and is only built for LTS releases of Ubuntu so using a newer version of Ubuntu is not an option, more on that [here]("http://www.linuxcnc.org"). It appears there are no drivers for my video card, a Radeon 6870, in this version of Ubuntu. That leads me into tweaking the VESA driver resolution stuff.

When trying to setup a higher resolution to match the monitor it says the resolution is beyond the maximum. Why does it say this? Maximum of what? Both the monitor and the video card are capable of 1440x900 but it says the maximum is 1280x1024 for some reason.

```

lolson@cnc:~$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
lolson@cnc:~$ xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
lolson@cnc:~$ xrandr --addmode default 1440x900_60.00
lolson@cnc:~$ xrandr --output default --mode 1440x900_60.00
xrandr: screen cannot be larger than 1280x1024 (desired size 1440x900)
lolson@cnc:~$

```

Any suggestions on where to take this next? I've spent a lot of time looking through forums and manuals but haven't found a good answer to this error. Thanks for your time and help!

---

### Post by lukeiamyourfather on 2011-09-22
Bump. This is frustrating, considering purchasing an older graphics card to get it to work.

---

### Post by .... on 2011-09-22
The available VESA resolutions depend on what's defined in the card's BIOS. You may be able to see these in /var/log/Xorg.0.log

Unfortunately, getting the open-source radeon driver to support this card would require a major kernel update. You're probably best off finding an older card to work with. Your other option is installing a recent fglrx/Catalyst driver. [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

---

### Post by lukeiamyourfather on 2011-09-23
> **.... said:**
> The available VESA resolutions depend on what's defined in the card's BIOS. You may be able to see these in /var/log/Xorg.0.log

Unfortunately, getting the open-source Radeon driver to support this card would require a major kernel update. You're probably best off finding an older card to work with. Your other option is installing a recent fglrx/Catalyst driver. [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

Thanks for the link. I tried the swat and edgers PPA with the newer open source graphics drivers, no luck there. Also tried manually installing the binary driver and it throws errors when running anything 3D and everything else is extremely slow to refresh. Probably because of the RTAI kernel used by the machine control software. I guess I'll find another graphics card. Thanks again!

---

