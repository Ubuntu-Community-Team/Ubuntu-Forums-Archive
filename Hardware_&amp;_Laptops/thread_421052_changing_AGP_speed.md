---
title: "changing AGP speed?"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by f4hy on 2007-04-24
Hi. I need a way to set the AGP speed from 8x to 4x. I am running fiesty with a ATI 9600XT. Running 3D apps crash the machine if in 8x mode. This has been verified by the ATI windows drivers which you to set the AGP mode. I am using FGLRX and it does not appear to have something like that.
I have set it in the bios to be agp 4x. However this does not seem to stick becuase if I do
```
grep "x mode" /var/log/kern.log
```
I get lines like this
```
Apr 23 15:04:51 f4hy-desktop kernel: [   78.175779] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
```
also running the ATI Cataylst control center reports "Bus Setting 8x"

I do not know how to set the AGP mode. I tried editing /etc/X11/xorg.conf to have the following under the device section:
```
Section "Device"
        Identifier  "ATI Technologies Inc RV350 AR [Radeon 9600]"
        Driver      "fglrx"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "no"
        Option "UseInternalAGPGART" "yes"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection
```

Unfortunatly if I check in /var/log/Xorg.0.log it looks like it is no longer supported to set the speed in xorg.conf
```
f4hy@f4hy-desktop:/var/log$ cat Xorg.0.log |grep AGPFast
(WW) fglrx(0): Option "AGPFastWrite" is not used
f4hy@f4hy-desktop:/var/log$ grep -B 5 AGPFast Xorg.0.log
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                30 128x128 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "AGPMode" is not used
(WW) fglrx(0): Option "AGPFastWrite" is not used

```

Does anyone know how to set the AGP speed or AGP fastwrite?
Is this a fglrx issue that is just not supported by their driver, or is it set somewhere else?

---

### Post by BungaMan on 2007-04-24
isn't there something like
man fglrx
which would list you all the options?

Option "AGPMode" is available when you use ati or radeon driver.  You could always try to use radeon and check performance.  Maybe 8x works fine with the radeon driver.

and aren't you supposed to state no for UseInternalAGPGART?  look up some info on it.

---

### Post by f4hy on 2007-04-24
There is no man entry for fglrx. If anyone knows where I can find documentation about weather it can set this option please let me know. Even if the answer is that it can not be set, I would at least like to know.

I have tried both settings for UseInternalAGPGART. I do not know exactly what that setting does, could anyone clarify for me?

8x does not work with either driver, or drivers for other OSes. The card fails when in 8x mode doing anything graphical.

---

### Post by Erlander on 2007-04-25
I would have changed it in bios.

Rob

---

### Post by f4hy on 2007-04-25
I already did change it in the bios. Thats why I was surprized that it was being set back to 8x. The drivers are overridding that setting.

---

