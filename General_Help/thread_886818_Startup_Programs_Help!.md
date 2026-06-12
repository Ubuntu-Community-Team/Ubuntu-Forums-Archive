---
title: "Startup Programs Help!"
date: 2008-08-11
forum: General Help
---

### Post by dsbogard on 2008-08-11
Dearest All----

I'm newish to Ubuntu, and am lost on this one.


i was trying to set some programs to run at startup.

SO, I went into sessions, chose the "session options" tab, and then "remember currently running applications".

Well, I did it later, too, thinking it would simply just replace the previous list of startup programs.  BUT instead it just added, and now I've got WAY too many programs running on startup.


How can I reset this, so those that were added don't start?  (they don't show up on the 'startup' tab.


Any thoughts?


Thanks

---

### Post by fahadsadah on 2008-08-11
Try ```
sudo aptitude reinstall gnome-sessions-manager
```

---

### Post by dsbogard on 2008-08-11
> **fahadsadah said:**
> Try ```
sudo aptitude reinstall gnome-sessions-manager
```

Thanks for the thought.

When i try that command i get:

Couldn't find any package whose name or description matched "gnome-sessions-manager"

---

### Post by anotherdisciple on 2008-08-11
First I would turn off that setting, then go to System > Preferences > Sessions and make sure all the programs you don't want to start are unchecked or deleted.

After that... add the programs that you DO want to start to that list. I would just pick the things that you open every time you turn on your computer.

---

### Post by dsbogard on 2008-08-11
> **anotherdisciple said:**
> First I would turn off that setting, then go to System > Preferences > Sessions and make sure all the programs you don't want to start are unchecked or deleted.

After that... add the programs that you DO want to start to that list. I would just pick the things that you open every time you turn on your computer.

I did do that, but still get quite a few programs that just start on their own (that started back when I first clicked the "those programs that are running" button)


Any thoughts?


Thanks so much for your help everyone.

---

### Post by dsbogard on 2008-08-12
No thoughts?  Oh well---the startup-programs seem to be an issue all over....

---

