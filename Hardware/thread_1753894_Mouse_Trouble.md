---
title: "Mouse Trouble"
date: 2011-05-09
forum: Hardware
---

### Post by Ashfaque on 2011-05-09
I'm having trouble with the mouse/touchpad. Two day old install with everything working fine initially.

A single tap is completely ignored for some reason. Double tapping  causes a single click and anything further does no good. I can't open an  application by double clicking it with the touchpad. The buttons,  however, work just fine.

Also, i can't seem to change mouse cursors, and it is now stuck b/w the default cursor and the white glass cursor, and displays either cursor at specific locations, e.g. the default cursor on the title bar and taskbar but the glass cursor everywhere else.

There doesn't seem to be anything else worth mentioning. That's possibly cause I'm a newbie to Ubuntu and have no idea about linux diagnostics.

I'm using Ubuntu Natty Narwhal on a Compaq CQ45.

---

### Post by zombolo on 2011-05-09
Post your xinput list.
I have similar problems with Alps touchpad (Aspire 3820T).

---

### Post by Ashfaque on 2011-05-10
> **zombolo said:**
> Post your xinput list.
I have similar problems with Alps touchpad (Aspire 3820T).
Is this what you wanted?

xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=14    [slave  keyboard (3)]
    &#8627; ENE eHome Infrared Remote Receiver          id=15    [slave  keyboard (3)]

Even I have an alps touchpad. Could it be a hardware issue?

---

### Post by zombolo on 2011-05-10
It's a software issue.
Alps touchpad in Linux is completely faulty. I got an Aspire notebook and have similar problems. No solution yet. It's a nightmare.

---

### Post by Ashfaque on 2011-05-10
So basically, we're done for? :/

---

