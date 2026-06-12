---
title: "openchrome max resolution is 1024x768?"
date: 2012-07-23
forum: Hardware
---

### Post by e3k on 2012-07-23
is it possible to get 1280x1024 working with this driver?

in settings/display i have only 1024x768 also xrandr says this is the min and max resolution.

i did setup a xorg.conf with: 

```
Section "Screen"
        Identifier  "screen0"
        Device      "video0"
        Monitor     "monitor0"
        DefaultDepth 16 
        Subsection "Display"
            Depth      16 
            Modes       "640x480" "800x600" "1024x768" "1280x1024"
        EndSubsection
    EndSection

```but i can get only 1024x768...

graphicscard: 01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

---

### Post by e3k on 2012-07-29
solved by adding **Option "VBEModes" "true"** into the device section


   ```
 Section "Device"
        Identifier  "video0"
        Driver      "openchrome"
        **Option     "VBEModes" "true"**
        Screen 0
    EndSection
```i figured i started to suspect this error: ViaPanelGetIndex: Non-native resolutions are broken

in my /var/log/Xorg.0.log

---

