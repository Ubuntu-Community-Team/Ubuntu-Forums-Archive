---
title: "cairo-dock broke after update"
date: 2008-07-16
forum: General Help
---

### Post by stldirty on 2008-07-16
ok there was a cairo-dock update yesterday and it failed during installation.  something about cairo-dock-data or something like that.  now i can't get my 3d panel work, it won't show my currently open programs, and my cairo apps aren't working.  its only showing my launchers.  i've tried reinstalling, uninstalling, and then doing a fresh install.  should i purge it?  i just don't want to lose my current theme that i hand customized...

---

### Post by fabounet on 2008-07-17
how did you install it ? 
was it the release candidate on Berlios ?
there is a new rc (1.6.1.2) there. for a maximum stability I recommend to wait until a version is on the repository.

---

### Post by stldirty on 2008-07-18
ok i reproduced the error.

```
E: /var/cache/apt/archives/cairo-dock-data_1.6.6.1-0ubuntu1~gilir6_all.deb: trying to overwrite `/usr/share/cairo-dock/cairo-dock_easy.conf', which is also in package cairo-dock
```

---

### Post by stldirty on 2008-07-18
> **fabounet said:**
> how did you install it ? 
was it the release candidate on Berlios ?
there is a new rc (1.6.1.2) there. for a maximum stability I recommend to wait until a version is on the repository.
i installed it via the repositories the first time.  the problem was the last update.  that error that i just posted up came up and ever since then i haven't been able to get the 3d bar, none of the cairo apps (clock, terminal, etc).  and i can't for the life of me figure out how to get everything back.  i've unintalled and reinstalled countless times.  i've gone through and deleted all the problem folders listed in that error message.  i got rid of my configuration folder in the home folder.  i tried installing from berliOS.  nothing is working now and its driving me nuts.  i'm running ubuntu hardy heron 64 bit if it matters at all.

---

### Post by dbulante on 2008-07-23
FWIW, I am having the same problem.  I couldn't get the plug-ins to work at all.  It disappeared after the latest update.

---

### Post by gilir on 2008-07-23
When you have this type of problem, just remove all cairo-dock packages (sudo apt-get remove cairo-dock*), wait some hours and try again.

It's seems that you are using my PPA, just be aware that it's subject to breakage, the time to stabilize the packaging.

---

### Post by stldirty on 2008-07-23
yea i got it working by removing everything and compiling from source.  i deleted everything but the folder in my home folder.

---

### Post by dbulante on 2008-07-24
> **gilir said:**
> When you have this type of problem, just remove all cairo-dock packages (sudo apt-get remove cairo-dock*), wait some hours and try again.

It's seems that you are using my PPA, just be aware that it's subject to breakage, the time to stabilize the packaging.

Thanks for this tip.  I've got it back up and running.  I really like this dock!

---

