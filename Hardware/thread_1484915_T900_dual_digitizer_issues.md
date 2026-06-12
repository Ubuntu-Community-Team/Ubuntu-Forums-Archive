---
title: "T900 dual digitizer issues"
date: 2010-05-16
forum: Hardware
---

### Post by njustn on 2010-05-16
Hi,

I am a new forum user, but a long time linux/ubuntu user.  Just got a new fujitsu T900 tablet with both pen and touch input on it, and can't seem to get the touch working.  I've worked with serial pen tablets for years now, and have that working fine in lucid, but the touch portion isn't recognized at all.  It doesn't even show up in xinput (pasted at the bottom) or xsetwacom list.

I've done some searching around in the forum, but didn't find anything with a clear solution.  Also tried installing the current linuxwacom, but lost all tablet support when that went in.  Any thoughts on a place to start?

njustn@ubuntu:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                         id=16    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Power Button                                id=10    [slave  keyboard (3)]
    &#8627; CNF8248                                     id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

---

### Post by njustn on 2010-05-16
To my surprise, I was wrong about the pen tablet working properly.  The pen is detected, and will move the cursor, but xsetwacom claims it can't find either device when I try and change parameters.  This is a new one on me.

njustn@ubuntu:~/scripts$ xsetwacom --list
Serial Wacom Tablet eraser ERASER    
Serial Wacom Tablet STYLUS    
njustn@ubuntu:~/scripts$ xsetwacom  --get stylus rotate
Cannot find device 'stylus'.
njustn@ubuntu:~/scripts$ xsetwacom  --get eraser rotate
Cannot find device 'eraser'.

---

### Post by njustn on 2010-05-16
Found the solution to the touch problems, udev rules from this bug report worked perfectly.

[https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/522318](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/522318)

That said, now xsetwacom --set rotate CW now crashes X... so... yeah that's a problem.

---

