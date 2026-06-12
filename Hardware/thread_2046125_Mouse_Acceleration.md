---
title: "Mouse Acceleration"
date: 2012-08-22
forum: Hardware
---

### Post by Trauer on 2012-08-22
Oukay... Before anything, I'd like to say that english is not my main language... So, uh, sorry about my grammar mistakes...

Anyway, heres the thing: i finally decided to man up and use linux... Only linux.
And as all newbies/windows 8 I'm having some silly adaptation issues...
The most annoying one is related to mouse acceleration/sensitivity... I'm using a Razer Imperator, and it's quite hard to use it here... I move it a inch and the cursor flew through the screen...

I googled for a while and found that:

xinput set-prop 10 'Evdev Middle Button Emulation' 0
xinput set-prop 10 'Device Accel Profile' -1
xinput set-prop 10 'Device Accel Velocity Scaling' 1 

helps a lot, but the sensitivity still quite high... At least the acceleration is gone...
Idk why, but xinput gave my Razer Imperator 2 ids...
So I have to type this twice, one for id 10 and another for id 11...

I'd like to create a start up script to run this commands...
I tried to... I opened gedit and wrote:

#!/bin/bash
#wait for the desktop to settle
sleep 5
# turn off mouse acceleration
xinput set-prop 10 'Evdev Middle Button Emulation' 0
xinput set-prop 10 'Device Accel Profile' -1
xinput set-prop 10 'Device Accel Velocity Scaling' 1 
xinput set-prop 11 'Evdev Middle Button Emulation' 0
xinput set-prop 11 'Device Accel Profile' -1
xinput set-prop 11 'Device Accel Velocity Scaling' 1 

saved it as noaccel.sh

Now what? D:

---

### Post by Trauer on 2012-08-23
Bump... 

ps: sorry if posted this in the wrong forum

---

### Post by Ubun2to on 2012-08-23
Settings>Mouse and Touchpad should help.
You can adjust the acceleration and sensitivity of the mouse from here.

---

### Post by knpoe on 2013-02-22
> **Trauer said:**
> Oukay... Before anything, I'd like to say that english is not my main language... So, uh, sorry about my grammar mistakes...

Anyway, heres the thing: i finally decided to man up and use linux... Only linux.
And as all newbies/windows 8 I'm having some silly adaptation issues...
The most annoying one is related to mouse acceleration/sensitivity... I'm using a Razer Imperator, and it's quite hard to use it here... I move it a inch and the cursor flew through the screen...

I googled for a while and found that:

xinput set-prop 10 'Evdev Middle Button Emulation' 0
xinput set-prop 10 'Device Accel Profile' -1
xinput set-prop 10 'Device Accel Velocity Scaling' 1 

helps a lot, but the sensitivity still quite high... At least the acceleration is gone...
Idk why, but xinput gave my Razer Imperator 2 ids...
So I have to type this twice, one for id 10 and another for id 11...

I'd like to create a start up script to run this commands...
I tried to... I opened gedit and wrote:

#!/bin/bash
#wait for the desktop to settle
sleep 5
# turn off mouse acceleration
xinput set-prop 10 'Evdev Middle Button Emulation' 0
xinput set-prop 10 'Device Accel Profile' -1
xinput set-prop 10 'Device Accel Velocity Scaling' 1 
xinput set-prop 11 'Evdev Middle Button Emulation' 0
xinput set-prop 11 'Device Accel Profile' -1
xinput set-prop 11 'Device Accel Velocity Scaling' 1 

saved it as noaccel.sh

Now what? D:

just add it to your ~/.bashrc file 
i.e.```
echo "/path/to/noaccel.sh&">>~/.bashrc
```

:D

(i use this for my razer naga- with dpi maxed)
and here is my script:
```
xinput set-prop 'pointer:Razer Razer Naga' 'Evdev Middle Button Emulation' 1
xinput set-prop 'pointer:Razer Razer Naga' 'Device Accel Profile' -1
xinput set-prop 'pointer:Razer Razer Naga' 'Device Accel Velocity Scaling' 1
xinput set-prop 'pointer:Razer Razer Naga' 'Device Accel Constant Deceleration' 2

```


hope that helps...  :)

---

### Post by vocalstatic on 2013-08-06
hey sorry to up this thread but i have the same issues with my mouse aceleration + 2 time razer imperator

i don't understand this part :

[COLOR=#000000]just add it to your ~/.bashrc file [/COLOR]
[COLOR=#000000]i.e.[/COLOR][COLOR=#000000]Code:
echo "/path/to/noaccel.sh&">>~/.bashrc[/COLOR]
Can you help me pls ?

I do it in terminal wit my path and it will start up in everyboot ?

my xinput : 
```

xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Imperator                       id=8    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Imperator                       id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```

---

