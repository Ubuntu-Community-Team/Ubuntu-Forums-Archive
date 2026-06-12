---
title: "CPU clock???"
date: 2008-11-04
forum: General Help
---

### Post by cowdog88 on 2008-11-04
I have windows on the internal harddrive of my laptop and i run Ubuntu HH from an external hard drive.  When I shut down windows the clock time is correct and when I start Ubuntu the time is correct, but when I shut down Ubuntu and reboot into windows the time is 6 hours off. Is Ubuntu re-setting my CPU clock?

---

### Post by Zill on 2008-11-04
It sounds like you have Ubuntu based on UTC (equates to GMT "London time") and Windows based on Local time.  Unless you live in the UK these will be different times!

I suggest you keep the PC hardware clock and Ubuntu based on UTC and also base Windows on UTC.  Then set the time offset to display your correct local time.  This will ensure that both OS's will show the correct time and will change DST on the correct date.

The section entitled "Multiple Boot Systems Time Conflicts" in [this thread]("https://help.ubuntu.com/community/UbuntuTime") should help.

---

