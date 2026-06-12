---
title: "Installed nvidia drivers, now fonts are too big"
date: 2005-11-24
forum: General Help
---

### Post by ErikTheRed on 2005-11-24
I went and installed the nvidia drivers for my system, and now all of my fonts are too big. I was able downsize some of them through the appearances section of system settings, but for the majority of my programs the fonts seem a lot larger than normal. Just wanted to see if I'm missing something to fix this problem.

---

### Post by Zeddicus on 2005-11-24
This works for me:

sudo kate /etc/kde3/kdm/kdmrc

Add "-dpi 100"

To this line:
```

ServerArgsLocal=-nolisten tcp 
```

So it reads:

```

ServerArgsLocal=-nolisten tcp -dpi 100
```

Back out to kdm, restart your session.

---

