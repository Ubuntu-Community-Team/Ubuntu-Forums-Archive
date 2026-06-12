---
title: "Screen resolution and KVM switch"
date: 2008-10-12
forum: General Help
---

### Post by Moepi on 2008-10-12
Hello,
I'm using multiple Ubuntu boxes connected to a single LCD monitor which is connected through a KVM switch. The screen resolution is correctly detected and set if the monitor is active while one of the boxes starts. However, if the monitor is active on another box the one currently starting is unable to detect the proper settings and chooses a poor resolution.
I tried to bypass the autoconfiguration by setting the approprate modeline in /etc/X11/xorg.conf - no success. I also tried to use 915resolution (fix for Intel based graphic cards) without luck.

Does anyone have an idea how to tell the X-server to use one specific resolution and refresh rate regardless if (or which) display is currently connected?

Thanks very much in advance!

---

### Post by orbish on 2008-10-12
I can tell you what's causing the problem.  8.04+ uses your monitor's EFID to detect your monitor, this is so everything "just works."  The problem is, with a KVM Switch, you lose the EFID data.

What I'm doing right now is just going from computer to monitor.  I haven't tried hooking my KVM back up, but I suspect the settings will be lost when I do.  I'm posting this to give you some insight.

The best way to rig this, to my estimation, is hooking up your monitor directly.  Then let X find all your settings.  Once this happens, find a way to tell Xorg to keep the settings.  (Xorg doesn't rely on xorg.conf much anymore).

Hope this helps.

---

### Post by Moepi on 2008-10-12
> **orbish said:**
> I can tell you what's causing the problem.  8.04+ uses your monitor's EFID to detect your monitor, this is so everything "just works."  The problem is, with a KVM Switch, you lose the EFID data.

What I'm doing right now is just going from computer to monitor.  I haven't tried hooking my KVM back up, but I suspect the settings will be lost when I do.  I'm posting this to give you some insight.

The best way to rig this, to my estimation, is hooking up your monitor directly.  Then let X find all your settings.  Once this happens, find a way to tell Xorg to keep the settings.  (Xorg doesn't rely on xorg.conf much anymore).

Hope this helps.

Yeah I suspected something like this. Unfortunately I found no possibility to tell X to keep the settings once they are detected. Either these settings are saved somewhere outside the xorg.conf or are completely rewritten in RAM every time the system starts up...

---

### Post by orbish on 2008-10-12
> **Moepi said:**
> Yeah I suspected something like this. Unfortunately I found no possibility to tell X to keep the settings once they are detected. Either these settings are saved somewhere outside the xorg.conf or are completely rewritten in RAM every time the system starts up...

there is a file ~/.config/monitors.xml that holds monitor information... you could create a backup file of it named monitors.xml.good and a small bash script to copy it over after X starts, but that's the only file i know of that holds the information

---

### Post by Moepi on 2008-10-12
> **orbish said:**
> there is a file ~/.config/monitors.xml that holds monitor information... you could create a backup file of it named monitors.xml.good and a small bash script to copy it over after X starts, but that's the only file i know of that holds the information

Such a file does not exist on my systems. I also searched for the actually configured resultion in any file by typing ```
find / * | cat | grep 1920 
``` without success... :(

---

### Post by orbish on 2008-10-12
I found this: [https://answers.launchpad.net/ubuntu/+source/hal/+question/1017](https://answers.launchpad.net/ubuntu/+source/hal/+question/1017)

I haven't tried it as I'm walking 3 people through some problems at the moment... also, every time I tried editing xorg it reset on boot.  i don't really know how to do what it says but i'll tinker with it in a bit.

---

### Post by Moepi on 2008-10-12
According to [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy) the settings which used to reside in xorg.conf are noe automatically detected during startup - ok, we already suspected that.

I tried to manually reconfigure the xorg.conf, I made some errors, X wouldn't start and offered me a setup assistant. I used it and made the best guesses I had (graphics card driver, screen resolution and so on) and it worked (almost). I got a xorg.conf with "old fashioned" layout and the system worked normally.
However the problem regarding the KVM still exists.

If the system wouldn't start up if I make consciously errors in the config I would say, that it is still ignored... :(

I also took these posts into account: [http://ubuntuforums.org/archive/index.php/t-480816.html](http://ubuntuforums.org/archive/index.php/t-480816.html)

Still no success :(


Update:
I figured out, that the following option in the Monitor section prevents Ubuntu from selecting the correct resolution although the monitor is currently active on the system:
```

Option "NoDDC"

```
Therefore I assume, that if I succeed to manually supply the DDC information my problem should be resolved. However, I was not able to figure out how to accomplish this yet...

---

### Post by orbish on 2008-10-13
Just received this from an Xorg developer.

> I have an IOgear extreme KVM switch that isn't passing along my EFID
> settings to xorg.  I know this isn't a problem with Xorg and isn't
> your problem.  But I need a solution, so here's what I'm thinking...
> When I plug my monitor in, all is right with the world, so how do I
> keep it that way.  In other words, how can I either turn of Xorg
> autodection of the monitor, or just freeze the configuration
> altogether.

If you write a monitor section in xorg.conf, we'll respect it.  If we
don't, it's a bug, and we want to know about it.

>   When I make changes to xorg.conf, they are reset at boot.

That really shouldn't happen.  X doesn't ever write back to the config
file [*], so this is likely to be something else in your OS mucking with
you.

[*] - fglrx will, sometimes.  But it doesn't look like you're running
fglrx.




So I'll be fiddling with this all morning and give updates if I tackle it.

---

### Post by orbish on 2008-10-13
update:

OK, at xorg guy's suggestion, I wrote in the section of my xorg.conf's monitor section.  Rebooted with the KVM hooked back up and the resolution did not stick.  I also added your noddc option, rebooted to no avail, here's the current Xorg.conf:

```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"HP LP2465"
	Modeline	"1920x1200" 193.16  1920 2048 2256 2592  1200 1201 1204 1242 -hsync +vsync
	Option		"NoDDC"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"HP LP2465"
	Device		"Configured Video Device"
EndSection
```



I should also mention the modelines were not googled but found in /var/log/Xorg.0.log.

---

### Post by ubufase on 2008-11-11
Hi everyone,

first, thank you for leading me to this solution.

I managed to solve my problem with the KVM by using the nvidia x server settings,
```
sudo nvidia-settings
```

after it changed the resolution I saved the changes to the xorg.conf and this is how it looks now(generated by nvidia x server settings):
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "BenQ T201W"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0; 1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

this might not help if you don't have nvidia card (I don't know if other cards have similar tools). but I think that if you configure the "Device", "Monitor", and "Screen" sections correctly, the xorg.conf will not reset when you restart.

---

