---
title: "Sound control doesn't work with penmount"
date: 2009-05-21
forum: Hardware
---

### Post by punong_bisyonaryo on 2009-05-21
Hi. When I install the penmount driver on my laptop, the sound volume rocker stops working. I'd file a bug report, but I have no idea what the problem is, except that by reverting xorg.conf, I get sound control back but lose penmount calibration.

Here's the code that gets appended to xorg.conf:

```
Section "InputDevice"
  Identifier  "Penmount"
  Driver    "penmount"
  Option  "Device"           "/dev/input/event5"
  Option  "Protocol"         "PM6000USB"
  Option  "BaudRate"         "19200"
  Option  "ADBit"            "10"
  Option  "ConfigFile"       "/etc/penmount.dat"
  Option  "Button2"          "3"  # 1=left, 2=middle, 3=right
  Option  "PenDownMode"      "0"  # 0=stream mode, 1=point mode
  Option  "HoldTime"         "500"  # how long ms to launch the 2nd button
  Option  "ScreenScale"      "0"  # screen scale enable/disable
  Option  "LockWindowRange"  "32"  # range for press and hold
  Option  "CalibHoldTime"    "750"  # hold time for calibration
  Option  "XMinOffset"       "10"  # edge compensation
  Option  "XMaxOffset"       "10"
  Option  "YMinOffset"       "10"
  Option  "YMaxOffset"       "10"
  Option  "StdXMin"          "30"  # standard calibration
  Option  "StdXMax"          "990"
  Option  "StdYMin"          "30"
  Option  "StdYMax"          "990"
  Option  "Beep"             "1"  # 0=off, 1=down, 2=up, 3=down+up
  Option  "PressVol"         "100"  # 0 = slience
  Option  "PressPitch"       "880"  # freq. (Hz)
  Option  "PressDur"         "15"  # duration (1~255)
  Option  "ReleaseVol"       "0"  # 0 = slience
  Option  "ReleasePitch"     "1200"  # freq. (Hz)
  Option  "ReleaseDur"       "10"  # duration (1~255)
  Option  "AveragePoint"     "0"  # average point (0,4,8)
  Option  "Rotation"         "1"  # rotation (1,2,4,8)
  Option  "RandR"            "0"  # RandR enable/disable)
  Option  "DebugLevel"       "0"  # debug
EndSection


Section "ServerLayout"
  Identifier  "Default Layout"
  Screen      "Default Screen"
  InputDevice  "Penmount" "AlwaysCore"
EndSection

Section "ServerFlags"
  Option  "AutoAddDevices"   "False"
EndSection

```

If anyone has any idea, I'm all ears (or eyes).

---

### Post by punong_bisyonaryo on 2009-05-30
Was just wondering if anyone has any idea, any idea at all, about this. Thanks!

Edit: I tried tinkering with xorg.conf, and removed the AddAutoDevices part. I thought it was kinda weird although I don't know *exactly* what it does, because...shouldn't I want to automatically add devices?

Anyway, long story short, that solved the problem and I'm checking right now if there are any side effects. I now have a calibrated touch screen and my sound rocker's working again.

Hope this helps someone.

---

