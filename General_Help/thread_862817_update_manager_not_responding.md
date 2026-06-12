---
title: "update manager not responding"
date: 2008-07-17
forum: General Help
---

### Post by electrahogg42 on 2008-07-17
update manager hangs 
shows updates that I have available but stalls when I click on install updates have to force quit update manger

---

### Post by iaculallad on 2008-07-17
> **electrahogg42 said:**
> update manager hangs 
shows updates that I have available but stalls when I click on install updates have to force quit update manger

Try to update from the terminal:

```
sudo apt-get update && sudo apt-get updrade
```

---

### Post by kunixos on 2008-07-17
sounds like you need to do a manual terminal update

open a terminal and type
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
that last one might not do much, but it's helpful sometimes.

That should probably update your Update Manager :)

Hope this helps!

---

### Post by electrahogg42 on 2008-07-17
that did it seems to be working now 
thank you

---

