---
title: "issue with Nvidia display"
date: 2008-11-25
forum: Hardware
---

### Post by jmkinter on 2008-11-25
Hi guys,
Im  new user of linux. 

I have installed Ubuntu 8.10, I have an issue with configuring Display card. 

I have Nvidia 7025/NF630a, Onboard.
 I have installed the Driver for Nvidia "NVIDIA accelerated graphics driver (version 177)[Recommended] ".

After restarting I'm only able to login But after that im geting the message " Input Not Supported " .

I have tried to force the Display mode "800x600" "1024x768", 
But still im geting the same message " Input Not Supported".

Here is my xorg.conf file :

========================
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Modes      "800x600" "1024x768"
    EndSubSection
EndSection

==============

Plz help me to configer the Display setting .. 
Thanks in Advance

Muthu

---

### Post by jmkinter on 2008-11-26
this issue is resolved 
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

thanks for the guys in IRC 

regards,
Muthu

---

