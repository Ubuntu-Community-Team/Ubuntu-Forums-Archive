---
title: "Display turned off while set not to"
date: 2018-01-27
forum: Hardware
---

### Post by accounts0 on 2018-01-27
Screenshot: [https://imgur.com/a/2ayfD](https://imgur.com/a/2ayfD)

I have power management set to not turn off the display but tonight I walked away from the computer for awhile & came back to a blue screen on my monitor, which it does when there's no signal. I moved my mouse & it all came back. Not sure why, or how to prevent it again.

EDIT:
Turns out however it went about removing the video from the monitor, it also rerouted the audio from the HDMI to the laptop speakers. I had to pulseaudio -k to get it back.

---

### Post by accounts0 on 2018-01-29
Bump

---

### Post by accounts0 on 2018-02-10
Bump

---

### Post by tinylagarto on 2018-02-11
What desktop environment do you use?

---

### Post by accounts0 on 2018-02-11
> **ivanovnegro2 said:**
> what desktop environment do you use?

kde

---

### Post by tinylagarto on 2018-02-11
Does your monitor have a proper standby function or something that could be disabled from the hardware itself?

What is the terminal output of:

```
xset q
```

---

### Post by accounts0 on 2018-02-12
> **ivanovnegro2 said:**
> Does your monitor have a proper standby function or something that could be disabled from the hardware itself?
No. It goes to bluescreen when the HDMI signal disappears, at which point the audio switches to the laptop speakers. After somewhere around 5 minutes the screen powers down.

If I move the mouse the image comes back but I have to close whichever app is currently using the laptop speakers, run pulseaudio -k, then restart apps involving audio so they're routed to the speakers.

> **ivanovnegro2 said:**
> What is the terminal output of:

```
xset q
```
```
[FONT=monospace][COLOR=#000000]$ xset q[/COLOR]
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  600    repeat rate:  25
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  20/10    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  900    cycle:  600
Colors:
  default colormap:  0x42    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,built-ins,/home/cb/.fonts
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled[/FONT]
```

EDIT:
Based on the above Screen Saver values, I'm guessing it's on with that 900 second timeout- despite being disabled in KDE's "System Settings".

At one point shortly after the onset of this behavior, I had a script that would run at logon, because I suspected it was XOrg behaving of its own volition. I don't remember where I found it, plus the script didn't work anyway. I figured I'd post it here for reference. It ran as user.

```

#!/bin/bash
sleep 30
xset s 0 s blank

```

I also found this old forum post [https://www.linuxquestions.org/questions/linux-general-1/how-to-disable-screen-blanking-in-x-175011/](https://www.linuxquestions.org/questions/linux-general-1/how-to-disable-screen-blanking-in-x-175011/)

...But I wonder if the solution(s) presented there might be outdated.

---

### Post by tinylagarto on 2018-02-12
From the look of those lines:

```
[FONT=monospace]DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled[/FONT]
```

dpms is disabled.

Therefore it could be something with the HDMI connection. Of course you could change some settings and try but if it is disabled it should not interfere.

---

### Post by accounts0 on 2018-02-20
To follow-up, shortly after my last message here above, I ran these 2 commands

```
xset s off
xset s noblank
```

And the screen hasn't turned off or blanked again since. I've also put these commands in a script to run at logon, but I haven't rebooted yet since then to know if it works.

---

### Post by tinylagarto on 2018-02-20
Not a bad idea.

---

### Post by accounts0 on 2018-02-22
> **accounts0 said:**
> To follow-up, shortly after my last message here above, I ran these 2 commands

```
xset s off
xset s noblank
```

And the screen hasn't turned off or blanked again since. I've also put these commands in a script to run at logon, but I haven't rebooted yet since then to know if it works.

So that doesn't work. Still tinkering, will check back.

---

### Post by accounts0 on 2018-02-22
Upon running ```
xset q
``` I saw that DPMS was somehow enabled, with timers all set at 600 seconds. When I went into KDE System Settings to check Power Management settings, I got an error message about the 'power management' background service being disabled, & thus not running. Enabled that & started it, then reset Power Management settings to never turn off the screen. Then I reran my startup script, thinking that it went unheeded at login since the power management background service wasn't running to hear it. Now after all that I have DPMS showing as disabled, & its timers are all at zero now.

Note that I have edited my startup script to do these commands both as user & root, don't know if it helps or not. Will reboot soon & see what happens when I walk away from the screen for a few minutes. For reference here's my script now.

```

#!/bin/bash
sleep 30
xset s off
xset s noblank
echo password | sudo -S xset s off && sudo xset s noblank

```

---

### Post by accounts0 on 2018-02-22
I've now waited well over 600 seconds- more like a half hour, actually. DPMS shows as still disabled with its timers all at zero. And my screen/HDMI audio is still alive & kicking after a break elsewhere.

I don't know what exactly I did to make this work right this time. Previously I thought I was in the clear & wasn't, so I'm still a bit tentative. However my break was successful just now after having set it all up prior to the most recent reboot. Again, don't know why but glad it is.

In this case a shotgun approach was my best bet IMO, so I've likely done some stuff that's entirely unnecessary. I just don't have time to go learn XOrg enough to know what exactly the deal was here.

Best of luck to anyone else who finds yourself in this thread. And keep your fingers crossed for me. Hopefully I'll have no reason to report back here again. :-)

---

### Post by tinylagarto on 2018-02-23
What a workaround. I am glad you solved it for you.

---

