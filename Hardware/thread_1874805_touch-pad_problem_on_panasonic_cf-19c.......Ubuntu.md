---
title: "touch-pad problem on panasonic cf-19c.......Ubuntu 11.10."
date: 2011-11-03
forum: Hardware
---

### Post by reillyx on 2011-11-03
touch-pad problem on panasonic toughbook cf-19c.......Ubuntu 11.10.
no scrolling  on touch-pad but everything else is working.up in system settings i can find only mouse settings and it is no touch-pad atoll ...
after running [xinput list                      ] i am getting that...

reilly@reilly-CF-19CCBCBVM:~$ xinput list 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen stylus                   id=9    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen eraser                   id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Panasonic Laptop Support                    id=12    [slave  keyboard (3)]
reilly@reilly-CF-19CCBCBVM:~$ 

i am tried everything what i know looks like i have all synaptics drivers but nothing really worked...
please somebody help me,...

---

### Post by DrSurge on 2012-03-07
**The problem with the drivers for the toughbooks in general is that the scroll support is just not there... The makers of the driver simply did not code in the ID of that area and function of the touchpad for the CF-19. On many different distros of linux I have tried to do the same on my 19, but it seems this issue needs to be brought up to the publishers for the synaptics driver in question. I am a toughbook collector by the way**.

---

