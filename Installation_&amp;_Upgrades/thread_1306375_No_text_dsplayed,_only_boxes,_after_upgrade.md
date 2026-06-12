---
title: "No text dsplayed, only boxes, after upgrade"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by moyashimaru on 2009-10-30
I upgraded from 9.04 to 9.10 today, now my login screen and desktop display only strings of empty boxes rather than words and letters. The LiveCD runs fine, however.
(Also my login screen display settings are also out of wack; it can be moved around not unlike an overlarge PDF file, as if my display were much bigger than it actually is.)

Any thoughts?

---

### Post by alwuntu on 2009-10-31
Same for me here.

But on my installation only the login screen is affected. I think there might be missing some fonts?

---

### Post by alwuntu on 2009-11-01
This is indeed a font problem...
After executing ```
gksudo -u gdm dbus-launch gnome-appearance-properties
``` you will see the same result.
And if you change in the same windows the "Sans" fonts to something else the login screen looks better...

---

