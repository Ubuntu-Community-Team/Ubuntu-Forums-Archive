---
title: "Problems with screen identifing Nvidia, Sager NP5125"
date: 2010-09-18
forum: Hardware
---

### Post by shteren on 2010-09-18
alright, so there is this nice laptop, sager np5125, really great.
it has nvidia gt330m gpu with optimus, ubuntu works just fine, unless you decide you want to try and install nvidia drivers...

lucid lynx is what i use.

the nomal jockey way gives a black screen, so does [this]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html") and [this]("http://ubuntuforums.org/showthread.php?t=1495936") methedos.
so the next step was trying to combine them.

first of all i looked at xorg log, it said (EE) no devices found.

so i configured the device like this:
Busid "PCI:1:0:0" (verified that this is the right adress using lspci)

well this works, sort of, x server did not fail, it loaded fine but showed blank screen (the back light was on though)

so i tried to define the screen manually like in the guides, and this is how the xorg.conf looks like:
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "False"
    Busid    "PCI:1:0:0"
    Option    "ConnectedMonitor" "DFP-0"
    Option    "CustomEDID" "DFP-0: /home/yotam/EDID.bin"
EndSection
```took the EDID from windows.
and this is the error i got in the log.

```
(WW) Sep 18 16:04:28 NVIDIA(GPU-0): Invalid ConnectedMonitor request; request was for 'DFP-0', but
(WW) Sep 18 16:04:28 NVIDIA(GPU-0):     the valid display devices are 'CRT-0'.
(WW) Sep 18 16:04:28 NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
```i have no external monitor connected, don't know where this CRT-0 comes from, and why DFP-0 is not connected...
i tought mybe i'll change the DFP-0 to CRT-0 at xorg.conf, x server went fine but the screen was blank again with back light on.
thats where i got stuck and don't know what else to do. the splash screen comes on, looks a bit distorted but is showing...

last thing i can add is this: from x log when loaded with intel drivers:
```
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1lvd
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1920x1080
```if anyone have any idea how to point x server to the right screen so that it'll show i'll be very glad.

---

### Post by jawaxman on 2010-12-29
I am having a similar issue on a Sager np5135. Has you solved this? Or does anyone else have any thoughts on a solution? Thanks.

---

### Post by shteren on 2010-12-31
:( noppe no solution yet...

apperently the problem is much more complex, optimus uses the igpu to act, it writes to it's buffer and thats how the gpu outputs, you actually needs a driver that can tell the gpu in linux how to do it, it's not just a metter of identifing the screen...

no other optimus laptop have different motherboard wiring and can make some workarounds, but for most thats the case, and untill nvidia jumps in theres not a lot that can be done, unless you're one hell of a drivers writer with a lot of spare time...

---

