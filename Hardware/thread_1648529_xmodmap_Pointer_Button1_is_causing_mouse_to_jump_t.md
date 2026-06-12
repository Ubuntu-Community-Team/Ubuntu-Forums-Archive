---
title: "xmodmap Pointer_Button1 is causing mouse to jump to bottom right of screen"
date: 2010-12-18
forum: Hardware
---

### Post by daveola on 2010-12-18
I just upgraded from a Panasonic Y5 to a Panasonic Y7 laptop (love it!).

The Y series laptops have a bunch of extra keys near the space bar, so I usually map them to mouse buttons.  This worked great on my Y5.  When I tried it on my Y7, the mouse button is pressed, as expected, but the mouse jumps to the bottom right of the screen, every time.

I'm using lines such as this:


xmodmap -e "keycode 133 = Pointer_Button1"


I tried it with other keys to make sure it wasn't related to the specific keys I was choosing and had the same effect.  The actual mouse buttons on the track pad do not have this problem.  I don't know where to start debugging a keyboard problem like this, or even who to report the bug to.

Any thoughts?

---

### Post by daveola on 2010-12-20
I just discovered that this is also happening with the mousekeys accessibility, which uses the PointerButton() function in the /usr/share/X11/xkb config files.

If I move the mouse around with mousekeys after hitting the button, it's fine, but the moment I actually move the mouse after doing a pointerbutton event from a key, that's when it jumps to the bottom right of the screen.

---

