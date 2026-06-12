---
title: "Problem with screen rotating on Thinkpad X60 tablet"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by Tu13erhead on 2008-02-25
I got a Thinkpad X60 this weekend and I really enjoy it.  I've got most things working, all I have left is sound and screen rotation.  I'm working on the latter and having issues.

If I rotate the screen to the left or right, it rotates but doesn't appear to change resolutions.  That is, there's a big black blank spot at the "bottom" of the screen, and it also sticks off the side.  If I invert the screen, I can move the mouse, but that's it.

This happens both with xrandr and Screen Resolution.  I have to restart X or let SR put it back for me.

Any ideas?

Thanks!

---

### Post by Tu13erhead on 2008-02-26
Bueller...Bueller...

---

### Post by Tu13erhead on 2008-02-28
After some searching it seems the culprit is compiz-fusion.  If I disable it, the screen appears to rotate just fine.

Anyone else experienced this, or gotten xrandr working with compiz-fusion?

---

### Post by Yellow Pasque on 2008-02-28
Perhaps you should try using the 'i810' driver instead of 'inte' or vice-versa depnding on what you're using now.
[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950)

---

### Post by schmolch on 2008-02-28
It's a known bug, compiz doesn't work with randr.
They consider it a low priority bug so don't hold your breath.

PS: If your screen is getting very slow when rotated you have to disable DRI.
I'm using a x60t myself.

---

### Post by Danners on 2008-03-07
> **schmolch said:**
> It's a known bug, compiz doesn't work with randr.
They consider it a low priority bug so don't hold your breath.

PS: If your screen is getting very slow when rotated you have to disable DRI.
I'm using a x60t myself.

That sucks, I use my laptop in tablet mode loads and have just discovered the wonders of compiz. I can't believe they consider it a low priority bug, I'm sure it affects loads of people. I bet it's just more hassle than it's worth to fix.

---

### Post by Tu13erhead on 2008-03-07
Is there any way we can get the priority increased?  Will everyone here complaining on the bug page help?

---

