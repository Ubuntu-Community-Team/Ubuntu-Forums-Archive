---
title: "Brightness Hot Key not working as intended (using an NVIDIA graphics card)"
date: 2016-02-11
forum: Hardware
---

### Post by H5&amp;#2! on 2016-02-11
Hi, I have a laptop with an NVIDIA GeForce 330M graphics card. I have decided to install the latest proprietary drivers for this graphics card (version 340 at the moment), because I intend to install some games onto this laptop. After installing the latest NVIDIA drivers, I wasn't able to use the hotkeys for adjusting the screen brightness. However, I was able to partially resolve this issue following the hints found in [this thread]("http://ubuntuforums.org/showthread.php?t=2190487").

What I did so far was that I just used the command ```
[FONT=courier new]sudo nvidia-settings[/FONT]
``` to create an initial config file and saved it to **/etc/X11/xorg.conf**. Then I used gedit and added ```
[FONT=courier new]Option "RegistryDwords" "EnableBrightnessControl=1"[/FONT]
``` to the device section of the graphics card.

I know that I can read out the maximum brightness value and the actual brightness value as follows:
```
[FONT=courier new]cat /sys/class/backlight/acpi_video0/max_brightness
[FONT=courier new]cat /sys/class/backlight/acpi_video0/actual_brightness[/FONT][/FONT]
```

After rebooting the hotkeys do now basically work, but not as intended. Those are the 2 problems that are still remaining now:

[LIST=1]
[*]According to the first command my maximum brightness value is **11**. However, if I lower the brightness using the hotkey, then the actual brightness value is reduced in steps of **3** (e.g. I have an actual brightness of **11**, then I press the hotkey, then the actual brightness is **8**. If I press the hotkey again, it is reduced to **5**). I would like to have it configured in a way that it is reduced in steps of **1**, because the steps of **3** are actually quite drastic! 
[*]My second problem (and maybe this problem is connected to the first one) is that I can unintentionally 'turn off' my screen with the hotkeys (I don't know how to call it in a better way). For example, when the actual brightness value is **2** and I use the hotkey to lower the brightness (in steps of **3**, obviously), then the actual brightness is reduced in such a fashion that I can't use the system anymore. I then have to enter the terminal pressing Ctrl+Alt+F2 and stop and restart the lightdm service (which returns me back to the login screen). Obviously, this is extremely unhandy and I'd like to resolve that! 
[/LIST]

I have tried to put in every information that I have so far into this post. If you need some further information, then don't hesitate to ask for them. Any help or ideas to resolve my problem is appreciated! Thanks in advance!

Additional info (as I don't know if that helps): With the originally pre-installed nouveau drivers the hotkeys worked as intended. And I can adjust the brightness in steps of 1 using the slider in the energy settings (but I think it would be quite impractical to handle it that way every time)...

---

