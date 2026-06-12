---
title: "trackpad &quot;gestures&quot;"
date: 2005-01-09
forum: Hardware &amp; Laptops
---

### Post by leviathon on 2005-01-09
Does anyone know how to disable (or modify) the way the trackpad interacts with firefox? I've noticed the bottom 1/3 or so of the tackpad provides back/forward functionality which although cool really annoys me.

---

### Post by Foxfyre on 2005-01-20
Me too. I don't know how to fix it. If someone knows, please share!

---

### Post by Foxfyre on 2005-01-20
Found it! Searched for 'pad firefox' on the forums and found two threads:

First found [this one](http://ubuntuforums.org/showthread.php?t=3478&highlight=pad+firefox) which in turn points to [this one](http://ubuntuforums.org/showthread.php?t=3994).

Worked like a charm for me, haven't had it happen since I made these changes.

---

### Post by jerome bettis on 2005-01-20
no no no

don't do that, it's stupid.  i didn't really read those links, but it looks like it disables the horizonal scrolling of the touchpad all together - not just in firefox.  this is no good obviously.

i found this to be pretty damn annoying myself and fixed it by typing about:config in the firefox address bar.  i changed the value of mousewheel.horizscroll.withnokey.action to 0 (it was 2 i think).  

i can move my finger down there in firefox and it doesn't switch pages.  horizontal scroll works outside of firefox.  i haven't tried scrolling horizontally in firefox, but if it doesn't work, maybe changing it to 1 is right instead of 0.

---

### Post by ddixonr on 2008-03-23
That's perfect! This solution worked perfectly! Thank-you, Thank-you. That function is really annoying for those with larger fingers.

---

