---
title: "Scroll Lock"
date: 2008-09-15
forum: Hardware
---

### Post by shortylonglegs on 2008-09-15
My scroll lock key doesn't work in Gnome.  It works fine in the ttys but doesn't work in Gnome.  This is only a problem because I use a kvm switch that is triggered by the scroll lock key, but the OS has to recognize it for the switch to recognize it.  Its not being blocked by the switch either, because I have connected my keyboard directly to the usb port, as well as using the built in keyboard (its a laptop) and nothing works.  Any ideas?

---

### Post by baggins on 2008-09-15
To check if your Scroll Lock presses is captured, try running xev from a terminal. Place your cursor on the little window that appears.
Press the Scroll Lock, if the xserver catches the scroll lock, you ought to see lines like these:
```
KeyPress event, serial 31, synthetic NO, window 0x5000001,
    root 0x13b, subw 0x0, time 114120794, (71,96), root:(889,383),
    state 0x10, keycode 78 (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x5000001,
    root 0x13b, subw 0x0, time 114120887, (71,96), root:(889,383),
    state 0x10, keycode 78 (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
in the terminal window.

 -- Jon

---

### Post by shortylonglegs on 2008-09-15
Ok, it looks like it being recognized, but it still isn't doing anything

```

KeyPress event, serial 31, synthetic NO, window 0x3a00001,
    root 0x59, subw 0x0, time 91918418, (355,393), root:(362,444),
    state 0x10, keycode 78 (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3a00001,
    root 0x59, subw 0x0, time 91918522, (355,393), root:(362,444),
    state 0x10, keycode 78 (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by baggins on 2008-09-15
Ok just did a few tests:
First I tried to use scroll lock in a terminal. No joy seems that gnome-terminal uses ctrl-s for scroll lock.

Next I tried playing around with the keyboard shortcuts (Menu: System -> Preferences -> Keyboard Shortcuts). Result; ScrollLock works fine, it's just that no function have been attached to it, so it's a dead key press.

Just for fun I tried adding a second keyboard layout (Menu: System -> Preferences -> Keyboard , layout tab) and set up Scroll Lock to switch between the two. Works fine!
So it's not Scroll Lock that is giving you the problems, it's how it's interpreted. 

You wrote that the kvm switch is triggered by the shift key. I assume that you mean that it's triggered by the scroll lock key (why else worry about it ;) ). Now I don't know what you need it assigned in order for it to work for you. Maybe the documentation for the kvm switch can help.

-- Jon

---

### Post by shortylonglegs on 2008-09-15
Yes, I meant the scroll lock, sorry.  Thanks for the help, its kind of working, its doing what I assigned the shortcut too, but the switch still isn't working right.  I'll keep working on it.

---

### Post by stinkinrich88 on 2008-11-03
This one worked for me:

[http://linuxtechie.wordpress.com/2008/04/07/getting-scroll-lock-to-work-in-ubuntu/]("http://linuxtechie.wordpress.com/2008/04/07/getting-scroll-lock-to-work-in-ubuntu/")

---

### Post by redhatpat on 2009-01-20
My logitech cordless keyboard doesn't have a scroll lock key to switch the KVM, but I came across a post on another board that copies the functions:
Function key + Pause/Break twice, then the right or left arrow.

My keyboard has a blue colour on the function key, and the Pause/Break key has a blue square with a down arrow, must be a scroll lock picture.

Anyway, that switches the KVM for me! No key re-mapping required.

---

