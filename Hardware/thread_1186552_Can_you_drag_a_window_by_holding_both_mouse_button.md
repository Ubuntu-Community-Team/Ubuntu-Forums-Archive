---
title: "Can you drag a window by holding both mouse buttons?"
date: 2009-06-13
forum: Hardware
---

### Post by etnpnys on 2009-06-13
In "Window Preferences" you can select either Control, Alt, or Super to let you hold that key and drag a window around. Is there a way to set this to the right mouse button so that you can just hold down both mouse buttons to drag the window? 

The reason I ask is because I think it's somewhat counterintuitive to have to search for a key on the keyboard to press in order to 'make it more convenient' to drag a window around... In the end, it ends up actually taking me MORE time to do it this way than to just grab the window's top bar (whatever that's called). 

I think this would be much more ergonomic and make more sense to do it with both mouse buttons - it would even feel more like you just physically grabbed the window and are throwing it around! AFAIK, you can't even do this on a Mac, and they're the magic usability people...

---

### Post by cubeist on 2009-06-13
> **etnpnys said:**
> In "Window Preferences" you can select either Control, Alt, or Super to let you hold that key and drag a window around. Is there a way to set this to the right mouse button so that you can just hold down both mouse buttons to drag the window? 

The reason I ask is because I think it's somewhat counterintuitive to have to search for a key on the keyboard to press in order to 'make it more convenient' to drag a window around... In the end, it ends up actually taking me MORE time to do it this way than to just grab the window's top bar (whatever that's called). 

I think this would be much more ergonomic and make more sense to do it with both mouse buttons - it would even feel more like you just physically grabbed the window and are throwing it around! AFAIK, you can't even do this on a Mac, and they're the magic usability people...

Personally, I am not sure if it would be more intuitive...it feels a bit awkward.  Nonetheless, it likely is not possible from a technical (xinput) point of view.  The problem is that the computer can't recognize simultaneous dual input, ie, both buttons being pressed at once for 'one' input... instead the computer sees button one being pressed, then a millisecond later, button two (or vice versa) and translates this into the action of "oh, the user has just pushed button one and THEN button two".  What you are asking the computer to recognize is "ah, the user has pushed button one AND button two"

AFAIK this type of input is not available in X...yet, but it is being worked on.

Edit -
But, if you use compiz, you can go to the 'move' plugin and set a custom mouse button to drag windows...so if you have a multi-button mouse, you can use one of the extra buttons.

---

### Post by ajgreeny on 2009-06-13
Have I missed the point of this post?  What is the reason for wanting anything other than the left mouse button on the window title border at the top, or Alt with the cursor anywhere in the window to move it.  As I say, I may have missed some good reason for this question, but I certainly can't see one.

---

### Post by cubeist on 2009-06-13
I think the OP is looking to find a more streamlined method of moving windows.  I agree, the existing methods work AOK, but I can also understand trying to find ways to improve and enhance a work flow.  Sometimes your non-mouse hand is busy (on the phone, eating ice cream, etc.) and the title bars aren't always visible...ie, fullscreen.

---

### Post by ajgreeny on 2009-06-13
OK, gotcha. Now I see the reasoning.

---

