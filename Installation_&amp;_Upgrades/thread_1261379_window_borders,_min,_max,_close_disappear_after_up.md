---
title: "window borders, min, max, close disappear after update"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by traigo on 2009-09-08
After an update and reboot, my min, max, close buttons are gone.  There are no borders on windows and I can't move or resize any of them.  I can close using ctrl+w, alt+f4, or file->close/quit.  I can move from one desktop to another and my keyboard shortcuts still work like win+t for terminal.  How can I find the offending update and roll back?

Thanks,
Traigo

---

### Post by argail1980 on 2009-09-08
Hi,

that happens sometimes when I have compiz turned on and a funny X configuration. When you open a terminal, is it in focus, i.e. can you type?

If yes, try 
```
metacity --replace
```

that disables compiz and calls the standard gnome window-manager. Then you have window borders again and can start to look for what has happened to either compiz or your xorg.conf

---

### Post by traigo on 2009-09-08
metacity --replace gave back my window borders and buttons.
here's my xorg.confg
```

ection "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    Option        "RenderAccel"    "True"
##This turns on NVidia’s TwinView
    Option    "TwinView"
##Here I’m setting the resolution to the individual monitors.
    Option    "MetaModes" "1920×1200 1920×1200"
    Option    "TwinViewOrientation" "LeftOf"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
    Load        "glx"
EndSection

```

---

### Post by argail1980 on 2009-09-08
the config looks fine at first glance. try to start compiz again:

```
compiz --replace
```

and look for error messages. Otherwise, I'm not sure what to do. Are there errors in ```
/var/log/Xorg.0.log
```?

I remember that the Option

```
Option      "AddARGBGLXVisuals" "True"

```

In my xorg.conf helped once against the same Problem, but that's been a while ago in Gutsy

I got it from

[http://wiki.archlinux.org/index.php/Compiz_Troubleshooting]("http://wiki.archlinux.org/index.php/Compiz_Troubleshooting")

---

### Post by traigo on 2009-09-08
compiz --replace gives me:
```

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0400 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3840x1200) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: symbol lookup error: /usr/bin/gtk-window-decorator: undefined symbol: decor_blend_top_border_picture
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

---

### Post by argail1980 on 2009-09-08
> /apps/compiz/plugins/scale/allscreens/options/initiate_edge

ok... maybe disabling that option helps..
```
gconf-editor
```

what about the xorg.conf option?

---

### Post by traigo on 2009-09-08
Ok, added the option, nothing.

```

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0400 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3840x1200) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: symbol lookup error: /usr/bin/gtk-window-decorator: undefined symbol: decor_blend_top_border_picture
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x0000000000824e30 ***

```

---

### Post by traigo on 2009-09-09
Ok, after much screwing around, I was able to get it back to normal.  Not sure how, though.  I did apt-get remove libdecorator then reinstalled it and compiz.  I mucked around with theme settings and compiz settings.  I noticed that after removing and reinstalling compiz, I was on version 0.7.4 and not 0.7.2 as I was before. I'm totally baffed, but at least I'm back to normal. 

Here's my xorg.conf

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    Option        "RenderAccel"    "True"
    Option        "AddARGBGLXVisuals" "True"
##This turns on NVidia’s TwinView
    Option    "TwinView"
##Here I’m setting the resolution to the individual monitors.
    Option    "MetaModes" "1920×1200 1920×1200"
    Option    "TwinViewOrientation" "LeftOf"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
    Load        "glx"
EndSection

```

---

