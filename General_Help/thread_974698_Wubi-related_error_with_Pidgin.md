---
title: "Wubi-related error with Pidgin?"
date: 2008-11-07
forum: General Help
---

### Post by justinpatterson on 2008-11-07
I used Wubi to install Ubuntu 8.10 on my computer, 10 gig partition, to run alongside Windows XP.  Everything works great, except one thing!  

When I open pidgin and enter in my login information and press "ok," it immediately closes out of pidgin! Anyone encounter this before?  It may be related to the way it was installed, using Wubi, or it could be simply a common Ubuntu error in general.  I tried some searches for it.

Ideas are welcome, heh.

---

### Post by justinpatterson on 2008-11-07
To add to this, it closes just as it begins to load my buddy list.  As in, I see screen names begin to appear and then pidgin shuts down.  Irritating.

---

### Post by deltateam2 on 2008-11-07
Applications >> Accessories >> Terminal

Issue
```
pidgin -d
```

Post what pidgin outputs to the terminal upon crash.

---

### Post by brandon88tube on 2008-11-08
This seems like an Ubuntu problem. I found a similar thread here [http://ubuntuforums.org/showthread.php?t=883086&highlight=pidgin+closes](http://ubuntuforums.org/showthread.php?t=883086&highlight=pidgin+closes) Not sure if it will help though.

---

### Post by Yashiro on 2008-11-08
Close Pidgin.
Delete everything in ~/.purple/.
Restart Pidgin.

If that fails, then uninstall Pidgin with Synaptic.
Re-install the base version that shipped with Intrepid.

---

### Post by justinpatterson on 2008-11-08
The other thread's suggestions did not work, but I do think you were right in saying it's not Wubi.  Perhaps I'll move the thread from here to that area of the forums.

---

