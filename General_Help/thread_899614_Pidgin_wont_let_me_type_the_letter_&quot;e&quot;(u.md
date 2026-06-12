---
title: "Pidgin wont let me type the letter &quot;e&quot;(ubuntu studio)"
date: 2008-08-24
forum: General Help
---

### Post by short circut on 2008-08-24
So here is the problem. Using Pidgin I accidentally clicked the logging button. Now every time I type the letter "e" into the IM Clent it toggles logging on or off, I have tried rebooting and reinstalling. Any one know how to fix this?

---

### Post by unutbu on 2008-08-24
There might be a better way, but here's something you might try:

Look in the file ~/.purple/accels

This file seems to hold keyboard shortcuts for pidgin.
Search for lines having the word "log" in them, and see if any of them end in "e". Erase the "e" and perhaps you'll be back to normal.

---

### Post by short circut on 2008-08-24
thank you. That worked wonders

---

