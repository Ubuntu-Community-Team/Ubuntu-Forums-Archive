---
title: "screen touch doesn't work,help please"
date: 2016-04-28
forum: Hardware
---

### Post by law2016 on 2016-04-28
Hello,

im french and sorry for my english.
my laptop is thnkpad X1 yoga, icore7 with screen touch.
I installed ubuntu 16.04.
The screen touch is not working.
i did this:

law@TX1CY:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Co.,Ltd. Pen and multitouch sensor Finger touch    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Co.,Ltd. Pen and multitouch sensor Pen stylus    id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Co.,Ltd. Pen and multitouch sensor Pen eraser    id=15    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)]
law@TX1CY:~$ xinput -set-prop 10 "Device Enabled" 1
law@TX1CY:~$ export TSLIB_TSDEVICE=/dev/input/eventX
law@TX1CY:~$ ts_calibrate
ts_calibrate : commande introuvable


The touch screen still doesnt work, who can help me please?

thanks

---

