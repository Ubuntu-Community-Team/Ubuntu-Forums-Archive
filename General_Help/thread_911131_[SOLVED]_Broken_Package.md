---
title: "[SOLVED] Broken Package"
date: 2008-09-05
forum: General Help
---

### Post by DarkTxS on 2008-09-05
Hello everybody (:

The Synaptic Package Manager says that I have 1 broken package on my system and I should use the "Broken" filter to locate it.
So... I tried to go to: **Top menu -> Settings -> Filters -> Broken** and couldn't find something.
I know there were some topics about it but didn't help much...
If anyone can help I'd be glad :)

Thanks! (:

---

### Post by Ryadt on 2008-09-05
Have a look here:
[http://ubuntuforums.org/showthread.php?t=140920&highlight=junk](http://ubuntuforums.org/showthread.php?t=140920&highlight=junk)

---

### Post by DarkTxS on 2008-09-05
Hmm.. didn't help as well..
It seems like after I go to the "Broken" filter, it finds no broken package.
It doesn't show any package which is broken.

Thanks again (:

---

### Post by gjoellee on 2008-09-05
which package is broken? (might be showed if you try to install something in the terminal if it is not showed elsewhere)

---

### Post by DarkTxS on 2008-09-05
I finally found the packge (using the custom filters) and just removed it. The Re-Installation has made some problems so I removed it.
Now everything works well, I think :P

Thanks you all (:

---

### Post by Ryadt on 2008-09-05
Try```
sudo dpkg --configure -a
```

---

### Post by gjoellee on 2008-09-05
> **DarkTxS said:**
> I finally found the packge (using the custom filters) and just removed it. The Re-Installation has made some problems so I removed it.
Now everything works well, I think :P

Thanks you all (:
  good it's fixed, please mark the thread as "solved"

---

