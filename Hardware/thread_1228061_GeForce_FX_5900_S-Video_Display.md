---
title: "GeForce FX 5900 S-Video Display"
date: 2009-07-31
forum: Hardware
---

### Post by PRupp89 on 2009-07-31
Hello everyone, I'm new to Ubuntu and have been using it for about 6 months or so, and would love to get my old pc I have it installed on to use my TV screen as my monitor instead of my old CRT screen, because I plan on using the machine as a media PC to put my home movies on and such, and having to take the CRT monitor back and forth with me to and from college would be a lot of extra weight I don't need. Anywho, I have looked for guides about changing the settings to get it to work but I haven't had any luck. Could someone point me in the right direction on what to do to get it set up? Here's my current xorg.conf file:

```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Princeton Graphics Systems PrincetonEO705"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5900"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0; 1024x768_85 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

I apologize in advance for the lack of knowledge with Ubuntu, but I'm willing to learn and really could use good step by step instructions to get this set up. Thank you!

---

### Post by davidmohammed on 2009-07-31
little hard to be specific - need to know which version of ubuntu you are using.  

At a guess looks like you are using hardy

presume you've looked at threads such as [this one]("http://ubuntuforums.org/showthread.php?t=625435&highlight=s-video")?

---

### Post by PRupp89 on 2009-07-31
> **davidmohammed said:**
> little hard to be specific - need to know which version of ubuntu you are using.  

At a guess looks like you are using hardy

presume you've looked at threads such as [this one]("http://ubuntuforums.org/showthread.php?t=625435&highlight=s-video")?
Yes I have, however isn't that just for ATI or Intel cards? And I'm using Jaunty 9.04. Hopefully you can help me out, and if you need any more details I'll let you know (I'm fairly new to this so I'm not sure what exactly you need to know in order to help me out). Thank you!

---

### Post by PRupp89 on 2009-07-31
Also to clarify I'd like if its possible to turn my TV into my primary (and preferably only) display, not just have the video go out to the tv like most things show.

I decided to try xrandr anyways, and after I got the settings set in VLC (which isn't the program I want to use -- I want to use moovida) I opened up terminal and typed in:
```
xrandr --addmode S-video 800x600
```
and it told me
```
xrandr: cannot find output "S-video"
```

---

### Post by davidmohammed on 2009-07-31
are you trying to hand-craft this or are you using nvidia-settings?

If the latter, it should create the 
Option         "TVOutFormat" "SVIDEO"

in your device settings.

Are you using a restricted driver (in System -Administration - Hardware Drivers) or the standard drivers?

Given that you are using jaunty I would suggest it should be able to cope with S-video directly using a clean xorg.conf

regenerate with
sudo dpkg-reconfigure -phigh xserver-xorg

Could be useful if you post your /var/log/Xorg.0.log - should give details of all the modes available for your driver.

---

