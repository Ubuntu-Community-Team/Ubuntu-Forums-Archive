---
title: "Use extra Mouse buttons"
date: 2010-05-12
forum: Hardware
---

### Post by himbert on 2010-05-12
Hello everybody, I need your help.

I want to set the thumbkeys of my Microsoft SideWinder X8 Mouse.
I want Crtl on button 8 and Shift on button 9 (got the numbers with event tester)

I've already tried to edit the xorg.conf file but it didn't work, or maybe I did something wrong.

I'm really new to Ubuntu (10.04) and I don't know much about it, so be a little patient with me, and explain me things good understandable please. :)

Here is the xinput list if that helps:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; stylus                                  	id=6	[slave  pointer  (2)]
&#9116;   &#8627; eraser                                  	id=7	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® SiderWinderTM X6 Keyboard	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger          	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger pad      	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® SideWinder(TM) 2.4GHz Transceiver	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® SideWinder(TM) 2.4GHz Transceiver	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® SiderWinderTM X6 Keyboard	id=10	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® SideWinder(TM) 2.4GHz Transceiver	id=14	[slave  keyboard (3)]

```

I Installed xbindkeys and xautomation and made a file named .xbindkeysrc
```
"xte 'control'"
b:8  # Maustaste 8

"xte 'shift'"
b:9  # Maustaste 9
```

like it's written in the Wiki. But it doesn't work.

I can post the Xorg.conf too if that is requiered, but I deleted the changes, because they didn't work.


I'd be very thankfull if someone could help me.

---

### Post by himbert on 2010-05-13
Is the anyone who can help me?

---

### Post by himbert on 2010-05-13
bump

---

### Post by himbert on 2010-05-14
Please help:(

---

### Post by dmitryilyin on 2010-06-01
Try keydown +
  Shift_L
  Shift_R
  Control_L
  Control_R

instead of control and shift

"xte 'keydown Shift_L'"
b:8

but it will press button, to release you can try:

"xte 'keyup Shift_L'"
release + b:8

[http://linux.die.net/man/1/xbindkeys](http://linux.die.net/man/1/xbindkeys)
[http://linux.die.net/man/1/xte](http://linux.die.net/man/1/xte)

---

