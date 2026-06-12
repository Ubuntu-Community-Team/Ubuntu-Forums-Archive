---
title: "nVidia 9600GT"
date: 2008-06-10
forum: Hardware
---

### Post by CLomax on 2008-06-10
I understand that this is a rather new card so there may not be good support for it yet, however, others have it working so it is possible. Below is the exact procedure I followed to install the 173.14.05 beta nVidia driver for the x86 architecture, this claims to support the 9600GT.

Could anyone please tell me if there is something wrong with what I did here:

Download 173... yaddayadda
Renamed to 'nvidia.run' [Also tried not renaming it]
'sudo apt-get build-essential'
'sudo apt-get remove nvidia*'

Ctrl+Alt+F1 {tty1}

logged in as me:
 'cd /home/uname/Desktop' {CD to file}
 'chmod a+x nvidia.run'   {Make executable}
 'sudo /etc/init.d/gdm stop' {Stop gnome/X server}
 'sudo sh nvidia.run'     {sh file}
Followed install procedure on screen:
 'sudo reboot now'

Once loading startup scripts the fan quiets from 100% noise, then speeds up again and repeats this about 3/4 times. Then the screen produces a heavily distorted display, impossible to work with.

---

### Post by CLomax on 2008-06-11
Update:

Attached photo of screen distortion, hopefully it helps in some way.

Also, the relevant parts of my /etc/X11/xorg.conf as follows:


[I]Section "Monitor"
  Identifier "Unknown"
  VendorName "Unknown"
  ModelName  "Unknown"
  HorizSync   30.0 - 110.0
  VertRefresh 50.0 - 150.0
  Option     "DPMS"
EndSection

Section "Device"
  Identifier  "Device0"
  Driver      "nvidia"
  VendorName  "NVIDIA corporation"
EndSection

Section "Screen"
  Identifier  "Screen0"
  Device      "Device0"
  Monitor     "Monitor0"
  Default depth 24
  Option      "AllowGLXWithComposite" "True"
  Option      "RandRRotation" "True"
  Option      "AddARGBGLXVisuals" "True"
  SubSection "Display"
    Depth  24
  EndsubSection
EndSection
[/I]

Hopefully, this will be useful to anyone willing to help.

---

### Post by tenmoi on 2008-06-16
Here is your solution.

[http://ubuntuforums.org/showthread.php?t=819043&page=5](http://ubuntuforums.org/showthread.php?t=819043&page=5)

---

