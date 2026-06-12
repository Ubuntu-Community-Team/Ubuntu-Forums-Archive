---
title: "G-sync not working on Freesync monitor."
date: 2019-04-12
forum: Hardware
---

### Post by ambawell on 2019-04-12
I am having screen tearing and shuttering issues on a Freesync monitor with a Nvidia 1660 Ti graphics card. I have Nvidia 418.56 driver installed with all settings to use G-sync compatible monitor in the nvidia-settings. Everything looks in the nvidia-settings however none of the browsers and flight simulators utilize it in Ubuntu 19.04 and 18.10. but is works in Windows 10. I get much less shuttering and no tearing in Windows 10.

Hardware
AMD RYZEN 5 2600 YD2600BBAF BOX CPU
MSI B450M Pro-VDH Mother board
T-FORCE TLRED48G3000HC16CDC01 8GB memory
GIGABYTE GeForce GTX 1660 Ti OC 6G Graphics Card
INSIGNIA NS-PMG278 Black 27" 144Hz 2K QHD 2560 x 1440 1m monitor

Flight Simulators
X-Plane 10 and 11
Silentwings 10.1

Even though the nvidia-settings look like it works nothing in Linux uses G-sync compatible mode.

Has anyone else had this issue and is there a fix?

---

### Post by #&amp;thj^% on 2019-04-12
Out of curiosity have you tried a lower version for the nvidia-driver? (410-415)
I have always had a great experience with the Nvidia drivers except for "nvidia-driver-418" I couldn't get rid of it fast enough.;)
Also I have at times had to add "nvidia-drm.modeset=1" to kernel parameter.
Also can you show us the return from:
```
nvidia-settings -q all | grep -i -e currentmetamode -e gsync -e vblank -e flipp -e visual
```

---

### Post by ambawell on 2019-04-12
No I have not tried an older driver. The trouble is that my card just got released Jan 22 2019. The oldest drive that lists support for my card is 418.43. Maybe I can find the first beta driver and try that.

This the output from:  nvidia-settings -q all | grep -i -e currentmetamode -e gsync -e vblank -e flipp -e visual

Attribute 'SyncToVBlank' (msi:0.0): 1.
    'SyncToVBlank' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'SyncToVBlank' can use the following target types: X Screen.
  Attribute 'AllowFlipping' (msi:0.0): 1.
    'AllowFlipping' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'AllowFlipping' can use the following target types: X Screen.
  Attribute 'AllowGSYNC' (msi:0.0): 1.
    'AllowGSYNC' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'AllowGSYNC' can use the following target types: X Screen.
  Attribute 'ShowGSYNCVisualIndicator' (msi:0.0): 1.
    'ShowGSYNCVisualIndicator' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'ShowGSYNCVisualIndicator' can use the following target types: X Screen.
  Attribute 'ShowVRRVisualIndicator' (msi:0.0): 1.
    'ShowVRRVisualIndicator' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'ShowVRRVisualIndicator' can use the following target types: X Screen.
  Attribute 'ShowGraphicsVisualIndicator' (msi:0.0): 0.
    'ShowGraphicsVisualIndicator' is a boolean attribute; valid values are: 1 (on/true) and 0 (off/false).
    'ShowGraphicsVisualIndicator' can use the following target types: X Screen.
  Attribute 'CurrentMetaModeID' (msi:0.0): 50.
    'CurrentMetaModeID' is an integer attribute.
    'CurrentMetaModeID' can use the following target types: X Screen.
  Attribute 'CurrentMetaMode' (msi:0.0): id=50, switchable=yes, source=xconfig :: DPY-2: nvidia-auto-select @2560x1440 +0+0 {AllowGSYNCCompatible=On, ViewPortIn=2560x1440, ViewPortOut=2560x1440+0+0} 
    'CurrentMetaMode' is a string attribute.
    'CurrentMetaMode' can use the following target types: X Screen.

---

### Post by #&amp;thj^% on 2019-04-12
The option here is AllowGSYNC. The -q option can show its current state:
Try this and just to be be sure we have optimal results (Or at the very least a chance)  reboot after,
To toggle it, use the -a flag:
```
nvidia-settings -a AllowGSYNC=1
```
This should toggle GSYNC on.

To Revert use:
```
nvidia-settings -a AllowGSYNC=0
```
To toggle off.
EDIT: Dose your manual/box mention any of this?
packaging does note "OpenGL 4/5" support... There isn't OpenGL 5.0, at least not yet. If it was intended for OpenGL 4.5, they have been supporting OpenGL 4.6 for a year and a half already.

---

### Post by ambawell on 2019-04-13
Thanks for your help.

I finally found out what was keeping Freesync from working.
It is the Xfce4 compositor in Window Manager Tweaks. Turn it off and even the games that do not use Freesync run much smoother.
With it off Freesync works in my X-Plane Flight Simulators.

---

