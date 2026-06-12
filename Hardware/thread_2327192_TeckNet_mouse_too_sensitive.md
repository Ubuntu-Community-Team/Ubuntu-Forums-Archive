---
title: "TeckNet mouse too sensitive"
date: 2016-06-08
forum: Hardware
---

### Post by dannymcgill on 2016-06-08
OS: Ubuntu 16.04
Mouse: TeckNet M002-GREY ( Cordless Optical Mouse )

In the settings tab "Mouse and Touchpad", all that shows up is "General" and "Touchpad" and nothing for the wireless mouse I'm using. Performing "xinput list" in the command prompt shows that the mouse is detected as "MOSART Semi. 2.4G Keyboard Mouse". The current settings make it too sensitive for my normal use, though it does function. I haven't found a way to either change the sensitivity via the command prompt or to get the GUI to display the option in the "Mouse and Touchpad" tab.

Any suggestions?

---

### Post by QDR06VV9 on 2016-06-08
What is the output of this in the terminal
```
xinput --list
```
Paste it back here.

---

### Post by dannymcgill on 2016-06-08
```
~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Keyboard Mouse            id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech K360                               id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; MOSART Semi. 2.4G Keyboard Mouse            id=9    [slave  keyboard (3)]
    &#8627; ASUS USB2.0 Webcam                          id=12    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
```

---

### Post by QDR06VV9 on 2016-06-08
try this to see if the sensitivity is better 
```
xinput --set-prop 10 "Device Accel Constant Deceleration" 4

```

---

### Post by dannymcgill on 2016-06-08
That did it, thank you!

---

### Post by QDR06VV9 on 2016-06-08
Ok Great! But I don't think that setting will survive a reboot so to make it persistent
We will need to add it to the system to do this after logging in

create script:

```
#!/bin/bash
xinput --set-prop 10 "Device Accel Constant Deceleration" 4
xinput --set-prop 10 "Device Accel Velocity Scaling" 1
```
Save it then run This:
I am assuming you are running either Unity or Gnome
 ```
gnome-session-properties
```
and add the script to the list.

---

### Post by dannymcgill on 2016-06-09
I'll have to restart my computer again to see if the bash script was created with the new commands successfully, but until then I'll mark this as solved.

Thanks, your help is very much appreciated.

---

### Post by QDR06VV9 on 2016-06-09
> **dannymcgill said:**
> I'll have to restart my computer again to see if the bash script was created with the new commands successfully, but until then I'll mark this as solved.

Thanks, your help is very much appreciated.

You are very welcome...and if anything needs adjusting just post back.
Kind Regards

---

