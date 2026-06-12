---
title: "Kensington Expert Mouse - Trackball Setup Ubuntu 14.04"
date: 2014-07-24
forum: Hardware
---

### Post by michael197 on 2014-07-24
I'm new to Linux, just having set it up on an i7 system I built a few years with 16GB RAM - using Ubuntu 14.04.  I have a Kensington Expert Mouse - which is actually a trackball with four buttons.  The upper left button acts as the middle button on a typical mouse.  The upper right button functions as a "back" button.  I want the upper left button to be "back" and the upper right button to be "forward".  Using 'xev' shows that the upper left button is button 2, and the upper right is button 8.  I can use 'xbindkeys' and 'xautomation' to assign those buttons as Alt - Left Arrow and Alt - Right Arrow, and it works, but it is slow, and often fails to catch button presses.

Other solutions I found mention editing xorg.conf - but there is no such file.  Xinput set-button-map works if set up to run on startup, but it does not survive sleep mode.

Does anyone know a good, solid, elegant way to remap those buttons?

Thanks

---

### Post by tdmeskimo on 2014-12-29
Hi, wow! no reply yet?  I am searching for something simular but for the Kensington K72337US Orbit Trackball with Scroll Ring for PC or Mac.  I do have a Logitech Marblemouse that I got the middle-button-enable with it one line termal.  I am very enterested if you have countued to search and found any answers yet.  With that being said, what I am hopeing for is a middle-button-enable with the Kensington I am getting. Thanks in advance.

---

### Post by lvlammert on 2015-06-25
xinput will allow remapping of buttons, .. use xev to see the button IDs & xinput to see the device.

On my system, for example:

```
$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Generic USB K/B                             id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Generic USB K/B                             id=8    [slave  keyboard (3)]
```

the ID is 9, so with a little experimentation using xev, I set the buttons as follows:

# Setup trackball buttons
xinput set-button-map 9 2 1 3

---

### Post by lvlammert on 2015-06-25
Both right and left click will normally simulate a middle click - had to work that out for gimp.

---

### Post by irregularnerd on 2015-06-29
> **lvlammert said:**
> xinput will allow remapping of buttons, .. use xev to see the button IDs & xinput to see the device.

On my system, for example:

```
$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Generic USB K/B                             id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Generic USB K/B                             id=8    [slave  keyboard (3)]
```

the ID is 9, so with a little experimentation using xev, I set the buttons as follows:

# Setup trackball buttons
xinput set-button-map 9 2 1 3

Wonderful, this seems to be pretty much it, thank you. After a little further searching I also found that instead of xev one can also use ```
xinput test device id
``` to find out which button is which.

I'm pretty new to ubuntu - does this persist through restarts?

---

