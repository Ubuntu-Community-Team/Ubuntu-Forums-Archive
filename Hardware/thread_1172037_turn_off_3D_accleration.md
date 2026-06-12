---
title: "turn off 3D accleration?"
date: 2009-05-28
forum: Hardware
---

### Post by scottc52 on 2009-05-28
how do you turn off 3D acceleration from the terminal?

---

### Post by scottc52 on 2009-05-28
please, I need help. My Ubuntu gets stuck at login if I try normal boot, so I can't do anything on it.

---

### Post by gradinaruvasile on 2009-05-28
More details would be good.
Which Ubuntu version are u using? What graphics card do u have? What drivers are u using (proprietary, opensource -i.e. what comes with ubuntu by default)?

---

### Post by scottc52 on 2009-05-28
I am using Ubuntu Studio, but I don't see how it'll make much difference, since I'm trying to do this from a terminal. Also, I have a 5 year old ATI graphics card that is NOT supported by any of their drivers anymore (whether it's for windows, linux, or mac). Therefore, any suggestions about finding the right driver for my graphics card is useless. (Trust me I've looked.) I've had similar problems with other distros trying to use 3D acceleration without proper drivers, and turning it off usually solves the issue. So, I need to know how to turn off all 3D acceleration functions from the Ubuntu recovery mode terminal.

---

### Post by vivedekananda on 2009-05-28
What you probably want to do is to switch to the open source driver ati(depending on your graphics card, that doens't necessarily mean you will not have 3D acceleration).
You will need to edit your xorg.conf file, use the command:
sudo nano /etc/X11/xorg.conf

Then, look for the following section(can be a bit different):
################xorg.conf######################
Section "Device"
        Identifier      "ATI bla bla yourcard"
        Busid           "PCI:7:0:0"
        Driver          "fglrx"    #YOU HAVE TO CHANGE THIS
        Option          "VideoOverlay"          "on"
        Screen  0
EndSection
##############xorg.conf##################

Then change the line
##########################
Driver          "fglrx"
##################
to
#########################
Driver          "ati"
###########################

Make sure you have the "ati" driver installed, use:
sudo apt-get install xserver-xorg-video-ati

I am not sure if this is what you are looking for, or if it is going to help.

In any case posting your Ubuntu version (not Studio/Desktop, but the actual number 9.04, 8.10 or similar, this will probably show in your terminal), teh type of your graphics card, and your xorg.conf would help people to help you.

Let us know how you progress.

---

### Post by kpkeerthi on 2009-05-28
Yes. Definitely try with the "ati" driver. If it doesn't help, you can switch to a more "generic" driver **xserver-xorg-video-vesa**. And you would have to use **Driver "vesa"** in xorg.conf.

---

### Post by scottc52 on 2009-05-30
As I've already mentioned, NO drivers fully work with my ATI card, including radeon, ati, radeonhd, and the propriety drivers. None. I'm using VESA right now. On a different distribution, I solved the issue by using fgrlx propriety drive with 3D acceleration capabilities turned off. I want to do this, because it gives better 2D performance, and allows me to have higher resolutions than with VESA. So, any advice?

---

### Post by scottc52 on 2009-05-30
ok, I solved my problem (although in a sucky) way. I basically took to xorg.conf files from my openSUSE installations and copied and pasted it to ubuntu. One thing though, the one that I used fglrx on doesn't work with ubuntu for some reason. So I had to dig up an old old openSUSE that I had on a different harddrive. So now I'm running Vesa but with high resolution. Here's what my xorg.conf looks like now. It may help if you're trying to get higher resolution with Vesa:

Section "ServerFlags"
  Option       "AllowMouseOpenFail" "on"
  Option       "ZapWarning" "on"
EndSection

Section "Module"
  Load         "freetype"
  Load         "extmod"
  Load         "dbe"
  Load         "glx"
  Load         "dri"
EndSection

Section "InputDevice"
  Driver       "kbd"
  Identifier   "Keyboard[0]"
  Option       "Protocol" "Standard"
  Option       "XkbLayout" "us"
  Option       "XkbModel" "microsoftpro"
  Option       "XkbRules" "xfree86"
EndSection


Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "ImPS/2 Generic Wheel Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[3]"
  Option       "Buttons" "7"
  Option       "Device" "/dev/input/mice"
  Option       "Emulate3Buttons" "on"
  Option       "HorizScrollDelta" "0"
  Option       "InputFashion" "Mouse"
  Option       "Name" "Synaptics;Touchpad"
  Option       "Protocol" "explorerps/2"
  Option       "SHMConfig" "on"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
  DisplaySize  305 230
  HorizSync    30-40
  Identifier   "Monitor[0]"
  ModelName    "Unknown"
  Option       "DPMS"
  Option       "PreferredMode" "1280x1024"
  VendorName   "Unknown"
  VertRefresh  50-75
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
EndSection


Section "Screen"
  DefaultDepth 16
  SubSection "Display"
    Depth      15
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


Section "Device"
  BoardName    "Radeon LW"
  Driver       "vesa"
  Identifier   "Device[0]"
  Option       "XAANoOffscreenPixmaps" "true"
  Screen       0
  VendorName   "ATI"
EndSection



Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  InputDevice  "Mouse[3]" "SendCoreEvents"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Screen       "Screen[0]"
EndSection


Section "DRI"
    Group      "video"
    Mode       0660
EndSection

Section "Extensions"
EndSection

---

### Post by vivedekananda on 2009-05-31
> 
Section "Device"
BoardName "Radeon LW"
Driver "vesa"
Identifier "Device[0]"
Option "XAANoOffscreenPixmaps" "true"
Screen 0
VendorName "ATI"
EndSection


You could experiment with your xorg.conf by changing the driver line to "ati"/"fglrfx" and adding the following lines in the above device section:
```

Option "DRI" "off" #this might switch off 3d acceleration
Option "NoAccel" "true" #this completely switches off hardware acceleration

```

Your problems might be specific to your graphics card type, and workarounds the switching off 3D acceleration might exist. To identify the type of your card run
```
lspci -nn | grep VGA
```
If you have an older card, it should be supported by the open source driver [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver").

Oh, and I also found at [https://wiki.ubuntu.com/X/Quirks]("https://wiki.ubuntu.com/X/Quirks"), that seting agpmode to lower values might sometimes be required, e.g.
```

Option "AGPMode" "2"
```

Btw, could you also post your opensuse xorg.conf that works with fglrx(are you sure you have the fglrx driver installed in ubuntu)?

---

