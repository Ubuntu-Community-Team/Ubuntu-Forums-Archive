---
title: "[SOLVED] Kbounce problems"
date: 2008-09-07
forum: General Help
---

### Post by Eviltechie on 2008-09-07
I installed kbounce, but the icon never showed up in the menu.
```
sudo apt-get install kbounce
```

So I tried to reinstall it.
```
sudo apt-get install kbounce
```

Then the install was duplicated.

I tried to uninstall it.
```
sudo apt-get remove kbounce
```

But it only removed one.

I tried it again.
```
sudo apt-get remove kbounce
```

But it said it wasn't installed. (I also tried purge)

So what do I do now?

---

### Post by Eviltechie on 2008-09-07
Bump!

---

### Post by Eviltechie on 2008-09-07
I opened up synaptic, and found the problem. There are two kbounce packages, kbounce and kbounce-kde4.

---

