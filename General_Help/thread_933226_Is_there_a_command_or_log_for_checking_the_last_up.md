---
title: "Is there a command or log for checking the last updates to ubuntu?"
date: 2008-09-29
forum: General Help
---

### Post by devosion on 2008-09-29
I just recently authorized some updates, between today and yesterday, and now my connection is acting a little wonky on my linksys WUSB54GC. Im pretty sure it had something to do with a recent update so i'd appreciate any help in finding logs for my recent updates.

---

### Post by ThrobbingBrain66 on 2008-09-29
In Synaptic's File menu, click History and you'll see a log of all packages installed, removed, upgraded, etc.

---

### Post by devosion on 2008-09-29
Thanks much.

---

### Post by kostkon on 2008-09-29
> **devosion said:**
> I just recently authorized some updates, between today and yesterday, and now my connection is acting a little wonky on my linksys WUSB54GC. Im pretty sure it had something to do with a recent update so i'd appreciate any help in finding logs for my recent updates.
You can check the dpkg.log from *System -> Administration -> System Log*. If it's not there, just add it by selecting *File -> Open*; it is in */var/log*

Using the command line, you can open it like this, e.g.
```
gedit /var/log/dpkg.log
```

You can also check the history option in Synaptic, although I don't know if it shows the updates. Nevertheless, if you ever need it, just open Synaptic and select *File -> History*.

---

