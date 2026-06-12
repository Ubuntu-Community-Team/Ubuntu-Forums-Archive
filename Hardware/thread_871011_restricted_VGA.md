---
title: "restricted VGA"
date: 2008-07-26
forum: Hardware
---

### Post by tejaka on 2008-07-26
Hi

Just installed Ubuntu on a pc with a nvidia 7 series VGA.

I downloaded driver directed by ubuntu and now says that it’s restricted driver. My resolutions is only 640x480 and I can not move forward than that.

So now don’t I have a solutions than unplugging VGA card and running from on board chip, if want to continue with ubuntu? 

Any help please…

Thanks.

---

### Post by brokenLockpick on 2008-07-26
I had alot of problems with my 7800GT it turned out to be an easy fix. I ended up trying a VGA cable rather than the DVI cable I had been using and the monitor was recognized as being able to use its full resolution. Also when I was using the default VESA drivers a quick edit to the xorg.conf file was able to sort things out. 

The xorg.conf file is located in /etc/X11/xorg.conf, if I had a guess I would bet that in your file it has your monitor listed as plug and play, that's what mine said when I was stuck at 640x480.

---

### Post by tejaka on 2008-07-26
no in my case this is how it shows in /etc/X11/xorg.conf...

```


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
```

is there any other changeable file or something to get the display resolution i want?

thanks in advance.

---

### Post by brokenLockpick on 2008-07-26
> **tejaka said:**
> is there any other changeable file or something to get the display resolution i want?

Not that I'm aware of. But there may be. Here's my entries for that file they have a bit more info on them maybe it'll help.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    ModelName      "NUL"
    HorizSync       31.5 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
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
    BoardName      "GeForce 7800 GT"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GT"
    BusID          "PCI:2:0:0"
    Screen          1
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
    Option         "metamodes" "CRT: 1280x1024 +0+0; CRT: nvidia-auto-select +0+0"
EndSection

Section "Screen"

    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TVOutFormat" "Component"
    Option         "TVStandard" "HD720p"
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 1280x720 +0+0"
EndSection


```

my setup is probably a bit more complicated than yours but I noticed what seems to be alot of details missing. Though it's been quite  while and I forget exactly which things I added by hand and which were automatic. I do remember having to force my flat panel to 720p and needing to look up the vert and horiz settings on the monitor manufacturers website.

---

### Post by tejaka on 2008-07-26
in my file there is nothing like 640X480 or anything about resolution.

i posted everything i could understand as it's about VGA and monitor.

so now it's really confusing...
i could try as yours if the card was the same, but i'll try to change it and see what will be happens.

my UGA is Geforce 7300LE.

---

### Post by tejaka on 2008-07-26
well i'm really confusing with editing within this little screen....

question remains the same...and i knows little about linux yet...
can you please tell me how to change that file's permission to be edited too... 

tried with GUI and could't find a way to do that...so is there any command to change it's editing permissions?

Thanks

---

### Post by brokenLockpick on 2008-07-26
> **tejaka said:**
> tried with GUI and could't find a way to do that...so is there any command to change it's editing permissions?
Thanks

To give the gui permissions temporarily, open a terminal.

```
sudo nvidia-settings
```

then type your password when prompted it'll bring up the gui and the app will have permissions to write to the xorg.conf file. Probably better to try that first. I always leave manual editing as a last resort.

---

### Post by brokenLockpick on 2008-07-26
I should also mention that if the GUI fails to fix it and you have to start editing the file manually. Start terminal and type 
```
sudo gedit /etc/X11/xorg.conf
``` 
Which will bring up the text editor and the file in question.

Good luck.

---

### Post by Feenix3k on 2008-07-29
My xorg.config is blank

---

### Post by brokenLockpick on 2008-07-29
> **Feenix3k said:**
> My xorg.config is blank

did you use "/etc/X11/xorg.conf"(correct) or "/etc/X11/xorg.config"(incorrect)

because if you type in the name of a file that doesn't exist it'll just open a blank file

---

### Post by tejaka on 2008-07-30
sadly even my file opens blank...though there is the file i gave above in that location, and though i typed command right...

now this problem is a headache and i have some another import things to configure with Linux such as setting up network etc... somehow it runs now at least under 800x600, until i solve other important matter that will be enough...i'll get back to you when i could free my mind to get back to this problem...


thanks in advance brokenlock...

---

