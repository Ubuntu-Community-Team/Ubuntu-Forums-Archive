---
title: "OpenType fonts"
date: 2008-11-18
forum: General Help
---

### Post by Tynach on 2008-11-18
I'm trying to install some OpenType fonts on my computer. I found a thread for this already here, but for some reason it won't let me post in it.

Anyways, I was trying to install an OpenType font on my computer, using the standard /usr/share/fonts, and they would show up only in other programs like KWord. Open Office does not list them.

I've already gotten them working by converting them with FontForge, but I still want to see if I can get the OpenType versions to work.

So, Open Office recognizes them in the Windows version, so its not really Open Office at fault. Linux recognizes them in other programs, so its not Linux's fault.

So, who's fault is it?

---

### Post by spiderbatdad on 2008-11-18
are the fonts in your /.fonts directory?
try: ```
sudo fc-cache -fv
```

---

### Post by Tynach on 2008-11-19
The fonts are in a directory that works with all other fonts. I have said that the TrueType fonts I converted them into work fine; I just want to see if I can get the OpenType versions to work properly.

---

