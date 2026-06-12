---
title: "Wireless presenter: buttons don't work"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by mrsva on 2005-05-22
Hi all!

I have a wireless presenter (USB mouse with laser pointer) that isn't recognized well in linux. It has a trackball in the upper side together with 4 buttons: left/right mouse click and PgUp/PgDown.

The trackball works fine and (to my surprise) the PgUp/PgDown buttons also. The problem is with the left/right click: they are just ignored. I tried to use xev to see what they are sending, and they don't send any code.

In windows this mouse is recognized without any extra drivers. I just plug it and it is recognized as a standard mouse, what makes me think that it should use some standard protocol and should be also recognized by linux. My other USB mouse is recognized as the same type of device by windows but this one works with linux.

I tried also a

cat /cat /dev/input/event0  # for my keyboard
cat /cat /dev/input/event2  # for my other USB mouse
cat /cat /dev/input/event4  # for the wireless presenter

When listening to event0, keys generate noise on screen but the buttons of the presenter not (PgUP/PgDown)
When listening to event2, the mouse movement and the buttons send noise
when listening to event4, only the trackball movement send noise -- no buttons send anything

Any ideas? What can I try?

Thanks!

Marcio

---

### Post by mrsva on 2005-05-24
An update here.

I booted Knoppix on the same machine and it recognized the pointer (but not my synaptics touchpad -- the machine is a notebook). Then I tried to use the X config file from Knoppix in my Ubuntu installation, but it didn't worked :(

Do you think this may be a problem with Xorg? I ask this because Knoppix still uses XFree86.

Marcio

---

