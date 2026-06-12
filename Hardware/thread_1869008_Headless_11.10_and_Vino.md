---
title: "Headless 11.10 and Vino"
date: 2011-10-25
forum: Hardware
---

### Post by daviest11 on 2011-10-25
Morning all,

I've done a lot of searching and there doesn't seem to be an answer to this particular issue... still, apologies if I've missed something.

So, I've always run Ubuntu headless and as file server and torrent box. For various reasons, I prefer to use Vino rather than any other flavour of VNC. There's always been issues running Vino headless, but they have generally been overcome by a variety of well documented changes to xorg.conf. However, after the upgrade to 11.10, none of these seem to work. I'm incredibly frustrated, and would appreciate some help.

What I've got so far:

/etc/X11/xorg.conf
```
Section "Device"
Identifier "VNC Device"
Driver "vesa"
EndSection

Section "Screen"
Identifier "VNC Screen"
Device "VNC Device"
Monitor "VNC Monitor"
SubSection "Display"
Modes "1024x768"
EndSubSection
EndSection

Section "Monitor"
Identifier "VNC Monitor"
HorizSync 30-70
VertRefresh 50-75
EndSection
```

I've also tried variations on this, including the Vesa tags that worked for my previous box and version of Ubuntu.

The relevant parts of Xorg.0.log

```
[    11.405] (==) Using config file: "/etc/X11/xorg.conf"
[    11.405] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
```

```
[    11.433] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.433] vesa: Ignoring device with a bound kernel driver
[    11.433] (WW) Falling back to old probe method for vesa
[    11.433] (II) UnloadModule: "vesa"
[    11.433] (II) Unloading vesa
[    11.433] (EE) Screen(s) found, but none have a usable configuration.
[    11.433]
Fatal server error:
[    11.433] no screens found

```

Obviously, with no session, Vino simply refuses to start. 

I'm on 64bit, and running on a new HP Proliant Micro server (which are awesome by the way. Ebuyer are still doing them dirt cheap with £100 cashback from HP)

Thanks in advance for any help,

Tom

---

### Post by daviest11 on 2011-10-25
After fiddling for a bit, I've now reinstated the gnome classic sessions, and they seem to be starting OK. However, starting vino-server still gives...

"Cannot open display:"

Could this be a more generic problem with Vino?

Thanks,

Tom

---

### Post by daviest11 on 2011-11-03
Managed to solve this one. Turns out that when you install the 3rd party ATI drivers for the proliant micro, it includes an application called aticonfig, which takes the place of the "X -configure" command. Running this produced an xorg.conf which worked perfectly. Even without a monitor plugged in, the sessions start and vino is available. 

For completeness sake, it's worth noting that I had already install ed the gnome-session-fallback package, and was using "Gnome classic (no effects)" as my default session.

---

### Post by elsalvador on 2012-01-15
Hi Guys,

yeah, still not there yet...
headless...hmmm.
Looks like a multi-layered issue, due to the "clever" ATI config program, erm... "aticonfig"

Stupid thing thinks we're always going to have a Plug&Play monitor attached, (make it easy for us).

So the xorg.conf is full of "aticonfig" stuff finding the Device, Screen & Monitor.
So (despite my noob skills) tried hand-crafting an xorg.conf to tell the stupid machine I have a 1080p monitor attached, but I have failed somewhere along the line & have had any number of failures, from no screen to a crappy small "unknown" screen...

FWIW, here's the "best" version I got to, although it's actually still pretty rubbish as it's best is 1600x1200, but at least VNC now works, and it boots, so it will do until/unless someone can suggest where I went wrong in the xorg.conf:
____xorg.conf____
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
Identifier "LG1080p"
#
HorizSync 31.5 - 80.0
VertRefresh 60
DisplaySize 510 287
ModeLine "1080p" 148.50 1920 2012 2068 2200 1080 1082 1088 1125

Option "ReducedBlanking" "TRUE"
Option "ExactModeTimingsDVI" "TRUE"
Option "ModeValidation" "NoDFPNativeResolutionCheck"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
Identifier    "Screen0"
Device        "aticonfig-Device[0]-0"
Monitor        "LG1080p"
DefaultDepth 24
    Subsection "Display"
    Depth 24
    Modes "1080p" "1920x1080_60.00"
    EndSubsection
EndSection
______end__________

Thanks - hope this helps someone.
(Ubuntu still not really there yet, is it? Close but still a lot of gotchas)

---

