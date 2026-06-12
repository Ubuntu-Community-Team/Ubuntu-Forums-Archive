---
title: "LCD Resolution Messed up after adding xorg.conf wacom lines"
date: 2008-04-27
forum: Hardware
---

### Post by beardiggin on 2008-04-27
Hello,

I'm using Hardy, on a Toshiba Tecra M7.  I did a clean install dual booting XP Hardy 8.04.  My stylus didn't work, so I attempted to add the lines to my xorg.conf.  I thought that I had backed up my xorg.conf.

After making the changes including lines for stylus, eraser and cursor. 

```

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "stylus"
 Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "cursor"
 Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


``` 

I restarted the xserver once using <ctrl> <alt> <bksp>.  The first time nothing happened so found than I needed to add some lines to the server layout.  I added these lines

```


        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"


```

I seemed to have extraneous content I was not aware of and it seems to have messed up my resolution.  I seem to be unable to get my system back to the clean graphics and resolution I had before, and my eyes are going crazy with this bad resolution.

Please help.

---

### Post by beardiggin on 2008-04-27
Never mind.  Somehow the x server must not have been restarting.  When I restarted the system all was well.  I reloaded the default xorg.conf using the command at the top of the xorg.conf file.

---

