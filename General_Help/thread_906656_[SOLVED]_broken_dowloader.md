---
title: "[SOLVED] broken dowloader"
date: 2008-08-31
forum: General Help
---

### Post by m005k on 2008-08-31
I tried to install a .deb package and now I can't get the Ubuntu updates.

When I try I get this error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

When I try to run this it says I need to run as a super user. I tried and used my password, but it says it is not the correct one.
Help!

Mike

---

### Post by Ryadt on 2008-08-31
Did you try to run it with sudo?```
sudo dpkg --configure -a
```

---

### Post by m005k on 2008-08-31
Ok, I tried that it says I need to close ohter package managers I have running. How do I do that?

Mike

---

### Post by Ryadt on 2008-08-31
You may have synaptic open. Just close it and re-run the code. If you don't have synaptic open, try restarting x (CTRL+ALT+BCKSPCE) and then do the code.

---

### Post by m005k on 2008-08-31
Yes-that fixed it. Now I just have to figure out how to install a .deb package. I downloaded Google's Picasa, but I don't know how to install it. 
Mike

---

