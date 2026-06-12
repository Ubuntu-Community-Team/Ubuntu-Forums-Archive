---
title: "Can't connect to wireless networks"
date: 2009-08-25
forum: Hardware
---

### Post by TyrantWave on 2009-08-25
I recently set up Ubuntu 9.04 on the house computer as XP had packed in again, and with some work I got everything to work nicely - I can browse the internet fine, all sound works, and nothing was failing.

However, whenever I try to connect to a wireless network now, it doesn't even do anything.

The wireless manager can see the network fine, and has good signal, but when I go to connect it tries for about 30 seconds, then asks me for the pass key again.

Nothing has changed in my set up overnight, but this suddenly started happening for some reason or another.

Any ideas why?

Annoyingly, I don't have a wired connection either on that computer, so I can't install much on it =/.

And I just realised I posted this in the wrong section, sorry.. =/

---

### Post by sergiom99 on 2009-08-25
I would start by changing network manager for wicd
```
 sudo apt-get install wicd
```

---

