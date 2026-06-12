---
title: "[SOLVED] Changing Gnome Menu Size"
date: 2008-11-19
forum: General Help
---

### Post by philheaton on 2008-11-19
Hi

I was wondering if anyone could help as I'm gradually going bald trying to solve this little riddle...

I am trying to alter the Gnome drop-down menu button sizes so that all the entries actually fit onto my laptop screen. 

I have had a look in the theme's gtkrc file, but am at a loss at what to edit. 

I have included 2 screenshots to illustrate what I'm going on about. I would obviously like to edit the theme in screenshot1 (dust theme) to give similar menu sizes to those in screenshot2 (aurora smooth). 

Thanks

Phil

[Edit] Jeez - would you believe it, not even a minute after posting this, I solved it.

---

### Post by eternalnewbee on 2008-11-19
Hi there.
So how did you solve it?

---

### Post by philheaton on 2008-11-19
I added this line to the top of the gtkrc file: 

gtk-icon-sizes = "panel-menu=16,16"

That's it! Worked like a charm!

---

### Post by eternalnewbee on 2008-11-19
Excellent! Then you can mark this thread as solved, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

---

