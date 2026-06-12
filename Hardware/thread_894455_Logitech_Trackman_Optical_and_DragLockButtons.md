---
title: "Logitech Trackman Optical and DragLockButtons"
date: 2008-08-19
forum: Hardware
---

### Post by omahn on 2008-08-19
I've recently purchased a Logitech Trackman Optical mouse to try and ease the pain from RSI. It seems to be doing a good job. I've successfully got all the buttons, except one working with the following xorg config:
```

  Driver "evdev"
  Option "Device" "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
  Option "Buttons" "10"
  Option "DragLockButtons" "7 1"
  Option "ZAxisMapping" "4 5"
```

I also have the following in /etc/X11/Xmodmap:

```
pointer = 1 2 3 4 5 8 9 7 6 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32
```

(Although I suspect I only need the first 11 values).

Unfortunately I've not been able to get the 'lock' button to work with Ubuntu. In theory, pressing the lock button should hold down button 1, the left mouse button, to allow easier dragging of objects around the screen.

Using the xev tool I've verified that the lock button returns button id 7 yet my 'DragLockButtons' entry in the xorg conf doesn't work. The button doesn't appear to be doing anything.

Does anyone have any ideas what could be causing this or any ways I can investigate further? I'm a bit stuck.

Thanks..

---

### Post by KingCharles on 2008-10-15
Hi there.
I just bought a Kensington Expert Mouse (trackball), and was setting it up.

I think that the "DragLockButtons" works the following way, by I could be mistaken:

You press the your draglock button plus say button one, that will initiate a lock for button 1 so you can drag objects around.

You can also press your draglock button and say button 2, and that way you would be able to "middle drag" objects also.

To get out of drag lock, you press the same combination again. Now I could be wrong since I just started playing around with it, but it is worth trying.

I only have one button under my Xorg's "DragLockButtons" entry (mine is number 6).

Let me know :]

*Edit:
Actually I just realized that the "DragLock" feature only works if you use the "Mouse" driver. I changed my setting so it uses "evdev", and although it gives an incredible smooth movement of the cursor, it seems it doesn't take the "DragLock" functionality.

---

### Post by omahn on 2008-11-11
> **KingCharles said:**
> Hi there.
*Edit:
Actually I just realized that the "DragLock" feature only works if you use the "Mouse" driver. I changed my setting so it uses "evdev", and although it gives an incredible smooth movement of the cursor, it seems it doesn't take the "DragLock" functionality.

I didn't realise that and I was using the evdev driver. Unfortunately changing to the 'Mouse' driver leaves me with no mouse working at all. I've actually got used to the trackball without the drag lock button now but it was worth a try. :-)

Thanks, Paul.

---

