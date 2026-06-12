---
title: "HOWTO: Disable HTTP Cache cleaner when using KDE apps on Gnome"
date: 2008-10-29
forum: General Help
---

### Post by Darkshade on 2008-10-29
Ok, I've seen millions of topics made by people asking how to disable the "Launching HTTP Cache Cleaner..." process that appears every once in a while on the taskbar/panel when using KDE apps like Amarok in GNOME. What I've never seen is a fix for it so here it goes:


1. Install kcontrol

```
sudo apt-get install kcontrol
```

It'll probably install kdebase-data kicker and libkonq4 too (not sure if they're needed but let it do it).

2. Go to Applications -> Other -> Cache. Uncheck the "Use cache" option, Apply, Close and you're done!

With these two simple steps you'll get rid of that "Launching HTTP Cache Cleaner" window forever.


p.s. not sure if it's the right section, please move it if not.


Any feedback will be appreciated.

---

### Post by munzli on 2008-11-25
i've found a way to get this one done in [kde4]("http://www.munz.li/?p=52")!

---

### Post by ctarwater on 2008-11-25
Thanks!

I love using ktorrent in gnome but never really bothered looking for a solution the CacheCleaner issue even though it annoys the hell out of me.

---

### Post by ninetails on 2009-06-13
How do you know if it's ok to disable it this way?  Maybe there's a good reason why it needs to run?

---

### Post by dowcet on 2010-04-30
> **ninetails said:**
> How do you know if it's ok to disable it this way?  Maybe there's a good reason why it needs to run?

I wonder about this too. But I tried following the directions above anyone and hit the following problem:

```

Package kcontrol is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdebase-workspace-bin kdelibs4c2a
E: Package kcontrol has no installation candidate

```

So, anyone know if there is a disadvantage to getting rid of this process (it seems to slow my machine down a lot) and whether there is a new way to do it?

---

