---
title: "Switching between laptop and widescreen external monitor"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by lajujkej on 2007-08-16
I working on a Dell D420 Laptop with an Samsung 906BW external monitor (1440x900 native resolution).    The video card is an internal intel 945GW and I am using the i810 drivers.

I have been able get my laptop to project 1440x900 to the external screen.  I had to make the following changes:

1.  Set Mode=3a in /etc/default/915resolution.

2.  Place the following in /etc/rc.local

sudo /usr/sbin/915resolution 3a 1440 900 8 1904 934
sudo /usr/sbin/915resolution 4b 1440 900 16 1904 934
sudo /usr/sbin/915resolution 5a 1440 900 32 1904 934

3.  Edit xorg.conf  (following are the relevant sections)

Section "Monitor"
        Identifier      "ShinyNewWidescreen"
        DisplaySize     410 257
        HorizSync       30.0-81.0
        VertRefresh     56.0-75.0
        Option          "DPMS"
        Option          "DDC" "false"
        Modeline        "1440x900" 106.5 1440 1520 1672 1904 900 903 909 934
EndSection

Section "Screen"
        Identifier      "Wide Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "ShinyNewWidescreen"
        DefaultDepth    24
        Option          "MonitorLayout" "CRT"
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
                ViewPort        0 0
        EndSubSection
EndSection


The problem is that now my laptop screen is blank.  How can I configure xorg for two screens so that I can switch between them.  When my laptop screen is properly configured I can use use F8 to switch to the external monitor, but the resolution is wrong.  When I fix the resolution (as above), I can't see the laptop screen.

Any help would be appreciated.

Best wishes,

Robert

---

