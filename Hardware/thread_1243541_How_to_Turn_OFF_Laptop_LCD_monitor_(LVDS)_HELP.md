---
title: "How to Turn OFF Laptop LCD monitor (LVDS)?? HELP"
date: 2009-08-18
forum: Hardware
---

### Post by sumantagogoi on 2009-08-18
I need to turn off the internal monitor of laptop as it is broken and i m using an external display.

At present i do this using xrandr, where i have to manually disable LVDS everytime i start the OS.

I want this to happen automatically on boot possibly without the internal monitor turning on at all.

Also my bios doesn't have the option to turn off the monitor.

PLEASE HELP

---

### Post by sumantagogoi on 2009-08-19
Finally Found The Solution

Have to create a script in /etc/X11/Xsession.d/ called "45custom_xrandr-settings"

Contents are:

```


[COLOR=#007800]EXTERNAL_OUTPUT=[/COLOR][COLOR=#ff0000]"VGA"[/COLOR]
[COLOR=#007800]INTERNAL_OUTPUT=[/COLOR][COLOR=#ff0000]"LVDS"[/COLOR]

xrandr [COLOR=#000000]**|**[/COLOR]grep [COLOR=#007800]$EXTERNAL_OUTPUT[/COLOR] [COLOR=#000000]**|**[/COLOR] [COLOR=#c20cb9]**grep**[/COLOR] [COLOR=#ff0000]" connected "[/COLOR]
[COLOR=#000000]**if**[/COLOR] [COLOR=#7a0874]**[**[/COLOR] [COLOR=#007800]$?[/COLOR] -eq [COLOR=#000000]0[/COLOR] [COLOR=#7a0874]**]**[/COLOR]; [COLOR=#000000]**then**[/COLOR]
    xrandr --output [COLOR=#007800]$INTERNAL_OUTPUT[/COLOR] --off --output [COLOR=#007800]$EXTERNAL_OUTPUT[/COLOR] --auto 
[COLOR=#000000]**else**[/COLOR]
    xrandr --output [COLOR=#007800]$INTERNAL_OUTPUT[/COLOR] --auto --output [COLOR=#007800]$EXTERNAL_OUTPUT[/COLOR] --off
[COLOR=#000000]**fi**[/COLOR]

```At startup this checks if external display is connected.
If it is connected then the laptop monitor turns OFF and external monitor turns ON.
If the external display is NOT connected then only internal monitor works.

---

### Post by raymr on 2010-05-03
This worked great for me, since the display would get scrambled when both monitors were turned on. I would manually disable the laptop monitor but rebooting or even locking/unlocking the screen would turn it back on again.

If anyone else uses this, be sure to check the names of the devices. In my case they were VGA1 and LVDS1.

---

### Post by Lightfast on 2010-09-21
Just what I was looking for. Works perfectly with my Xubuntu 10.04. Thanks a ton!

---

### Post by GhettoFish on 2011-01-21
This worked for me as well!
Had to change VGA to VGA-0 though but that was no biggie.

The real issue I have since like you my monitor is broken is that I am unable get the image to my external monitor unless I enter x.org.
If anyone has a solution to only use the VGA-port on the back and never use internal monitor please give me a shout :)

Thx again for this solution though!

---

### Post by finnian on 2011-07-20
This alternative script adapts to variations in output names: VGA, VGA1, VGA-01 etc

```
VGA_MONITOR_LINE=$(xrandr | grep "^VGA.*connected")
VGA_MONITOR_LINE=${VGA_MONITOR_LINE%%ed*}
VGA_MONITOR=${VGA_MONITOR_LINE%% *}
VGA_MONITOR_STATUS=${VGA_MONITOR_LINE#* }

LVDS_MONITOR_LINE=$(xrandr | grep "^LVDS.*connected")
LVDS_MONITOR=${LVDS_MONITOR_LINE%% *}

if [ $VGA_MONITOR_STATUS = "connect" ]; then
    xrandr --output $LVDS_MONITOR --off --output $VGA_MONITOR --auto 
else
    xrandr --output $LVDS_MONITOR --auto --output $VGA_MONITOR --off
fi
```

---

### Post by markosjal on 2013-01-08
I have an Asus Mini ITX with Built in LVDS port, abd no way to disable in BIOS. WHen I ran Linux Mint 10 (ubuntu 10.10) I only had to turn off the LVDS in the Gnome setings. However with Linux Mint 14 Cinnamon the GUI settings had no effect on XBMC, so I used the above modified. I am sure it is more than is needed I just want the LVDS always disabled, and dont really need it, then but was unsure of editing. I did this

```

VGA_MONITOR_LINE=$(xrandr | grep "^VGA.*connected")
VGA_MONITOR_LINE=${VGA_MONITOR_LINE%%ed*}
VGA_MONITOR=${VGA_MONITOR_LINE%% *}
VGA_MONITOR_STATUS=${VGA_MONITOR_LINE#* }

LVDS_MONITOR_LINE=$(xrandr | grep "^LVDS.*connected")
LVDS_MONITOR=${LVDS_MONITOR_LINE%% *}

if [ $VGA_MONITOR_STATUS = "connect" ]; then
    xrandr --output $LVDS_MONITOR --off --output $VGA_MONITOR --auto 
else
    xrandr --output $LVDS_MONITOR --off --output $VGA_MONITOR --auto
fi

```

the above works for me but I think I could probably just use

```

VGA_MONITOR_LINE=$(xrandr | grep "^VGA.*connected")
VGA_MONITOR_LINE=${VGA_MONITOR_LINE%%ed*}
VGA_MONITOR=${VGA_MONITOR_LINE%% *}
VGA_MONITOR_STATUS=${VGA_MONITOR_LINE#* }

LVDS_MONITOR_LINE=$(xrandr | grep "^LVDS.*connected")
LVDS_MONITOR=${LVDS_MONITOR_LINE%% *}

    xrandr --output $LVDS_MONITOR --off --output $VGA_MONITOR --auto
fi

```

but did not test

---

