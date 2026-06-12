---
title: "Can't right click while touching touchpad"
date: 2013-03-18
forum: Hardware
---

### Post by ShadowVegan on 2013-03-18
I have a new laptop (Asus X55A). When I try to right click while touching the touchpad, it counts as a left click. It doesn't even matter if I'm moving the cursor, any contact on the touchpad results in any click--left or right--registering as a left click. Is there any way to fix this? I am running Ubuntu 12.04.2 LTS 64-bit. Thanks.

---

### Post by cortman on 2013-03-18
Just to clarify- are you pressing a physical button on the touchpad to click, or are you tapping the pad itself?
Please also post the output of 

```
xinput
```

Thanks!

---

### Post by ShadowVegan on 2013-03-18
I am clicking the physical buttons, but they are part of the touchpad--i.e. they are sensitive, so if I move my finger along the buttons it moves the cursor. It looks like [this](http://laptoptab123.com/wp-content/uploads/2013/02/Asus-X55A-SPD0204O.jpg). And clicking the right button works normally, as long as I am not touching the touchpad in any other place at the same time.

```
administrator@X55A:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; ASUS USB2.0 Webcam                          id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=10    [slave  keyboard (3)]
```

Thanks.

---

### Post by cortman on 2013-03-18
Hm, try running

```
synclient PalmDetect=1
```

or

```
synclient FingerHigh=50
```

---

### Post by ShadowVegan on 2013-03-18
synclient PalmDetect=1 did nothing. synclient FingerHigh=50 made the touchpad very unresponsive (my USB mouse is unaffected), but didn't fix the right click issue.

---

### Post by cortman on 2013-03-18
Well, run

```
synclient FingerHigh=30
```

To reset that.

I suppose you could try disabling tap to click?

```
synclient TapButton1=1
```

---

### Post by ShadowVegan on 2013-03-18
That didn't seem to change anything. I'm thinking it might just be a hardware issue that can't be changed... but if you have any more ideas I'd love to hear them. Either way thanks for trying.

---

### Post by cortman on 2013-03-19
Must not be thinking right. It's

```
synclient TapButton1=0
```

1 means on, 0 means off.

---

### Post by ShadowVegan on 2013-03-19
Still no change.

---

### Post by cortman on 2013-03-20
I don't know if messing around with other synclient commands will help or not. You can try. Running

```
synclient
```

will bring up a list of available commands/settings.
Alternately, you can set it so that a two-finger tap equals right click (this is how I set all my laptops). The command is

```
synclient TapButton2=3
```

---

### Post by ckressibucher on 2013-11-03
If someone still looks after a solution: I used ```
synclient
``` to set following properties on my ASUS X55a (with Ubuntu 12.04):

```

synclient RightButtonAreaLeft=1650
synclient RightButtonAreaRight=3320
synclient RightButtonAreaTop=1600
synclient RightButtonAreaBottom=2300

```

this properties define an area (by coordinates), which register a right click event. Perhaps you have to figure out yourself, which coordinates work best for your device.

---

