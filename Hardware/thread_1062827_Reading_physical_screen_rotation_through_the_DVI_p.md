---
title: "Reading physical screen rotation through the DVI port..."
date: 2009-02-07
forum: Hardware
---

### Post by ragtag on 2009-02-07
Hi,

 I have a screen I can rotate into portrait mode. I've written a simple script that toggles the rotation of the screen, which works fine, but I have to run it by hand. When this screen is used with Windows, you can have the driver automatically detect when the screen rotates and rotate the desktop to match.

 Now, I figure the screen sends some kind of message to the machine through the DVI connection. Is there any way to get a hold of this message so I could use it to rotate the desktop on Ubuntu too. Would be really cool to just be able to rotate the screen physically and have the desktop rotate too without needing to run a script or click on anything. :)

The screen is an LG Flatron Slim.

---

### Post by mamut() on 2009-02-07
can you please show us your script?
and tell us a little about your system configuration (graphics card and driver)
do you use this randr tool?

thx

---

### Post by ragtag on 2009-02-07
The script is pretty basic. Just checks what the current rotation is (probably in a non-reliable way), and then rotates the screen and wacom. I'm rotating the wacom in the oposite direction of the screen as it's more comfortable to use it that way. :)

```

#!/bin/sh
# Toggle the rotation of the screen from normal to right.
rotation=`xrandr -q | grep "default" | awk '{print $4}'`
if [ "$rotation" = "(normal" ]; then
    xrandr -o left
    xsetwacom set "stylus" Rotate CW
    xsetwacom set "eraser" Rotate CW
else
    xrandr -o normal
    xsetwacom set "stylus" Rotate NONE
    xsetwacom set "eraser" Rotate NONE
fi

```

The scrpit works nicely with my setup.

The machine has an Nvidia GeForce 6800 GT card and is running Ubuntu 8.10.

I know the screen sends some kind of signal to the graphics card when I rotate it physically, and it would be really nice if I could capture that signal and have it trigger a script like the one above. I just don't know how to capture that signal. :)

---

