---
title: "touchpad configuration hp pavilion g7-1204sa under 10.04"
date: 2012-01-08
forum: Hardware
---

### Post by paulernest on 2012-01-08
Hello,

I've been googling again, but to no avail.

I want to be able to disable the touchpad of my laptop so that I can type without the cursor jumping all over the place when I accidentally brush the touchpad. Ideally I would like to be able to use the enable/disable feature built into the touchpad, but reading around, I think this is probably beyond what's currenly possible. I'd be quite happy with a keyboard short cut to enable/disable the touchpad, or to try out the feature I've read about where the touchpad is intelligently disabled when you type. I think that gsynaptics will give me plenty of useful options to play with but I can't get it to work.

If I install gpointing-device-settings, then I get a pointing devices menu under system>preferences, this gives me options for middle button emulation and scrollwheel emulation, but nothing to disable the touchpad.

If I install gsynaptics, then I get a touchpad menu entry under system>preferences, but when I click it I get the message 
```
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```I've followed the instructions [here]("https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick") to enable SHMConfig, but adding the new hal policy and rebooting doesn't change anything and I still get the error message shown above. Should I be adding a policy specific for my machine or is the one from the above ubuntu help page good for everyone? Also how can I tell if that policy is being loaded?

If it's of any use, I get the following output.
```
synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?
```I'd really appreciate any help that anyone can offer. Please ask and I'll post any output that will help.

Thanks

---

### Post by paulernest on 2012-01-09
I've come up with a solution, it's not great but it does the job. Because I'm hoping that there is a proper solution using either gsynaptics or gpointingdevicesettings, I wont mark this thread a solved.

A little bit of googling led me to this command to enable/disable the touchpad 
```
xinput --set-prop "PS/2 Synaptics TouchPad" "Device Enabled" 0
```I wrote a short shell script that toggles the touchpad on and off, and then bound that script to a keyboard shortcut, using system->preferences->keyboard shortcuts

The toggle script is shown below
```
if [ "`xinput --list-props 'PS/2 Synaptics TouchPad' | grep 'Device Enabled.*1$'`" ]; then xinput --set-prop "PS/2 Synaptics TouchPad" "Device Enabled" 0; else xinput --set-prop "PS/2 Synaptics TouchPad" "Device Enabled" 1; fi
```This is rough around the edges, but I guess it does the job until I find a better solution. Any suggestions on getting gpointingservices working would be gratefully received.

---

