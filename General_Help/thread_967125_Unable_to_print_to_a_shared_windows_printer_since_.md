---
title: "Unable to print to a shared windows printer since going to 8.10"
date: 2008-11-01
forum: General Help
---

### Post by Meson on 2008-11-01
I completed a fresh install of 8.10 and added a printer on my parents' windows machine.  Printing a test page works fine.  Trying to print from firefox results in the job failing silently.  Trying to print from gedit I get "Error printing / Too many failed attempts"

Anyone else having printing difficulties since the upgrade?

---

### Post by NomadTW on 2008-11-04
I'm having the exact same issue.

printing works fine when hard wired, but the network printer doesn't work from inside any sort of actual program, but it does work to print a test page.

I upgraded to 8.10 from 8.04

---

### Post by Meson on 2008-11-04
My issue seems to have been resolved.  I deleted the printer from CUPS at one point and recreated it.  Everything has worked fine since then.

---

