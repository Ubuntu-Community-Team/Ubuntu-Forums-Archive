---
title: "shutdown xfce"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by zoomiest on 2008-02-04
I am still having problems getting XFCE to recognize my wide screen. I set the resolution to 1440 x (various) and the fonts squish together but there is still a large black blank on the left hand side of the screen.

xfce 4.4
LG widescreen
NVIDIA card
Xubuntu (latest for amd64)

SO FAR:
I HAVE the latest NVIDIA driver - but**_ I cant shut down xfce!!!!!_** (which installation requires...)
I have read the postings on using xfsm-shutdown-helper but I can find it... its not in sbin, its not in libexec... (dont have one anyway)...

any help would be appreciated.

---

### Post by erginemr on 2008-02-04
Could you please post your xorg.conf file with:
cat /etc/X11/xorg.conf
and what is the natural resolution of your monitor? 1440x900?

---

### Post by zoomiest on 2008-02-04
Surely...

1. yes, the default resolution is 1440 x 900

2. As requested:
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "intl"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation GeForce 7100 GS"
        Driver          "nv"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "L194WTX"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation GeForce 7100 GS"
        Monitor         "L194WTX"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

---

### Post by erginemr on 2008-02-04
First, you should back up your current X configuration to be used in case something goes wrong after taking the following steps:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
``` 

I suggest you to change the line:
```
Modes "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
```
as:
```
Modes "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
```
by dropping the first resolution and restarting your X server with Ctrl+Alt+BackSpace.

If it doesn't make any difference (and also even if it works): 

Apparently, you are using the open source "nv" driver for your NVidia card. However, according to the following list, your card "GeForce 7100 GS" is supported by the "nvidia-glx-new" package:
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

For best performance and 3D support, I suggest you to install the binary driver for your card with either through Alt+F2 -> "restricted-manager", or via

```
sudo aptitude install nvidia-glx-new
sudo nvidia-xconfig
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then, you can edit the xorg.conf file further to add your custom resolutions if necessary. Also there is a tool Alt+F2 -> "nvidia-settings" that comes with the binary installation, from where you can presumably adjust some settings of your desktop such as the screen resolution.

The following site will give you more info on this:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by erginemr on 2008-02-05
Alternatively, you can keep your "Modes" section intact as:
```
Modes "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
```
but can add the following line to your **"Device"** section:
```
Section "Device"
Identifier "nVidia Corporation GeForce 7100 GS"
Driver "nv"
BusID "PCI:2:0:0"
**[COLOR="Red"]Option "MetaModes" "1440x900"[/COLOR]**
EndSection
```

which will presumably force your screen resolution to 1440x900.

Regarding your second problem, can you please explain it a little more:
> I HAVE the latest NVIDIA driver - but I cant shut down xfce!!!!! (which installation requires...)

I assume the shut down dialog comes up when you try to switch off your system, but without the shut-down/restart buttons. Or is it something else?

---

### Post by zoomiest on 2008-02-05
Thanks for all your helps. I will implement your suggestions, above.

Regarding the second issues, for which you requested more explanation... To resolve my problem, I downloaded the latest NVIDIA drivers, but during the install process it asks me to shut down the X server... (which is XFCE, right?) After doing a whole bunch of searching, googleing, etc. I havent been able to find out how to shut down XFCE (while leaving the rest of the system up). The file that has been suggested I use (with references to various locations) doesnt seems to be on my system... (xfsm-shutdown-helper). Its a mystery. I also couldnt find any graphical command to shut down only X (XFCE) but not the system.

So, I have the drivers, to install, but I cant seem to be able to install them...
But I will try your process, that you have mentioned above. Maybe I wont need to install the new driver from nvidia... Thank you again for your timely help.

---

### Post by erginemr on 2008-02-05
I see. In order not to run into serious compatibility issues after a kernel update, you should try to stay away from "NVIDIA*.run" type of installers if possible. However, just in case, to stop the X server, you need to login from another terminal with Ctrl+Alt+F1 (to F6, with Ctrl+Alt+F7 being the graphical desktop) and issue:

```
sudo /etc/init.d/gdm stop
```
to stop the X server, and
```
sudo /etc/init.d/gdm start
```
to start it back.

---

