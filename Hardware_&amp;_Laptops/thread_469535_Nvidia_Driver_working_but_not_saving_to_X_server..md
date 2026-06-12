---
title: "Nvidia Driver working but not saving to X server."
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by waelaltaqi on 2007-06-10
i installed nvidia-glx driver for UbuntuStudio 7.04 and it's working fine. The problem is that it doesn't save the settings to the X server which means that everytime i logoff or restart i have to set the settings again.  My laptop is Dell Latitude 820 with  GeForce Go 7400 (rev a1) graphic card. 
i issue the following command to start nvidia manager: 
```
sudo nvidia-settings
```
when i try to save my settings, it comes back with the following error message:

```
ERROR: Unable to determine valid vertical refresh ranges for display device
       'LPL' (GPU: GeForce Go 7400)!
ERROR: Failed to add display device 'LPL' to screen 0!
ERROR: Failed to add X screen 0 to X config.
ERROR: Failed to add X screens to X config.
ERROR: Failed to generate an X config file!
ERROR: Unable to determine valid vertical refresh ranges for display device
       'LPL' (GPU: GeForce Go 7400)!


```

i couldn't find a GUI place when i can change the model of the screen... and the driver is not allowing to change the refresh rate to other than 60 MHZ.... can anyone help on this? i would appreciate any help

---

### Post by logos34 on 2007-06-10
Did you run '**sudo nvidia-glx-config enable**' after you installed it?

looks like you'll have to edit it by hand.  
[edit: or run the interactive config 
**sudo dpkg-reconfigure xserver-xorg**]
Consult the documentation for your display/monitor, then add it to X config file

gksudo gedit /etc/X11/xorg.conf

here's the relevant sections of mine:

> Section "Monitor"
    Identifier     **"Insignia"**
   [B] HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 160.0[/B]
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Insignia"
    **DefaultDepth    24**
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

