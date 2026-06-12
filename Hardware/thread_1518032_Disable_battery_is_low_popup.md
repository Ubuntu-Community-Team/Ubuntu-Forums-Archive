---
title: "Disable battery is low popup"
date: 2010-06-25
forum: Hardware
---

### Post by JoeGoalie on 2010-06-25
My laptop is old...  Very old...  And the battery gauge is all out of whack.  So, most of the time my battery reads as <9% and is "critically low."  Which is fine but, the popups are maddening.  I can't do anything on the computer without being interrupted by a freaking popup up giving me miss-information.  How the heck do I turn these off?

I got three of those popups just typing this!

---

### Post by gmargo on 2010-06-26
Something to try: open gconf-editor and navigate to /apps/gnome-power-manager/notify/ and uncheck the "low_power" checkbox.

---

### Post by JoeGoalie on 2010-06-27
> **gmargo said:**
> Something to try: open gconf-editor and navigate to /apps/gnome-power-manager/notify/ and uncheck the "low_power" checkbox.

Thank you, I will give it a shot and report back.

---

### Post by JoeGoalie on 2010-06-27
That stopped the little notifications in the top right corner but, it didn't stop the annoying popup dialog boxes.

---

