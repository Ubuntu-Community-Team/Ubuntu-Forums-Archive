---
title: "Resolutions other than native on inspiron 1720"
date: 2008-06-05
forum: Hardware
---

### Post by smani on 2008-06-05
Hello,
I have the following little problem: Ubuntu (8.04) correctly recognizes the native resolution of my screen (1920x1200), but does not allow me to select any other resolution... I tried some of the different suggestions over the internet, most of them ended up with my X-Server not starting anymore... One reason why I would like to be able to use other resolutions is that currently in wine full-screen applications will only run at 1920x1200, which, in the case of games, kills my gpu :D
Does anyone know how to add other resolutions?
Thanks for any inputs!
Cheers
smani

---

### Post by kpkeerthi on 2008-06-05
If your 1720 comes with nvidia GPU, the easiest way to change resolution is by using nvidia-settings utility.

1. Install nvidia restricted driver (Hope you've done that already)
2. Install nvidia-settings
```
sudo aptitude update && sudo aptitude install nvidia-settings
``` 
3. Applications -> System Tools -> Nvidia Settings. If you can find there, just type **nvidia-settings** in a terminal window.
4. Change the resolution using the GUI.

---

### Post by smani on 2008-06-09
Thanks for your reply. Unfortunately also in the nvidia gui the only resolution available is the native 1920x1200. Am I missing something?

---

### Post by smani on 2008-06-29
Right, so after doing some research I found out that edid (who should be responsable for reading the "technical data" from the display, such as resolutions, syncs and so on) failed, no idea why actually...
Anyway, I ended up in using modelines, here is what I did in case it may be to any use to someone else:

In terminal, execute:

```
gtf x-res y-res refreshrate
```

where you need to replace the arguments with the ones you need, i.e.

```
gtf 1440 900 59
```

Next, edit the xorg.conf file and add the output of the previous command to the Monitor section, in my case it looks like this

```
Section "Monitor"
    Identifier     "Configured Monitor"
    # 1440x900 @ 59.00 Hz (GTF) hsync: 54.93 kHz; pclk: 104.58 MHz
    Modeline "1440x900_59.00"  104.58  1440 1520 1672 1904  900 901 904 931  -HSync +Vsync
EndSection
```

Also note that I added the resolution in the Screen section, which looks like this

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "ModeValidation" "NoDFPNativeResolutionCheck"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200" "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200" "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200" "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200" "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200" "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1440x900"
    EndSubSection
EndSection
```

Restart X and you should be able to select the newly added resolutions in "Screen Resolutions" or in "NVIDIA X Server Settings".

Final Note: I could not find any specifications for the LCD panel of my laptop, therefore I am not sure if the refresh-rate I used is the best one - if anyone has a cleaner approach, I'd be glad to hear it.

Cheers,
smani

---

