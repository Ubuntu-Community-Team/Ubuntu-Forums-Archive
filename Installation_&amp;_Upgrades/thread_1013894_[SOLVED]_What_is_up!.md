---
title: "[SOLVED] What is up?!"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by Cadeyrn on 2008-12-17
Why is Ubuntu 8.xx's Update Manager so incompatible with computers that have ATI video cards??? And why is it worse for 8.10?

Virtually everyone with an ATI card on 8.xx who's recently ran the manager is reporting numerous problems. My computer is acting like Windows Vista, i.e. absolutely everything about the system is going wrong, tons of reliable fixes strangely don't work for me, and no one seems to know how to fix it and most just don't care. I'm being forced to reinstall, which will fix everything but one problem:

How am I supposed to update my system when I KNOW the Update Manager flashes the updates I need, doesn't install them, never says I need updates again, and then gradually screws up my entire system?

---

### Post by taurus on 2008-12-17
Why not just run it from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mikewhatever on 2008-12-17
> **Cadeyrn said:**
> 
How am I supposed to update my system when I KNOW the Update Manager flashes the updates I need, doesn't install them, never says I need updates again, and then gradually screws up my entire system?

Applications/Accessories/Terminal in the menu, type in 
```
sudo apt-get update && sudo apt-get upgrade
```.

---

### Post by Cadeyrn on 2008-12-17
I'm sceeeeeeaaaarrrred (XD). Would it not cause the problems Update Manager has? Is it safe?

EDIT: Hey, I liked your signature. I just learned user-friendly means friendly-towards-what-you-want instead of easy-to-use.

---

### Post by Cadeyrn on 2008-12-19
UPDATE: It turns out my problem was never Update Manager. It was the Restricted ATI driver.

---

