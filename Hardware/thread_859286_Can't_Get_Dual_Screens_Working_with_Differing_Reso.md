---
title: "Can't Get Dual Screens Working with Differing Resolutions"
date: 2008-07-14
forum: Hardware
---

### Post by whitethunder922 on 2008-07-14
I'm running 8.04 2.6.24-19-generic on a Dell Latitude D820 laptop with an Nvidia GeForce Go 7300 and an external Dell monitor. The laptop screen maxes out at 1920x1200 and the external monitor goes to 1280x1024. I'm having a hard time getting the resolutions and configurations just right. I've tried using nvidia-settings but it always complains that I'm not using the Nvidia drivers, which is a lie because I used envyng to install them. Even if I use the Hardware Drivers app to install proprietary drivers, it STILL complains that I'm not using the Nvidia driver. So that's why I've resorted to manually editing the xorg.conf file directly. If anyone knows how to get the GUI tool working, that would be ideal. Otherwise, could someone let me know how to modify my xorg.conf file?

I have the external monitor as a secondary monitor so that I can take my laptop away from the docking station and still have it work fine. The monitor is to the right of the laptop screen. Right now it seems to think that the external monitor is the primary monitor because that's where the login screen appears (with the laptop screen being blank). The laptop screen ends up being rightof the external screen with some amount of unviewable desktop space inbetween. So if I move my mouse pointer off the right edge of the external monitor, it disappears for a second, but when I keep dragging it to the right, it eventually appears on the left edge of the laptop screen. Additionally, the laptop screen's resolution is not set right. I think it's at 1280x1024 as well. Any ideas what I need to do to the xorg.conf file below? Thanks!

P.S. If any of you looking at this are wondering "why did you...(fill in blank)", it's because I hardly know what I'm doing with this stuff.


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Mouse1"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "bitmap"
    Load           "ddc"
    Load           "dri"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

... (omitted mouse/keyboard info)

#Laptop display
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 77.0
    Option         "DPMS"
EndSection

#External monitor
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Dell 1907FPVt"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 77.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7300"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7300"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1920x1200 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by ssm360 on 2008-07-14
I got it working using my 8800GT and the proprietary drivers with my HDTV at 1360x768 in and my monitor at 1680x1050 on my desktop pc.

Install the nvidia-settings tool from the synaptic package manager after u install the driver, when installed run terminal type in "sudo nvidia-settings", all thats left 2 do is tweak your settings and when u save 2 the xorg.conf and restart X u should have duel-screen.

---

### Post by whitethunder922 on 2008-07-15
Thanks for the suggestion but I still get the error "You do not appear to be using the Nvidia X driver..." Any idea how to get around that?

---

### Post by ssm360 on 2008-07-15
If ur talking about were ur mouse pointer disappears when between screens, u could try using the nvidia settings 2 select your res, then click the save to X configuration file, when the save window pops up click show preview and add the text to the xorg.conf file manually, other than that im not sure.

---

### Post by whitethunder922 on 2008-07-15
I'd love to do that but like I said, nvidia-settings doesn't work because it thinks I'm not using an Nvidia driver, which is false. How do I get it to realize I'm using the Nvidia driver?

---

### Post by dannyboy79 on 2008-07-15
> **whitethunder922 said:**
> I'd love to do that but like I said, nvidia-settings doesn't work because it thinks I'm not using an Nvidia driver, which is false. How do I get it to realize I'm using the Nvidia driver?

post the output of this command:

dmesg | grep NVIDIA

---

### Post by whitethunder922 on 2008-07-15
[   27.319649] nvidia: module license 'NVIDIA' taints kernel.
[   27.570374] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008

---

### Post by dannyboy79 on 2008-07-15
> **whitethunder922 said:**
> [   27.319649] nvidia: module license 'NVIDIA' taints kernel.
[   27.570374] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008

i have a 

VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

and I used Envy as well and it installed 169.12

NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008

I would say you're using an older nvidia driver by the looks of it. try to uninstall envy, download the latest envy and first uninstall everything nvidia* through synaptic (you might be using the restricted modules driver), use vesa for the time being if you need a GUI, then install envy and install the nvidia driver, it should pick up a newer one than 96.43.05.

---

### Post by whitethunder922 on 2008-07-15
If I install the newer driver it doesn't work with this card. I wrestled with the 169 for a while (also trying nvidia-settings when that driver was installed with the same results) but as soon as I installed the 96.43.05 driver, everything worked really well. I messed with my xorg.conf file enough now that I got it all to work properly but nvidia-settings still refuses to believe I'm using an Nvidia driver, so all changes have to be made textually. Any other ideas how to get nvidia-settings to work or is it not possible with this driver? Thanks.

---

### Post by ssm360 on 2008-07-15
have u tried installing the 173.14.09 driver from the nvidia website, i have never tried it cuz i don't know ubuntu that well and dont want 2 muck it up,

[http://www.nvidia.com/object/linux_display_ia32_173.14.09.html](http://www.nvidia.com/object/linux_display_ia32_173.14.09.html)

---

### Post by doas777 on 2008-07-15
forgive me for jumping in late, but it looks like Xinerama is on (value of 1). I believe that you need to turn Xinerama off to use dual Xscreens. just a thought from a n00b

---

### Post by ssm360 on 2008-07-15
> **doas777 said:**
> forgive me for jumping in late, but it looks like Xinerama is on (value of 1). I believe that you need to turn Xinerama off to use dual Xscreens. just a thought from a n00b

i dont think so cuz whitethunder922 can get dual screen but the res is mucked up and the nvidia settings dont work.

---

