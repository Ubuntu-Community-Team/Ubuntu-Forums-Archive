---
title: "Ubuntu 16.04 LTS - touchpad click makes mouse jump randomly"
date: 2016-05-13
forum: Hardware
---

### Post by insane9 on 2016-05-13
I'm using a HP Envy - when I use the touchpad to click on a part of the screen, the mouse sometimes jumps to another part of the screen. I've ran xinput , xinput --test 13 and then xinput --watch-props 13 

Here is the output of each command:

simon@envy:~$ xinput 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Truevision HD                            id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=13    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=14    [slave  keyboard (3)]
simon@envy:~$ 
simon@envy:~$ xinput --test 13



simon@envy:~$ xinput --watch-props 13
Device 'HP WMI hotkeys':
    Device Enabled (139):    1
    Coordinate Transformation Matrix (141):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Product ID (259):    0, 0
    Device Node (260):    "/dev/input/event15"


Not sure what to do next. Can anyone help me to fix this??

Thank you in advance.

EDIT: I followed steps here: [https://askubuntu.com/questions/127829/synaptics-touchpad-cursor-moves-around-when-just-tapped-after-ubuntu-12-04-u](https://askubuntu.com/questions/127829/synaptics-touchpad-cursor-moves-around-when-just-tapped-after-ubuntu-12-04-u) and changed my FingerHigh and FingerLow setting. It has helped a tiny bit, but not fixed the issue.

EDIT 2: Seem to have fixed issue using this video: [https://www.youtube.com/watch?v=4-cGqVLXyrA](https://www.youtube.com/watch?v=4-cGqVLXyrA) but I think i've found the underlying problem. When I use the touchpad to select text on a page (left click and hold, then drag with touchpad to select text). If you move up/down with your right finger, the page goes up or down..... Madness. Who would ever want that as a feature?? Trying to find out how to disable that.

EDIT 3: Potential fix: [http://ubuntuforums.org/showthread.php?t=2322086&p=13477856#post13477856](http://ubuntuforums.org/showthread.php?t=2322086&p=13477856#post13477856)

---

