---
title: "A little mouse/tablet help needed..."
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by mikesname on 2005-04-25
Hello there,

I've recently installed Hoary 5.04 on my Thinkpad T30 and am generally getting on well with it.  However I'd be most grateful if anyone has any suggestions for sorting out some input device problems.  I'm using:

- The Thinkpad's Trackpoint (my model has no Trackpad)
- A rather cheap but handy Genius tablet

Both devices work but the tablet has some configuration problems:

- The buttons assignments are wrong
- It works in relative mode rather than absolute, so is a bit awkward to control

So far I've been able to change the button assignments using xmodmap, but this also changes the trackpoint - not what I want to happen.

I have installed Xinput and I gather this can change devices individually, and also alter the relative/absolute modes, but I think the problem is due to the trackpoint and tablet working as the 'same' device.

Here's my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

Likewise, the xinput list:

```
"Configured Mouse"      id=0    [XPointer]
        Num_buttons is 5
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is 1023
                Resolution is 1
        Axis 1 :
                Min_value is 0
                Max_value is 767
                Resolution is 1
"Generic Keyboard"      id=1    [XKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255

```

Does anyone know what I have to do to get the trackpoint and tablet working as separate devices?  I've tried fiddling with my xorg.conf but I don't really know what I'm doing with these things!

Any help gratefully accepted.

Thanks,
Mike

---

### Post by alastair on 2005-04-25
You probably just need an extra device section in your X config file. A google search might help you figure this out e.g.

[http://www.kalibalik.dk/anders/software/easypen/](http://www.kalibalik.dk/anders/software/easypen/)

Xorg will be similar to XFree (but maybe watch out for device names/paths themselves).

---

