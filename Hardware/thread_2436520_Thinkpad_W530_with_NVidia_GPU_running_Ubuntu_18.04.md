---
title: "Thinkpad W530 with NVidia GPU running Ubuntu 18.04/NVidia 340 - display brightness"
date: 2020-02-07
forum: Hardware
---

### Post by wb0gaz on 2020-02-07
Thinkpad W530 with NVidia GPU running Ubuntu 18.04/NVidia 340 - display brightness only changes at boot-up (it reads the intended brightness from the settings area and takes on that brightness.) Once the machine is running, subsequent changes to brightness SETTING are saved in settings dialog, however, the actual brightness in the hardware does not change from the boot-up brightness (as set prior to boot-up.)

100% repeatable.

Where can I go for advice to resolve?

---

### Post by thehipho on 2020-02-11
You can use nvidia-settings to change brightness?

And in terminal to write the current X server configuration to ~/.nvidia-settings-rc

```

nvidia-settings --rewrite-config-file

```

---

### Post by wb0gaz on 2020-02-12
Thanks for the reply!

There doesn't seem to be any means to adjust (backlight) brightness in nvidia-settings GUI.

I was able to execute the nvidia-settings command you recommend; the file contents are show below.

#
# /home/(user name)/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Wed Feb 12 11:36:26 2020
#

# ConfigProperties:

RcFileLocale = C
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
UpdateRulesOnProfileNameChange = Yes

# Attributes:

[DPY:LVDS-0]/RedBrightness=0.000000
[DPY:LVDS-0]/GreenBrightness=0.000000
[DPY:LVDS-0]/BlueBrightness=0.000000
[DPY:LVDS-0]/RedContrast=0.000000
[DPY:LVDS-0]/GreenContrast=0.000000

---

### Post by thehipho on 2020-02-12
> 
Thinkpad W530 with NVidia GPU running Ubuntu 18.04/NVidia 340 - display  brightness only changes at boot-up (it reads the intended brightness  from the settings area and takes on that brightness.) Once the machine  is running, subsequent changes to brightness SETTING are saved in  settings dialog, however, the actual brightness in the hardware does not  change from the boot-up brightness (as set prior to boot-up.)

There doesn't seem to be any means to adjust (backlight) brightness in nvidia-settings GUI.


The brightness settings should be at color correction in nvidia-settings GUI, see attached screenshot.

---

### Post by wb0gaz on 2020-02-13
I found the settings you recommended - they do adjust brightness/contrast (I think by adjusting the LCD rather than the backlight intensity, but still it is having a change), however, after reboot the settings are restored back to the native ubuntu settings dialog (which I think it adjusting the backlight intensity), which itself cannot be adjusted during operation, only in advance of the next start-up. Perhaps this is the intended design of the system? If I can find a command line method to change the nvidia settings (instead of the GUI for Nvidia), that would probably suffice.

---

### Post by thehipho on 2020-02-14
You tried with xbacklight?

```
sudo apt install xbacklight

```

---

### Post by wb0gaz on 2020-02-14
Just installed and tried xbacklight --- it doesn't read current backlight setting and doesn't change the current setting (=any response to the command is just another command prompt.) I looked at xrandr, however, it's brightness function seems to work like the nvidia brightness control - changing the LCD transmission, but not altering the backlight intensity (xrandr tells you to go to xbrightness for that purpose.)

So, as yet unsolved, but I do appreciate the advice!

Dave

---

### Post by thehipho on 2020-02-16
May I ask why you're using NVidia 340, this ppa has the latest  stable release nvidia-390 or nvidia-430 depending on your video card?

```
sudo add-apt-repository ppa:graphics-drivers/ppa 
sudo apt-get update
```

---

