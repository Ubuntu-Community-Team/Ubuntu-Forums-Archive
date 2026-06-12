---
title: "Karmic Koala 9.10 Battery Icon"
date: 2009-10-30
forum: Hardware
---

### Post by wewantutopia on 2009-10-30
I suppose this should go here seeing that desktops don't have batteries normally.

Just upgraded...  everything is going ok for the most part.  Just noticed that the battery charging state/ plugged in icon is displaying what I can only assume is the default icons and not the icons in my pack which displayed fine in jaunty (of course).  Does anyone have any clue as to the issue here.  I'm guessing the battery applet is not looking for the icon in the same place as in juanty.  Any ideas?

---

### Post by lotharmat on 2009-10-30
Swap! I have a laptop and can't get the damn battery applet to show!!

---

### Post by konqueror7 on 2009-10-30
have you tried managing it in System > Preferences > Power Management? it allows you to show or hide the battery...as of why, i don't know since haven't upgraded yet...:D

---

### Post by lotharmat on 2009-10-30
Cheers mate! Worked like a charm.

---

### Post by wewantutopia on 2009-10-30
I just finished fixing the problem on my system.  Looks like the default icons are in 

/usr/share/gnome-power-manager/icons/hicolor/"specific size"/status.

The icons representing charge state in my icon pack in ~/.icons were all labeled gpm-primary-* which before the update worked fine.  

I just copied those icons and renamed them to match the new icons gpm-battery-*

Problem solved.

---

### Post by konqueror7 on 2009-10-30
nice...now lets mark the thread as solved...:D

---

