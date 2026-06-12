---
title: "nvidia su settings"
date: 2008-08-18
forum: General Help
---

### Post by posterpaint on 2008-08-18
Type in nvidia-settings I get in terminal:
ERROR: Cannot open display 'chuck-desktop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 22 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 23 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 24 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 25 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 26 of configuration
       file '/home/chuck/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 27 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ForceGenericCpu specified on line 28 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 29 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 30 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 31 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 32 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 33 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 34 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 35 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 36 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 37 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 38 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 39 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 40 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 41 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 42 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 43 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 44 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 45 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 46 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 47 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 48 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 49 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       50 of configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       51 of configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 52 of
       configuration file '/home/chuck/.nvidia-settings-rc' (no Display
       connection)


The nividia server settings opens, 3D compiz works ok, screen rez perfect at 1680x1050, what is wrong?
Thanks for reading this too long post...:confused:

---

### Post by sdennie on 2008-08-18
Have you done something to change your DISPLAY variable (like in ~/.bashrc)?  nvidia-settings needs a valid DISPLAY variable to run.  Try:

```

DISPLAY=:0.0 nvidia-settings

```

If that works but opening a new terminal and trying still gives you the problem, make sure you aren't explicitly setting DISPLAY in ~/.bashrc.  Also, verify that that other X apps work.  Just try:

```

gcalctool

```

And see if it brings up a window from the terminal.

---

### Post by posterpaint on 2008-08-18
In terminal,
DISPLAY=:0.0 nvidia-settings
Same long display
In new terminal,
gcalctool
opened the calculator

Thanks so far

---

### Post by posterpaint on 2008-08-18
One more mystery,
in terminal enter nvidia-xconfig
get this;

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first CorePointer in the config input list.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.

chuck@chuck-desktop:~$ nvidia-settings

ERROR: Cannot open display 'chuck-desktop:0.0'.

---

