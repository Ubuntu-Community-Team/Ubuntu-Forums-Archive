---
title: "[SOLVED] Need to hide a package from aptitude/apt-get autoremove."
date: 2008-10-30
forum: General Help
---

### Post by hellion0 on 2008-10-30
I'm running Xubuntu 8.04.1 on both my desktop and laptop.

On my laptop, whenever I try to use aptitude to add/remove software, it also prompts me to remove XMMS (which I installed from the .deb [here](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)), saying it was automatically installed and no longer being used. (Even if it's in fact being used at the moment I call aptitude from the CLI.) I end up having to use apt-get instead, which suggests removing it, but lets me carry out whatever operation I'm doing without getting rid of it.

I never have a similar problem with XMMS and aptitude/apt-get on my desktop, which I installed XMMS on from the same .deb package. Aptitude does exactly what I want it to on that machine - it ignores XMMS's presence unless I specifically want to remove it.

Basically, what I want to know is: Is there a way to make aptitude ignore the presence of xmms so it won't try to remove it every time I call it (and hide it as well from apt-get autoremove)?

---

### Post by geirha on 2008-10-30
I believe this happens if you install a package that depends on xmms, and then later remove that package again, aptitude will think you don't need xmms either. Try reinstalling it ```
sudo aptitude reinstall xmms
```

---

### Post by hellion0 on 2008-10-30
> **geirha said:**
> I believe this happens if you install a package that depends on xmms, and then later remove that package again, aptitude will think you don't need xmms either. Try reinstalling it ```
sudo aptitude reinstall xmms
```That came back with this:
```
Writing extended state information... Error!
E: I wasn't able to locate file for the xmms package. This might mean you need to manually fix this package.
```

That said, I did manage to figure it out:
```
sudo aptitude unmarkauto xmms
```
This unmarks the xmms package as automatically installed, therefore aptitude no longer wants to treat it as an automatically installed but unneeded package.

---

### Post by geirha on 2008-10-30
Ah, I just did a search and there isn't any package called xmms in the hardy repositories. There's xmms2 and gxmms2, are you sure you're not using one of those?

---

### Post by hellion0 on 2008-10-30
Nope. Just plain XMMS, which was removed from the repos when Hardy was released. Like I said, I grabbed the .deb file from the link in the first post, then installed it manually with dpkg.

---

