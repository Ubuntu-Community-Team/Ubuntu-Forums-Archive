---
title: "How to set one monitor to run always as default?"
date: 2022-03-18
forum: Hardware
---

### Post by TheUninvited on 2022-03-18
So I have two monitors even though I am changing it to single display,  every time i reboot I have to do the same... because when my computer opens , it activates both screens but i only want one.

---

### Post by him610 on 2022-03-18
I do not have two monitors, so I can not try it for myself, but I wonder - Why not just keep one monitor turned off?

---

### Post by mastablasta on 2022-03-18
it can be almost impossible on nvidia... :-)

but anyway what GPU are you using and also are you on ubuntu? in system settings there should be an option (which you maybe already use) to use only one monitor. in KDE you would apply it and the setting would stay as you set it. are you saying you select single monitor and loose this setting at reboot?

if you are using nvidia, then make sure you also do it in nvidia settings.  in my case on the old card it always turned on TV (or rather the HDMI output went to TV), before it was turned off and it automatically switched to VGA PC monitor only.

---

### Post by yetimon_64 on 2022-03-18
> **TheUninvited said:**
> So I have two monitors even though I am changing it to single display,  every time i reboot I have to do the same... because when my computer opens , it activates both screens but i only want one.

I am on Xubuntu 20.04 on a laptop with a HDMI tv plugged in here. The laptop has a screen name of "eDP1" with the TV called "HDMI1". I control displays here with a bit of scripting run from session startup settings.

 On startup I have a script called mon-chk that is run from "Session and startup" in the settings.
The checking script "mon-chk" that is called at session startup...
```
#!/bin/bash

if [ $(xrandr | grep HDMI-1 | cut -d\  -f2) == "connected" ]; then
   $HOME/.screenlayout/hdmi.sh
else
   $HOME/.screenlayout/edp1.sh
fi

exit 0
```
If my hdmi TV is detected as being connected the "hdmi.sh" script is run. The "hdmi.sh" script turns off the laptop screen and sets up the display for the TV...
"hdmi.sh"
```
#!/bin/sh
xrandr --output eDP-1-1 --off --output HDMI-1-1 --primary --mode 1920x1080i --rate 60 --pos 0x0 --rotate normal
```

Otherwise if my TV is not connected the "edp1.sh" is run which sets up the laptop screen...
"edp1.sh"
```
#!/bin/sh
xrandr --output eDP-1-1 --mode 1920x1080 --pos 0x0 --rotate normal --output HDMI-1-1 --off
```

I set up this bit of scripting for when I have the TV plugged in I don't want both screens turned on like you are noting. Basically these 3 scripts control my display output here at each session startup. This scripting idea I use here could be altered to suit your monitor names and settings.

Note the path "$HOME/.screenlayout" is a custom location on my set up and is added to my users path. If you try out this scripting idea you would be best to store any scripts in $HOME/bin which after restarting or logging out and back in again would be in you users path.

Cheers, yeti.

---

### Post by slickymaster on 2022-03-18
*Thread moved to **Hardware**.*

---

### Post by mIk3_08 on 2022-03-18
> **TheUninvited said:**
> So I have two monitors even though I am changing it to single display,  every time i reboot I have to do the same... because when my computer opens , it activates both screens but i only want one. 
For me, this matter to the vga ports which is the primary and secondary port you are using. In my case, the primary port setting  is the dp then hdmi then last is dvi. That's it. It works great. regards.

---

