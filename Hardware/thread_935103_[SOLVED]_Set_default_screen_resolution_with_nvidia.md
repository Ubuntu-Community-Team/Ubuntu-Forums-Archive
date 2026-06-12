---
title: "[SOLVED] Set default screen resolution with nvidia card"
date: 2008-10-01
forum: Hardware
---

### Post by pxhai on 2008-10-01
Recently I bought a widescreen 19' LCD (1400 x 900) and threw away the old 17' CRT. But when Xserver starts, it always sets resolution at 1280 x 960. I have to use 'Nvidia X server settings' to set to 1400x900, quite annoying. I tried to stop Xserver (/etc/init.d/gdm stop), alter file 'xorg.conf' to the configuration that Nvidia Xserver settings generates in option 'Save to X configuration file', but Xserver just failed, cannot change resolution, i have to restore the old xorg.conf.
Can you help me, please? Manually changing the resolution is so troublesome.
Thanks,
pxhai

PS: I installed nvidia-glx restricted driver

---

### Post by milton1 on 2008-10-01
your xorg.conf file should have a line containing resolutions. Make the first entry on that line 1400 x 900. This should then be the default.

---

### Post by pxhai on 2008-10-01
i made change in the section "screen"

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1400x900" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```
but no luck

---

### Post by pxhai on 2008-10-02
ok, it works now. Need to do it by force: start from liveCD and change the xorg.conf with the content nvidia settings generated, and then its fine.

---

