---
title: "[SOLVED] Cairo Dock weird problem...."
date: 2008-10-24
forum: General Help
---

### Post by x C0MMAND0 x on 2008-10-24
So I was editing the height of Cairo-Dock launchers, and I mistakingly added an extra number so it came out to be 1000 pixels or something like that.  Needless to say, my computer basically froze up as it could not render this monstrous size.

I rebooted directly in the shell, ran

```
sudo apt-get remove cairo-dock
```

and it removed cairo-dock and the plugins as well.

Then, I reinstalled it but now when I try to run it, it freezes up my whole computer.  I'm guessing that somehow my customization features got saved somewhere and when I reinstall it is still somehow pulling my old settings.

Any thoughts/ideas for this interesting problem I ran into?  Does anybody know where the cairo dock settings are stored or if they even are?

Thank you VERY much for your help.  FYI I'm running 64 AMD, but at one point I did have cairo-dock fully functioning.

---

### Post by x C0MMAND0 x on 2008-10-24
SOLVED!

I found it out.  It WAS pulling my old settings.  I ran this code to fix it

```
cairo-dock -m
```

the -m allows you to edit the settings and "manage" it before the app loads.

---

### Post by Idefix82 on 2008-10-25
Alternatively, so you know for next time, when reinstalling you should do
```
sudo apt-get purge cairo-dock
```

This also deletes all your settings in the home folder. If you just say remove then your home folder is not touched.

---

### Post by nimrodwebdesign on 2010-06-17
Thanks so much. I just started using Cairo and I was stuffed because the 'slider' app just kept locking it up, even when I tried to remove it. Your **-m** saved me! :KS

---

### Post by x C0MMAND0 x on 2010-06-28
> **nimrodwebdesign said:**
> Thanks so much. I just started using Cairo and I was stuffed because the 'slider' app just kept locking it up, even when I tried to remove it. Your **-m** saved me! :KS

Glad to help!

---

