---
title: "Need an X-Org Expert for getting a Wacom Intuos to work!"
date: 2010-07-15
forum: Hardware
---

### Post by ManDay on 2010-07-15
Hello, so everyone I've asked is more or less clueless. I've worked all my way through the Ubuntu-Wiki, Wacom Linux Project page, various other resources and all possible man pages I could find. I can proudly claim that I think to have pinned the problem down to an XOrg specific problem but that's as far as I can get with my limited understanding of the XServer.

Config:

Wacom Intuos4
Lucid
2.6.32-23 generic all the way through
Tried with both KOs, the vanilla one and the one I compiled from the Wacom Linux Project
X-Org module is the one from the reps because that appears to be the latest.

Ok, skipping the part where I tried everything out and coming straight to the part where I tell you what I think the problem is - first, the problem itsself:

The Stylus works perfectly fine, configuration in xorg.conf and HALD included, no issues there. Eraser - well, basically same device with another Driver option - too.

Pad? No. If I touch the touchring, press one of the buttons the according action is executed but at the same time the mouse pointer jumps to [0,0] which messes everything up.

Why is that?

I think I found the reason using xinput to observe the events emited from the driver. Where I want the touch ring to provide information about it's radial touch position, that very position appears to be interpreted as pointer position!

Yes, see for yourself: xinput with first all buttons pressed in order and then dragged on the ring (red):

> xinput --test 8
button press   1 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button release 1 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button press   2 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button release 2 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button press   3 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button release 3 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button press   8 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button release 8 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button press   9 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button release 9 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button press   10 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button release 10 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button press   11 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button release 11 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button press   12 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button release 12 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button press   13 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
button release 13 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=0 
[COLOR=Red]motion a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=15 
motion a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=12 
button press   4 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=9 
button release 4 a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=9 
motion a[0]=0 a[1]=0 a[2]=0 a[3]=0 a[4]=0 a[5]=9[/COLOR]

The button event is properly emitted but at the same time the scrolling coordinates are transmitted in a tuple which is interpreted as mouse poisition.

THAT IS WHAT I WANT TO SOLVE.

I already tried making the Pad-Device non-core in xorg.conf but that wholly disabled it. Now I'm out of options.

Thanks!

PS: Any idea why xxd does display nothing on the wacom device (never)

---

### Post by ManDay on 2010-07-15
[https://bugs.launchpad.net/linuxwacom/+bug/560180](https://bugs.launchpad.net/linuxwacom/+bug/560180)

---

### Post by ManDay on 2010-07-15
Please take my excuse, I've not noticed that the lates xf86-input-wacom solves this problem which it did for me.

---

