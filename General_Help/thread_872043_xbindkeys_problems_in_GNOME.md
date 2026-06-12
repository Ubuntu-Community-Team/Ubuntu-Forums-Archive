---
title: "xbindkeys problems in GNOME"
date: 2008-07-27
forum: General Help
---

### Post by toylas on 2008-07-27
Dear All,

I have been using xbindkeys for a couple of years now with all the window managers and desktop environments. It was working fine with GNOME until 2-3 hours back when it suddenly stopped and would not start. I can't figure out what's happened. It is working very well with other window managers but it does not seem to work anymore in GNOME. It does not even start in GNOME. 

Any ideas what could be happening?

Thanks,
Tulasi

---

### Post by toylas on 2008-07-27
I just checked, even though xbindkeys works fine in other accounts, when I tried using xbindkeys with fluxbox on my account, I faced the same problem. It does not start. I'm confused :(

---

### Post by toylas on 2008-07-28
Anyone? Any ideas?? Not being able to use xbindkeys is driving me nuts :(

---

### Post by toylas on 2008-07-28
Well I figured it out. While editing my .xbindkeysrc file, I actually made two clashing definitions of a key combination. That was somehow making xbindkeys crash. It did not give any error message though. That was the reason I could not figure out why xbindkeys was not even starting. But once I removed one clashing key combo, it worked fine.

---

