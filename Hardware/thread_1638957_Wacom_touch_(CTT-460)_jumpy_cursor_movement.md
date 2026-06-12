---
title: "Wacom touch (CTT-460) jumpy cursor movement"
date: 2010-12-06
forum: Hardware
---

### Post by Stormherz on 2010-12-06
I'm using ubuntu 10.04 and yesterday I've bought subj device, installed linuxwacom drivers and so on (following this howto [http://ubuntuforums.org/showthread.php?t=1515562]("http://ubuntuforums.org/showthread.php?t=1515562")), it's working now, but cursor movement is really jumpy. It moves with step around 5px. Trying to solve it I've found that if I set "Device Accel Constant Deceleration" parameter with xinput cursor moves much smoother and much slower, unfortunately :( How can I solve this problem?

---

### Post by Favux on 2010-12-06
Hi Stormherz,

Welcome to Ubuntu forums!

Are you using one of the sample scripts?  Of course you'd discard the stylus and eraser sections.  If so try setting RawSample to 1.

---

### Post by Stormherz on 2010-12-07
> Hi Stormherz,

Welcome to Ubuntu forums!

Thanks!

> 
Are you using one of the sample scripts?  Of course you'd discard the stylus and eraser sections.  If so try setting RawSample to 1.

No, no sample scripts were used. It looks better when changing RawSample to 1 or 0. Can you explain why is this happening? Can movement be smooth as mouse movement or pen movement in wacom pen tablet? It seems like cursor is moving aligned - like keyboard-driven cursor.

---

### Post by Favux on 2010-12-07
Hi Stormherz,

Good.  RawSample is how many data points are being looked at, so by going to 1 or 0 you are increasing them.

Right now the touch code is in flux.  MT (multitouch) code is being introduced to the X driver and I believe the MT code has been accepted into the 2.6.37 kernel.  By that I mean the officially sanctioned MT code.  Wacom had MT before the specification came out.  Which is why there is all the confusion.  So there are also changes going on to the filters.  Chris has a new patch that he thinks helps:  [http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTinzj9jPn4-ZqaMWcLuuCYORV8s1UTL8ZN%3DX3Kx_%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTinzj9jPn4-ZqaMWcLuuCYORV8s1UTL8ZN%3DX3Kx_%40mail.gmail.com&forum_name=linuxwacom-devel)  We'll see.

I'm working on updating the script.  A proposed version is in the last few pages of the thread.  Probably post it tomorrow.

---

### Post by Stormherz on 2010-12-07
> 
Good.  RawSample is how many data points are being looked at, so by going to 1 or 0 you are increasing them.

Right now the touch code is in flux.  MT (multitouch) code is being introduced to the X driver and I believe the MT code has been accepted into the 2.6.37 kernel.  By that I mean the officially sanctioned MT code.  Wacom had MT before the specification came out.  Which is why there is all the confusion.  So there are also changes going on to the filters.  Chris has a new patch that he thinks helps:  [http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTinzj9jPn4-ZqaMWcLuuCYORV8s1UTL8ZN%3DX3Kx_%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTinzj9jPn4-ZqaMWcLuuCYORV8s1UTL8ZN%3DX3Kx_%40mail.gmail.com&forum_name=linuxwacom-devel)  We'll see.

I'm working on updating the script.  A proposed version is in the last few pages of the thread.  Probably post it tomorrow.

I see.. Is this a problem of touch input devices or with MT only? 
Is there a way to force tablet to work as non-MT device? (like a simple mouse)

---

### Post by Favux on 2010-12-07
Single finger touch seems good.  I don't know for sure if you can do that with a Bamboo touch.  You could change gestures to "off" and Mode from the default "Relative" to "Absolute".  If it lets you change Mode that may force it to behave like Tablet PC single finger touch.  Comment out ScrollDistance and ZoomDistance.

Let me know how it goes.

---

### Post by Stormherz on 2010-12-07
> Single finger touch seems good.  I don't know for sure if you can do that with a Bamboo touch.  You could change gestures to "off" and Mode from the default "Relative" to "Absolute".  If it lets you change Mode that may force it to behave like Tablet PC single finger touch.  Comment out ScrollDistance and ZoomDistance.

Let me know how it goes.

Ok, I played a bit with xsetwacom and xinput and with this settings it works fine, but there is 2 annoying problems:
- sometimes cursor just randomly jumps to some point on the screen, may it be interference with connected mouse?
- I can't quite understand what makes a double click active. One time a need to tap once, and other (in the same situation) twice.


```
Device 'Wacom Bamboo 2FG Finger touch':
Device Accel Profile (251):	0
Device Accel Constant Deceleration (252):	1.000000
Device Accel Adaptive Deceleration (254):	1.000000
Device Accel Velocity Scaling (255):	1.000000
Wacom Tablet Area (261):	0, 0, 480, 320
Wacom Display Options (265):	-1, 0, 1
Wacom Capacity (266):	3
Wacom Pressure Threshold (267):	27
Wacom Sample and Suppress (268):	1, 2
Wacom Enable Touch (269):	1
Wacom Hover Click (270):	0
Wacom Enable Touch Gesture (271):	0
```

---

