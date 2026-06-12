---
title: "Using an external monitor"
date: 2008-10-25
forum: General Help
---

### Post by rmcellig on 2008-10-25
I hooked up an external monitor to my laptop but I don't see anything on it. Is there something I have to do in Ubuntu 8.04 to get it working??

---

### Post by Don S on 2008-10-25
Your graphics card driver should have a GUI configuration program. For example, Nvidia's is nvidia-settings.

If you have an Nvidia card, try and run:
```
sudo nvidia-settings
```

In the X Server Display Settings, you can configure your screen setup. To save for next setup, press the "Save to X Configuration File".

Alternatively, if you know your way around a configuration file, you can edit the /etc/X11/xorg.conf file manually, to add a secondary monitor. It's different for each graphics card, how to set up the secondary monitor, but my current setup is like this:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: 320x240 +960+784"
EndSection
```

(Notice that I set my primary screen to 320x240 in the lower left corner, because it's actually broken, so I only use the secondary CRT monitor - this is probably not what you're looking for.)

---

### Post by rmcellig on 2008-10-25
I don't seem to have the Nvidia-settings GUI. Where can I download it from?

---

### Post by rmcellig on 2008-10-25
Found it. After installing it, how can I put it in my Applications menu?

---

### Post by rmcellig on 2008-10-25
Actually, I would like to put the nvidia-settings into my System Preferences for easy access. How can I do this?

---

### Post by Don S on 2008-10-25
In System -> Preferences -> Main Menu, there's an option to create menu items. Just create a new item in whichever menu you want, and set it to use the command "sudo nvidia-settings".

---

### Post by rmcellig on 2008-10-25
Thanks! Seeing how I am new to Linux, one of the stumvling blocks I came across was what to insert where it says command. How would I know what to type in here if I ever wanted to create a new launcher for example. Where do you find these commands?

Thanks!!

---

### Post by Don S on 2008-10-26
Basically, in the command, it is the same type of command, as you would execute in a terminal. Usually, you wouldn't have to create a menu shortcut, as they are normally automatically included in packages, but if you want to create a shortcut for something, the easiest way to figure it out, would be to search the web or ask on these boards, as there are numerous of different parameters for each program and a lot of different programs. But, eventually, after some time, learning various commands comes naturally and more intuitively than pressing a button.

:)

---

