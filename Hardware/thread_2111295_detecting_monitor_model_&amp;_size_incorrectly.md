---
title: "detecting monitor model &amp; size incorrectly"
date: 2013-02-01
forum: Hardware
---

### Post by Digital Magi on 2013-02-01
Did a fresh install of 12.04 and am having a bit of hardware trouble. My monitor (which worked great on 11.04) is not being detected properly.

I am running a Samsung Syncmaster 932BW 19" VGA LCD with a 1440x900 native resolution. Graphic chip is an onboard NVIDIA Quadro NVS 210S.

The monitor is being detected as a 20" generic LCD, and as such I have to resize the screen using the physical controls on the monitor. This is not optimal and distorts the display.

After some reading on the new changes in X I got the monitor specs from the manual and generated a custom 10-monitor.conf file which defined the size of the monitor. This did not work, caused error at boot. Switched to a terminal and deleted the file then it booted again. Not sure what I am doing wrong. This is my first time trying to do a manual display config.

here is the 10-monitor.conf I wrote and placed in /usr/share/X11/xorg.conf.d/

```
#10-monitor.conf:

Section "Monitor"
  Identifier    "Samsung Syncmaster 932BW"
  VendorName    "Samsung"
  ModelName     "932BW"
  DisplaySize    408.24 255.15
  HorizSync 30-81
  VertRefresh 56-75
  Option "DMPS" = "true"
  #modelines calculated using cvt
  # 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
  Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
EndSection

Section "Device"
  Identifier    "NVIDIA Quadro NVS 210S"
  Option        "Monitor-VGA-0"  "Samsung Syncmaster 932BW"
EndSection

Section "Screen"
  Identifier    "Default Screen"
  Monitor       "Samsung Syncmaster 932BW"
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
EndSection
```

---

### Post by Digital Magi on 2013-02-08
bumpity-bump

Any ideas? Am I going about this the wrong way?

Since the monitor wasn't detected correctly, I figured that defining the parameters myself was the way to go. I couldn't find any newbie-friendly references on making a custom 10-monitor.conf so my attempt may have been improperly written/syntaxed.

Did I make a massive typo or something similarly bone-headed?
Or is this just the wrong approach?

---

### Post by sudodus on 2013-02-09
Ubuntu 12.04 LTS should be rather well debugged by now.

I suggest that before resorting to complicated tweaking, you run live sessions (booted from the Ubuntu install CD/USB drive and try some boot options. Start with nomodeset.

See this link [[COLOR="Red"]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

Try with the built in driver (probably nouveau will be selected), and then try with the suggested nvidia proprietary driver (if ***jockey-gtk*** is suggesting one). If I remember correctly, these operations are possible to do without reboot, so it works in a live session.

---

### Post by papalagi on 2013-02-10
I world suggest using xrandr and cvt to find and test the correct modeline for the monitor, way more practical:

[http://askubuntu.com/questions/19954/how-to-set-the-monitor-to-its-native-resolution-which-is-not-listed-in-the-resol/19956#19956](http://askubuntu.com/questions/19954/how-to-set-the-monitor-to-its-native-resolution-which-is-not-listed-in-the-resol/19956#19956)

---

