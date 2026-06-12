---
title: "Touch screen not functioning right (2310ti)"
date: 2011-03-15
forum: Hardware
---

### Post by Smigh on 2011-03-15
I have this touchscreen at work that we're going to use with a kiosk application in a store. We thought of deploying it with Ubuntu but now that we're testing it, we see that it has a strange behavior that doesn't happen in windows.

If I touch the screen, the system registers the click but not the mouse movement to the position where I touched the screen... but if I hold the finger down and move it around, it registers the movement perfectly. So, for example, if I drag the pointer on top of the close button of a window in the middle of the screen, then if I stop touching it, then touch the bottom left corner of the screen (or any part of it), the window closes and the pointer doesn't move to the place I touched.

Can this be a driver issue? How would I go about diagnosing and solving this issue?

---

### Post by Smigh on 2011-03-15
Never mind. Installed utouch, restarted and it started working like expected.

---

