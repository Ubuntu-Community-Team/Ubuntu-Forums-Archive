---
title: "nvidia-settings won't do anything"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by ElTimo on 2008-01-25
ok I had a thread like this before, but apparently it got deleted or something.

nvidia-settings won't do squat. i opened it up in a terminal and it gave me a whole boatload of errors, the very first one being "cannot open display tim-laptop:0.0" which it damn well should be able to open! any help would be greatly appreciated.

---

### Post by Mikecore on 2008-01-25
> **ElTimo said:**
> ok I had a thread like this before, but apparently it got deleted or something.

nvidia-settings won't do squat. i opened it up in a terminal and it gave me a whole boatload of errors, the very first one being "cannot open display tim-laptop:0.0" which it damn well should be able to open! any help would be greatly appreciated.

usually when this happens your are trying to run a program logged in as root. or you have some type of file permission problem. "you could try uninstalling the driver/tools and reinstalling"

---

### Post by oldsoundguy on 2008-01-25
have you tried installing the drivers using Envy?  Worked for me on three different desktops without a hitch!

---

### Post by ElTimo on 2008-01-26
this is what happens:
tim@tim-laptop:~$ sudo nvidia-settings
[sudo] password for tim:

ERROR: Cannot open display 'tim-laptop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 22 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 23 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 24 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 25 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 26 of configuration
       file '/home/tim/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 27 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ForceGenericCpu specified on line 28 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 29 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 30 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 31 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 32 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 33 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 34 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 35 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 36 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 37 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 38 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 39 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 40 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 41 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 42 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 43 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 44 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 45 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 46 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 47 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 48 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 49 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       50 of configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       51 of configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 52 of
       configuration file '/home/tim/.nvidia-settings-rc' (no Display
       connection).

/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:195: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:199: Overlay image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:231: Unable to locate image file in pixmap_path: "Toolbar/toolbar.png"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:234: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:904: Unable to locate image file in pixmap_path: "Scrollbars/stepper-up.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:908: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:914: Unable to locate image file in pixmap_path: "Scrollbars/stepper-up-prelight.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:918: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:924: Unable to locate image file in pixmap_path: "Scrollbars/stepper-up-prelight.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:928: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:934: Unable to locate image file in pixmap_path: "Scrollbars/stepper-up-insens.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:938: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:948: Unable to locate image file in pixmap_path: "Scrollbars/stepper-down.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:952: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:958: Unable to locate image file in pixmap_path: "Scrollbars/stepper-down-prelight.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:962: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:968: Unable to locate image file in pixmap_path: "Scrollbars/stepper-down-prelight.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:972: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:978: Unable to locate image file in pixmap_path: "Scrollbars/stepper-down-insens.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:982: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:991: Unable to locate image file in pixmap_path: "Scrollbars/stepper-right.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:995: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1001: Unable to locate image file in pixmap_path: "Scrollbars/stepper-right-prelight.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1005: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1011: Unable to locate image file in pixmap_path: "Scrollbars/stepper-right-prelight.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1015: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1021: Unable to locate image file in pixmap_path: "Scrollbars/stepper-right-insens.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1025: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1035: Unable to locate image file in pixmap_path: "Scrollbars/stepper-left.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1039: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1045: Unable to locate image file in pixmap_path: "Scrollbars/stepper-left-prelight.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1049: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1055: Unable to locate image file in pixmap_path: "Scrollbars/stepper-left-prelight.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1059: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1065: Unable to locate image file in pixmap_path: "Scrollbars/stepper-left-insens.pngxxx"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1069: Background image options specified without filename
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1586: Unable to locate image file in pixmap_path: "Buttons/button-normal.png"
/root/.themes/Blue-Junior0.9.4/gtk-2.0/gtkrc:1590: Background image options specified without filename

** (nvidia-settings:6943): WARNING **: Invalid borders specified for theme pixmap:
        /root/.themes/Blue-Junior0.9.4/gtk-2.0/Frame-Gap/frame-gap-start.png,
borders don't fit within the image

** (nvidia-settings:6943): WARNING **: Invalid borders specified for theme pixmap:
        /root/.themes/Blue-Junior0.9.4/gtk-2.0/Frame-Gap/frame1.png,
borders don't fit within the image

** (nvidia-settings:6943): WARNING **: Invalid borders specified for theme pixmap:
        /root/.themes/Blue-Junior0.9.4/gtk-2.0/Frame-Gap/frame-gap-end.png,
borders don't fit within the image

@oldsoundguy: Thats how i nstalled the drivers to begin with. good thought though

EDIT: What I'm trying to say is that the problem is definitely with nvidia-settings itself.

---

### Post by Mikecore on 2008-01-26
based on that I would try un installing your graphic driver from nvidia ( from your version to the latest one. or if it already is that I would un-install reinstall and make sure you remove  /home/tim/.nvidia-settings-rc from your home directory before you reinstall sound like some bad settings are there.

---

