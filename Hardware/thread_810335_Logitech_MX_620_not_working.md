---
title: "Logitech MX 620 not working"
date: 2008-05-28
forum: Hardware
---

### Post by dimk1 on 2008-05-28
The problem is well known, however it seems that i might be doing something worg and my buttons in my MX 620 Logitech mouse are not working.

First things first, here is the output of the xev command

1. Left Button -> Button 1
2. Right Button -> Button 3
3. Backwards Thumb Button -> Button 2
4. Forward Thumb Button -> Button 3
5. Scroll wheel up -> Button 5
6. Scroll wheel down -> Button 4
7. Push wheel down -> Button 2
8. Push Wheel left -> not recognized
9. Push Wheel right -> not recognized
10. Search Button -> not recognized

First of all you can see that some buttons are configured twice, so the first thing to do is to identify them correctly. HOW?
And then how to make them work in firefox and dolphin for example?
Opposed to xev, i have installed vmwheel which does not recognize any of my buttons except from scroll up and down!!

Any ideas??

---

### Post by ascendant on 2009-05-03
I'm running gentoo and have a similar problem.
I had a Logitech MX 600, some buttons were duplicated, particularly the forward and back thumb buttons. This is according to xev.
I've never heard of vmwheel.  The forward and back buttons work in Firefox without any action so I can't help you there.  I think it was a Firefox problem, so it may be fixed by now.
Anyway, it broke and I warrantied it for a MX 620.
Here are the results from xev:
Left, middle, right: 1, 2, 3
Backward: 8
Forward: 9
MWheel up, down: 4, 5
MWheel tilt: unrecognised

The search button is a different story: xev originally recognized it as keycode 229 with no Sym.  I used ~/.Xmodmap to map it to XF86Search.
This is because it is not a mouse button, but rather a keyboard button. (the mouse presents a mouse device and a keyboard device to X).

Anyway, does anyone know how to get X to recognize the mousewheel tilts?  There is no response from xev when I tilt the mousewheel.

---

