---
title: "font issue"
date: 2008-11-03
forum: General Help
---

### Post by sidny4 on 2008-11-03
My font has been constantly getting messed up since I upgraded to 8.10. I have an intel 965 integrated graphics controller using the intel driver. I have tried changing my font settings but this still happens. Attached are some screenshots, does anyone know what is causing this?

---

### Post by jayson.rowe on 2008-11-03
You did say you tried changing your font settings - did you change the hinting style or the fonts themselves? If you haven't try selecting different fonts to see if that corrects the problem.

You could also try bringing up a terminal and doing a:
```
sudo dpkg-reconfigure fontconfig-config
```
followed by 
```
sudo dpkg-reconfigure fontconfig.
```

At this point, I doubt it could hurt.

---

### Post by sidny4 on 2008-11-04
that did clear it up for a few minutes, then it went back to being all messed up. I have tried it with compiz off and on and that doesn't change anything. Also, I do have it set up in a dual monitor configuration. When I take it out of the dual monitor mode it isn't messed up, any other thoughts?

---

### Post by jayson.rowe on 2008-11-05
What about DPI - sometimes GNOME will select a different DPI in dual-head mode than in Single Head. See what it's choosing under single head, and then see if it's different under the dual-head config.

---

### Post by Bufke on 2008-11-09
This happens to me too sometimes with dual monitors.  Only happens sometimes, it's weird. Playing with font settings fixes it for a few minutes.  The DPI is the same on both single and dual monitor.

---

