---
title: "MPX: Works, but visual glitches"
date: 2011-04-18
forum: Hardware
---

### Post by Svip on 2011-04-18
So after getting MPX working with 10.10 (read [this for how](http://alec.mooo.com/mpx.html)), as I have three mouse input devices to my desktop.

Unfortunately, the additional cursors seems to have a lot of glitches around their positions (in an area of 50x50 pixels around the cursor).  Which is an issue to me, because one of the additional input devices is a Wacom Bamboo Pen, and thus GIMP displays some visual glitches as I draw, which is unfortunate.

I thus wonder if anyone has any experience with this and know how to fix it?  In addition, I have yet to restart X, but I wonder if the settings done by **xinput** will remain after a restart.

I have an additional query on the matter, I have seen videos of MPX where each cursor had their own colour; is this possible?

---

### Post by brnetonboy on 2011-04-24
This is so awesome, thank you! After literally waiting years, I finally got multiple cursors to work with just a few minutes of following instructions. That was amazingly easy!

It still seems really buggy. Clicking seems to be erratic, and tasks like click-drag are not reliable. Hopefully we can work out the bugs on this soon and get it up to real working order!

---

### Post by Svip on 2011-04-24
You are welcome.  According the same guide, compositing - such as compiz which comes default with Ubuntu - causes issues; turning them off seems to help with most of the glitches.

---

### Post by brnetonboy on 2011-04-24
Oh, that makes sense. Can I just uninstall compiz, or would that break things? (I'm using Maverick.)

---

### Post by Svip on 2011-04-24
Compiz and compositing can be turned off in System > Preferences > Appearance > Visual Effects > None.

This has improved my extra cursor somewhat, but it will occassionally flicker, but the surrounding glitches are gone.

---

