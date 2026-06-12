---
title: "Bamboo Touch and Pen support"
date: 2010-02-21
forum: Hardware
---

### Post by whackedspinach on 2010-02-21
I'm trying to get Wacom's Bamboo Fun Touch and Pen working.  I know there are lots of development threads about this, but all the instructions seem to be a few months old, in different stages of development, and over my head.  I tried following a few, but with no luck.  Can anyone point me to the most up to date/easy/best guide to getting Bambbo Fun Touch & Support on Ubuntu 9.10?

---

### Post by portets on 2010-02-21
here's my thread from two days ago, favux helped me alot. hopefully it helps you.

[http://ubuntuforums.org/showthread.php?t=1410430](http://ubuntuforums.org/showthread.php?t=1410430)

just ask if you need some help. i *might *be able to help you.
by the way, touch doesn't completely work yet, but it should soonish it seems.

---

### Post by whackedspinach on 2010-02-21
Okay, I managed to get it to work using this excellent guide ([http://ubuntuforums.org/showpost.php?p=6546012&postcount=1]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") )

Unfortunately, I cannot get wacomcpl to work correctly. When I open up wacomcpl, all I see are stylus, eraser, and pad.  If I try to click on them I get these error messages:
eraser:
```
unknown device "eraser" or it is currently a core device
unknown device "eraser" or it is currently a core device
    while executing
"wacomxi::bindevent . $device <ButtonPress> """
    (procedure "updateDevice" line 12)
    invoked from within
"updateDevice"
    (command bound to event)
```
pad:
```
unknown device "pad" or it is currently a core device
unknown device "pad" or it is currently a core device
    while executing
"wacomxi::bindevent . $device <ButtonPress> """
    (procedure "updateDevice" line 12)
    invoked from within
"updateDevice"
    (command bound to event)
```
or
```
can't read "hasPad(209)": no such element in array
can't read "hasPad(209)": no such element in array
    while executing
"if { $hasPad($model) } {
		createPanel 0 1 0 0
	    }"
    (procedure "updateDevice" line 25)
    invoked from within
"updateDevice"
    (command bound to event)
```
stylus:
```
unknown device "stylus" or it is currently a core device
unknown device "stylus" or it is currently a core device
    while executing
"wacomxi::bindevent . $device <ButtonPress> """
    (procedure "updateDevice" line 12)
    invoked from within
"updateDevice"
    (command bound to event)
```

There is another error I get on eraser or stylus:
```
can't read "isLCD(209)": no such element in array
can't read "isLCD(209)": no such element in array
    while executing
"if { ![ string compare $type "pad" ] } {
	    if { $hasPad($model) } {
		createPanel 0 1 0 0
	    }
	} elseif { ![ string compare $type "touch" ] } {
..."
    (procedure "updateDevice" line 24)
    invoked from within
"updateDevice"
    (command bound to event)
```

Anyone know what is going on here?  Any help is appreciated!

EDIT: Yeah, thanks portets.  I actually read your thread and it helped me get it working.

---

### Post by portets on 2010-02-21
yeah, i get the same errors through wacomcpl. favux said that it's probably broken for some people in 0.8.5-10 due to recent work. i'm hoping for it to be fixed in 0.8.5-11

---

### Post by whackedspinach on 2010-02-21
Alright cool.  Thanks for your help.  This is fine for now.

---

### Post by portets on 2010-02-21
wait, sorry!

my errors are a little different. they might be related though

---

