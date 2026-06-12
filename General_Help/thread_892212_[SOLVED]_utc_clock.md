---
title: "[SOLVED] utc clock"
date: 2008-08-16
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2008-08-16
I installed 8.10 over 7.04 and just noticed that the clock in the panel doesn't do utc time anymore. Is there any way to get this back?

Al

---

### Post by p_quarles on 2008-08-16
8.10 isn't out yet, so don't expect it to work correctly. :)

That said, you should be able to set the clock to display whatever time you want, so maybe I don't completely understand the question?

---

### Post by ihatetryingtopickaloginna on 2008-08-17
Ah yes, fingers are faster than my brain. That would be 7.10 and 8.04 to be precise. Just wait till I install another version and have to keep up with three.

The clock applet doesn't have utc in the preferences like 7.10 did. I've clicked on every button in there and can't find it.

Al

---

### Post by mrz80 on 2008-09-29
> **ihatetryingtopickaloginna said:**
> Ah yes, fingers are faster than my brain. That would be 7.10 and 8.04 to be precise. Just wait till I install another version and have to keep up with three.

The clock applet doesn't have utc in the preferences like 7.10 did. I've clicked on every button in there and can't find it.

Al

That's worth a bug report, as the docs indicate the option should still be there.

---

### Post by mrz80 on 2008-09-29
I did some rummaging around on my work machine (which also has clock-applet 2.22.2 running, but *does* show the UTC option on its preferences) and found the appropriate knob to tweak using gconf-editor.  I just checked here on my home machine (which doesn't have the UTC preferences option) and sure enough, gconf-editor can get  it to display UTC.

Start up gconf-editor.
Select /apps/panel/applets/clock_screen0/prefs
You'll see an option named gmt_time
Click the check-box
Voila!  GMT!

---

### Post by ihatetryingtopickaloginna on 2008-10-02
Ok thanks. I'll try it out.

---

