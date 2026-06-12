---
title: "help cant download anything"
date: 2008-08-05
forum: General Help
---

### Post by abredin on 2008-08-05
I was trying to download lime wire on my computer when the power went all funny and the computer shut down and now when ever i start a new download it says "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
i have new clue what to do

---

### Post by iaculallad on 2008-08-05
> **abredin said:**
> I was trying to download lime wire on my computer when the power went all funny and the computer shut down and now when ever i start a new download it says "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
i have new clue what to do

On your terminal, do what the message say's, only this time, insert sudo:

```
sudo dpkg --configure -a
```

---

### Post by abredin on 2008-08-05
thanks

---

