---
title: "New monitor(Samsung Syncmaster940NW)"
date: 2008-10-04
forum: General Help
---

### Post by Arwen on 2008-10-04
Hello to everyone!
I've just bought this monitor and when I first booted 8.04 it had 1024x768 screen resolution but I want to use the highest it can have(1440x900).
I went to System->Preferences->Screen resolution and chose 1440x900 but when it tried to set it up(you know that window saying "keep new or previous settings") the whole screen was moved to right side leaving a black space on the left side so I didn't let it apply the new resolution.
Do I have to edit xorg.conf? Now it's like that:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

I have already installed nvidia drivers(System->hardware drivers->NVIDIA accelerated graphics driver(latest cards) is checked).My graphics card is NVIDIA 7600GS.
I'm using 8.04.

Thank you for any help,my eyes hurt with 1024x768,it looks sooo wide!

---

### Post by Perfect Storm on 2008-10-04
Open the terminal;

```
gksudo nvidia-settings
```

Set the prefered resolution. Restart X.

---

### Post by Arwen on 2008-10-04
I did it but nothing shows up,just the cursor "blinks" for a second and then ~$ again..

---

### Post by Arwen on 2008-10-04
I did "nvidia-settings" and it said I haven't installed it yet..Shall I do it now or it will change my settings and cause more problems?

---

### Post by howefield on 2008-10-04
from terminal type

```
sudo apt-get install nvidia-settings
```

Then you can use the command advised above.

---

### Post by Arwen on 2008-10-04
:D It worked!
Shall I press "Save to X configuration file"? I only did "Apply"..
Thank you guys!!

---

### Post by howefield on 2008-10-04
You will need to save to the config file, otherwise you will need to reapply every time you boot up.

---

### Post by Arwen on 2008-10-04
I saved it but when I rebooted it had 1024x768 again.I guess I should uncheck "merge with existing file" when saving to xorg.conf?

---

### Post by Arwen on 2008-10-04
Yet it has edited xorg.conf but why doesn't it apply the new resolution when booting?

xorg.conf now:

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900 +0+0; nvidia-auto-select +0+0"
EndSection


---

### Post by Arwen on 2008-10-04
I did "sudo -i" and then "nvidia-settings",unchecked "merge with existing file" but it still doesn't save the changes :-(  There must be a way..

---

### Post by Arwen on 2008-10-07
Bump..
Do I really have to fix the resolution every time I boot up..?
I do save it to xorg.conf but I think it creates a file xorg.conf.backup and uses that,I can't explain why doesn't it save my settings..
Any ideas?I'm freaking out because even ubuntu 7.04 is working flawlessly with the new screen..!

---

