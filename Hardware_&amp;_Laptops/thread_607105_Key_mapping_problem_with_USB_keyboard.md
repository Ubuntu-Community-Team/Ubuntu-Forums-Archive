---
title: "Key mapping problem with USB keyboard"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by taahwrux on 2007-11-08
I have been using Ubuntu since March 2007.  Everything is fine except the multimedia keys on my new Logitech Wave USB wired keyboard.  

The keyboard just worked right ouf of the box including the media player keys such as mute, play, pause, stop, forward, backward, etc.  Unfortunately, beside the calculator key, the rest of the multimedia keys, like Flip 3D button , Zoom in / out, Fn key , are not working at all.

And I found this one and did all the steps.
[https://wiki.ubuntu.com/KDEMultimediaKeys]("https://wiki.ubuntu.com/KDEMultimediaKeys")

Now, I got one multimedia key, which is the music key, reporting in the xev.  the other keys are just dead.

I realized that must be a problem with the linux kernel.  So i try
```
sudo getkeycodes
```
the output is:
```
Plain scancodes xx (hex) versus keycodes (dec)
0 is an error; for 1-88 (0x01-0x58) scancode equals keycode

KDGETKEYCODE: No such device
failed to get keycode for scancode 0x5a
 0x58:   88  89
```

Is there anyone here can help me solve this problem?   Some google results told me that that was the problem with the USB keyboard.  
does that mean that the "getkeycodes" only works with PS/2 connector?

---

### Post by lordkalkin on 2007-12-09
*bump*

I just bought one of these as well, and i would like to know if it's possible to get these buttons to work somehow.

---

### Post by mooglinux on 2007-12-25
I am having the same issue. Mute, volume up, volume down, stop, play/pause, next, previous, and the music button all work. the rest of the extra keys do not, however. That would be the window switcher, Fn, zoom in and zoom out, gadget, photo, and calculator. the power button puts the system into hybernate, rather than pulling up the shutdown menu like pressing the icon on the status bar does. Pressing these keys in xev does not evoce a responce, even the ones that do work.

Running getkeycodes brings up this:
```
Plain scancodes xx (hex) versus keycodes (dec)
for 1-0 (0x01-0x00) scancode equals keycode

 0x00:    0   1   -   -   -   -   -   -
 0x08:    -   -   -   -   -   -   -   -
 0x10:    -   -   -   -   -   -   -   -
 0x18:    -   -   -   -   -   -   -   -
 0x20:    -   -   -   -   -   -   -   -
 0x28:    -   -   -   -   -   -   -   -
 0x30:    -   -   -   -   -   -   -   -
 0x38:    -   -   -   -   -   -   -   -
 0x40:    -   -   -   -   -   -   -   -
 0x48:    -   -   -   -   -   -   -   -
 0x50:    -   -   -   -   -   -   -   -
 0x58:    -   -   -   -   -   -   -   -
 0x60:    -   -   -   -   -   -   -   -
 0x68:    -   -   -   -   -   -   -   -
 0x70:    -   -   -   -   -   -   -   -
 0x78:    -   -   -   -   -   -   -   -

Escaped scancodes e0 xx (hex)

e0 00:    -   -   -   -   -   -   -   -
e0 08:    -   -   -   -   -   -   -   -
e0 10:    -   -   -   -   -   -   -   -
e0 18:    -   -   -   -   -   -   -   -
e0 20:    -   -   -   -   -   -   -   -
e0 28:    -   -   -   -   -   -   -   -
e0 30:    -   -   -   -   -   -   -   -
e0 38:    -   -   -   -   -   -   -   -
e0 40:    -   -   -   -   -   -   -   -
e0 48:    -   -   -   -   -   -   -   -
e0 50:    -   -   -   -   -   -   -   -
e0 58:    -   -   -   -   -   -   -   -
e0 60:    -   -   -   -   -   -   -   -
e0 68:    -   -   -   -   -   -   -   -
e0 70:    -   -   -   -   -   -   -   -
e0 78:    -   -   -   -   -   -   -   -

```
this is the wired logitech wave keyboard, not that that makes a difference how the keys are mapped.

---

### Post by sweetthdevil on 2008-01-22
Just bought one of them! did you manage to get the extra keys working?

---

### Post by mooglinux on 2008-01-22
No, no solutiongs have presented themselfves. apparently most of those keys do not give out scan codes, because i cannot seem to get them to be picked up on any program... you probably need the drivers to go read them. that goes for most of the Fn keys as well, with a couple exceptions (havent tried to retrive scancodes from any fn key combo)

---

