---
title: "Disabling tilt wheel in certain applications"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by greybirds on 2007-05-30
My new mouse has left-right scroll wheel functionality. I both love and hate it, depending on the app. I love it in, say, Firefox. But it makes life in Inkscape difficult and life in Blender next to impossible.

From what I xev says, dragging with the scroll wheel depressed (button 2), gets interrupted with intermittent tilt left (button 7) press/release events. A lot of them, actually. In something like Inkscape, which recognises button 2 dragging as "pan around" and button 7 as "pan right" I get erratic panning. Blender, which apparently doesn't recognise the tilt buttons at all, seems to decide the best reaction is to stop whatever it's doing (rotating and panning the view, in this case).

I have options, of course. I can disable the left-right tilt entirely, but I've gotten attached to it in apps that handle it well. Blender has a kludgy workaround involving alt-left-click, shift-alt-left-click, and control-alt-left-click that requires me to relearn years of ingrained behavior and brings my productivity to a complete halt. I could also plug in a second mouse but acceleration and sensitivity seem to be effected and the point of the new mouse was to get rid of a too-short cord.

I'm researching evdev, xmodmap, and xinput right now but haven't hit on anything useful. 

By the way, the mouse in question is a Logitech s510 and is being driven with evdev at the moment. Any help or directional pointers would be much appreciated.

---

### Post by kaiska on 2008-03-05
I have the same problem. The wheel right/left click is boring me. Have you found an issue to disable those "horizontal click" ?

---

