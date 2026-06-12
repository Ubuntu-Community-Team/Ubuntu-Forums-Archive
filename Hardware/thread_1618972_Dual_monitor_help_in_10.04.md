---
title: "Dual monitor help in 10.04"
date: 2010-11-11
forum: Hardware
---

### Post by joshuajon on 2010-11-11
So I've been at this for a day and a half now and I've still only got one (and a half) monitor setup.  

I have two graphics adapters shown here in the output of 'lspci |grep VGA'

> 
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
01:04.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)I have tried to set up a second monitor with Xinerama using the instructions found here: [http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)  

The relevant sections of my modified xorg.conf looks like this:

> Section "Device"
    Identifier    "Configured Video Device"
    Screen 0
EndSection
Section "Device"
        Identifier      "PCI"
    BusID    "PCI:1:4:0"
    Driver    "nv"
    Screen 1
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Monitor"
        Identifier      "PCImon"
EndSection


Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "Screen"
        Identifier      "Screen2"
        Monitor         "PCImon"
        Device          "PCI"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen    0 "Default Screen"
    Screen  1 "Screen2" RightOf "Default Screen"
    Option "Xinerama" "true"
EndSectionI know that the second card and monitor works.  If I set the PCI video card as primary in the BIOS I can boot with the other monitor.  

When i start X with the onboard card as the primary driver and this configuration the second monitor comes on but shows only bizarre vertical green lines.  

What am I missing?

---

### Post by dino99 on 2010-11-11
you can follow this example to build yours

[http://ubuntuforums.org/showpost.php?p=9604915&postcount=2](http://ubuntuforums.org/showpost.php?p=9604915&postcount=2)

---

### Post by joshuajon on 2010-11-11
That looks awfully similar to what I've done.  Here is a new xorg.conf based on the example you linked:

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    Screen      1  "Screen1" RightOf "Screen0"

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
EndSection


Section "Device"
    Identifier     "Device0"
    BusID          "PCI:00:02:0"
    Screen 0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nouveau"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:01:04:0"
    Screen 1
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
EndSection



I'm still stuck with the same problem though.  The first device and monitor work, the second shows vertical green lines.  When I checked the Xorg logs I see this
> 
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) Option "Xinerama" "1"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled


which makes me hopeful that I'm close, but I still see only these damn green lines.  Any other suggestions?

---

### Post by joshuajon on 2010-11-11
Yet more hopeful info.  The command "lshw -C display" returns the following

> *-display               
       description: Display controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fcf00000-fcf7ffff ioport:c800(size=8) memory:d0000000-dfffffff(prefetchable) memory:fcf80000-fcfbffff
  *-display
       description: VGA compatible controller
       product: NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       version: 15
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
       resources: irq:16 memory:fd000000-fdffffff memory:fa000000-fbffffff(prefetchable) memory:fe000000-fe00ffff(prefetchable)


So what gives?

---

### Post by joshuajon on 2010-11-11
I added the monitor refresh and sync to the xorg.conf and that didn't help.  I noticed in that lshw output that both display adapters have irq of 16.  Could this be the problem?  The second monitor is now showing green lines even with xorg.conf failsafe in use.  I don't get it!

---

### Post by joshuajon on 2010-11-12
Anybody? Anybody? Bueller?

---

