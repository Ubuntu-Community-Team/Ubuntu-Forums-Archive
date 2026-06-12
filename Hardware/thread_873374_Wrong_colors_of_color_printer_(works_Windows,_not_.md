---
title: "Wrong colors of color printer (works Windows, not Ubuntu)"
date: 2008-07-28
forum: Hardware
---

### Post by dkulchenko on 2008-07-28
Hey all,

I just bought a new Epson Stylus CX7400 printer. Plugged it in to Ubuntu, got autodetected, and I added it as a printer. Easy enough. But there's one problem: when I connexct it to Windows, or print a test page DIRECTLY from the printer, the colors are fine (everywehre). If I print a test page from Ubuntu, however, The colors in general are fine, but specific percentages are screwed up, for example 90% black is blue, 70% yellow is pink, etc. 

I'm guessing this is either a problem with my driver, or the color settings. Does anyone know the specific color settings I must use? I've tried RGB Color (which was BAD), CMYK (which was better), and CMY Color (which was worse than RGB). Which one should I use, or maybe something is wrong with my driver?

Thanks in advance.

---

### Post by dkulchenko on 2008-07-29
Never mind, it's working now. I've installed the pipslite drivers from avasys.jp, (they were rpms, I converted them to debs with alien). It works fine now.

---

### Post by wannadumpwindows on 2008-07-29
Do us all a favor. Use the "Thread Tools" menu to make your thread as solved once your problem is resolved.:)

---

### Post by hod139 on 2008-09-08
I found that changing the print quality from standard to high fixed the test page colors (for both RGB and CMYK).

---

### Post by hod139 on 2008-10-27
Just an update. I recently upgraded from hardy to intrepid, and the new printer drivers in intrepid seem to be working well with the printer now.

---

