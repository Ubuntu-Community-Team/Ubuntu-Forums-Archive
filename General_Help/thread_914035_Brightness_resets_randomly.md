---
title: "Brightness resets randomly"
date: 2008-09-08
forum: General Help
---

### Post by Mr. Spontaneous on 2008-09-08
Hi All,
I've been running 8.04 KDE 4 remix updated with the 4.1 PPA repositories and have had no problems whatsoever... until the latest series of updates (4.1.1 and on, I believe).

Recently I've found my laptop brightness being reset to 55% no matter what I do.  For example, I set it to 100% and it holds for a few seconds until a draw event occurs on screen, or I change focus to a new window.  This also holds true for brightnesses lower than 55%.

This is what I have in the appropriate proc file...
```
$ cat /proc/acpi/video/VID/LCD0/
levels:  100 100 20 25 30 35 40 45 50 55 60 65 70 75 80 85 90 100
current: 55
```

And here is my video chipset...
```
$ lspci
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

I googled around and checked launchpad but couldn't find a bug that represents my problem.  Any suggestions?

Thanks in advance!

---

### Post by pofigster on 2008-09-08
Not a solution, but I had that exact same problem on my laptop running Ubuntu - I did a fresh reinstall and it fixed the problem.  Also, on that same laptop at the same time, the volume would, on it's own, jump up to 100% all the time.  It was way annoying.

---

