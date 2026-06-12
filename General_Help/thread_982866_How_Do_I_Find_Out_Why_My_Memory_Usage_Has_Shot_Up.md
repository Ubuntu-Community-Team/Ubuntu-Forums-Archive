---
title: "How Do I Find Out Why My Memory Usage Has Shot Up?"
date: 2008-11-15
forum: General Help
---

### Post by Mark76 on 2008-11-15
I used to be getting readings under the 300 MB mark, but now I'm getting over 600.

---

### Post by squaregoldfish on 2008-11-15
Which process(es) are using the memory?

Steve.

---

### Post by ajgreeny on 2008-11-15
Whwew are you getting these memory readings from?  Don't forget linux deals with freeing memory quite differently from windows and only frees it when it is needed, not just because you shut down the particular application.  To see what is really being used by the running system and can not be freed by it run ```
free -m
```and look at the **-/+ buffers/cache:** figures which are more accurate.

---

### Post by Mark76 on 2008-11-15
It's back to normal.

How annoying is that?

---

