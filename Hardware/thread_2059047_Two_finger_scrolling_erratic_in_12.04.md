---
title: "Two finger scrolling erratic in 12.04"
date: 2012-09-17
forum: Hardware
---

### Post by Andos on 2012-09-17
Hi There

I've just installed 12.04 on my Asus Zenbook UX31.  In general everything worked perfectly out of the box.  The only problem I have is the two finger scrolling on the touchpad.  If I'm scrolling a long web page in Chrome it will jump around erratically.  

For example, it will scroll down about 10-20 lines smoothly and then suddenly jump right back to the top.  If I keep scrolling in the same motion it may then jump back to the position I started scrolling from.  Alternatively, sometimes the page position starts jumping around e.g. "bouncing" off the top of the page or flicking rapidly back and forth between two points.

This also happens in some other applications such as Spotify.  I tried switching to edge scrolling which is slightly smoother but I still see issues.  Does anyone have any idea how I can fix this?

Thanks for any help!

---

### Post by Andos on 2012-09-17
Hmm from another thread I found it seems the latest "proposed" kernel may improve matters.  Maybe I'll just have to hang tight and see what happens with that, unless anyone has any other ideas.

---

### Post by maze2 on 2012-12-13
I found why, and I made a patch.

You can find it here:
[http://ubuntuforums.org/showthread.php?t=2093793](http://ubuntuforums.org/showthread.php?t=2093793)

Or here:
[http://sentelic.pkbd.org](http://sentelic.pkbd.org)

When you have tried this, please tell me what version of the touchpad you are using. You should find it in the kernel log messages when loading the psmouse driver.

---

