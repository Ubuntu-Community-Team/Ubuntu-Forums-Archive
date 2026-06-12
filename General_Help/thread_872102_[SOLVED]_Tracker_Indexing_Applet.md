---
title: "[SOLVED] Tracker Indexing Applet"
date: 2008-07-27
forum: General Help
---

### Post by employeeno5 on 2008-07-27
Hi there,

I feel a little foolish on this one. So, the tracker search applet, the little thing that goes in your system-tray and let's you know the status of your indexing; I right-clicked on that to adjust the preferences. I told it to hide the icon except for when giving "important messages".
Now, I don't know how to bring it back so I can adjust other preferences again,

I am aware that under system>preferences> there is the "search and indexing" menu. However, those options do not include some of the ones specific to the actual tracker applet.

Any help would be fantastic.

Thanks!

---

### Post by Tim Sharitt on 2008-07-27
Hit Alt-F2 and enter
```
tracker-applet
```

---

### Post by employeeno5 on 2008-07-27
Thanks for the advice, however, it does not help me. The tracker applet is set to be hidden. I need it unhidden so I can change it's preferences, or some other means of doing so.
So though I can turn it one via your command, I cannot see it still in my system tray or change it's properties.

Any other ideas?

---

### Post by hackerseraph on 2008-09-11
Bump

---

### Post by pierissimo on 2008-09-17
try deleting /home/user/.config/tracker/tracker-applet.cfg

It should return visible

---

### Post by employeeno5 on 2008-09-18
> try deleting /home/user/.config/tracker/tracker-applet.cfg

Thank you! That was just what I needed!

---

