---
title: "Compiz Stopped Working after Updates"
date: 2008-11-10
forum: General Help
---

### Post by Nimaran on 2008-11-10
My Desktops effects stopped working after I downloaded the most recent updates, at least I think that is what is causing it, I haven't done anything else. When I try loading "compiz" in the terminal I get the following error:
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/met

---

### Post by cdtech on 2008-11-10
I had the same issues when I upgraded. I just clicked on the "Compiz Fusion Icon" and it came back.
?

---

### Post by Nimaran on 2008-11-10
I don't have one of those icons, but when I go to System>Preferences>Appearance>Visual Effects, and choose Extra it just thinks for a while and then says "Desktop Effects Could Not Ben Enabled."

---

### Post by cdtech on 2008-11-10
Try to run it from a terminal:
```
fusion-icon &
```

---

