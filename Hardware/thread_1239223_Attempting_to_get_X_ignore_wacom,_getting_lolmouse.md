---
title: "Attempting to get X ignore wacom, getting lolmouse in return"
date: 2009-08-13
forum: Hardware
---

### Post by cheerybounce on 2009-08-13
I've written a file: /etc/hal/fdi/policy/no-wacom.fdi
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
        <device>
                <match key="info.product" contains="Wacom Bamboo">
                        <remove key="input.x11_driver"/>
                </match>
        </device>
</deviceinfo>

```

I installed the tablet like usual. So the tablet works nice on xorg. Though the problem is I want to use it through evdev, not through xorg because I want to get the absolute coords and not some damn pixel coords.

The trouble is my Wacom Bamboo starts freaking me out with the pad buttons. Button labeled 'FN1' starts behaving like it was a right mouse button and the another labeled '<' would like to be a middle-button. (Basicly the left side-buttons, but right-side buttons neither seem to work through evdev)

[IMG]http://advocatesstudio.files.wordpress.com/2008/08/bamboo.jpg[/IMG]

This is obviously not nice, I'd also want to use buttons through evdev without X hijacking them. :(

---

### Post by cheerybounce on 2009-08-13
Gah.. seems like it does work okay, I tried it errorneously.

---

### Post by Favux on 2009-08-13
Hi cheerybounce,

Well, given that I don't quite understand what you're trying to do, I guess you could check if X's button map is applying.

Get the "name" with:
```
xinput list | grep 'id='
```
and to view current button map:
```
xinput get-button-map "name"
```
and to change it you would say:
```
xinput set-button-map "name" 1 2 3
```
to
```
xinput set-button-map "name" 1 3 2
```
And then plug the line into plug that line into ~/.xstartup or other init file.

[http://tronche.com/gui/x/xlib/events/keyboard-pointer/keyboard-pointer.html#XButtonEvent](http://tronche.com/gui/x/xlib/events/keyboard-pointer/keyboard-pointer.html#XButtonEvent)

---

