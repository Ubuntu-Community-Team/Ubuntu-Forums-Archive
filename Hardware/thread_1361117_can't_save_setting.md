---
title: "can't save setting"
date: 2009-12-21
forum: Hardware
---

### Post by aminmatrix on 2009-12-21
i use Ubuntu 9.10
 nvidia GForce 5200
i installed the driver and every thing is ok
but i can't "save to X configuration file " he shows "failed to parse existing X config file '/etc/X11/xorg.conf'!
every time i reboot my pc i have to chage the resolution from 640x480 to 1024x768 using nvidia X server setting

---

### Post by jocko on 2009-12-21
That's because you need to run nvidia-settings with sudo to get permission to write to /etc/X11/xorg.conf. Type this in a terminal:
```
gksudo nvidia-settings
```

---

### Post by aminmatrix on 2009-12-21
> **jocko said:**
> That's because you need to run nvidia-settings with sudo to get permission to write to /etc/X11/xorg.conf. Type this in a terminal:
```
gksudo nvidia-settings
```


itshows this error message
```

ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 49 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


```

---

### Post by aminmatrix on 2009-12-21
```

root@ubuntu:~# gksudo nvidia-settings

ERROR: Cannot open display 'ubuntu:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 20 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 21 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 22 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 23 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 24 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 25 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 26 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 27 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 28 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 29 of configuration
       file '/home/amine/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 30 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 31 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 45 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 46 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       47 of configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       48 of configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 49 of
       configuration file '/home/amine/.nvidia-settings-rc' (no Display
       connection).

root@ubuntu:~# 


```

---

