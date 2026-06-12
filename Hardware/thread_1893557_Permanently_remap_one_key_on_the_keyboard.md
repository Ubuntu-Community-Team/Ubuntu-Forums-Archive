---
title: "Permanently remap one key on the keyboard?"
date: 2011-12-10
forum: Hardware
---

### Post by Starlight on 2011-12-10
Hi! I'm not using Ubuntu at the moment, but I think it's something that's not specific to a single Linux distro. 

Some time ago I spilled some juice on my laptop's keyboard. Since then, the letter "P" isn't working. I found a way to make another key act as a P:

```
xmodmap -e 'keycode 135 = P'
```

However, I need to run it every time I reboot my computer. I tried adding that line to .bash_profile in the "User specific environment and startup programs", but it's not doing anything. :( Is there a way to make it work?

---

### Post by Starlight on 2011-12-11
*pokes this thread with a poking stick because it appears to have died*

---

