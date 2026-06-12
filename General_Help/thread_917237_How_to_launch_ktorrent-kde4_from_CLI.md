---
title: "How to launch ktorrent-kde4 from CLI?"
date: 2008-09-11
forum: General Help
---

### Post by foxmulder881 on 2008-09-11
As title says. I used to have ktorrent (kde3) package installed. Then I upgraded to some kde4 packages and installed ktorrent-kde4. Now I can't seem to launch ktorrent-kde4 from my command-line. I just get an error saying ```
bash: ktorrent-kde4: command not found
```

---

### Post by milasch on 2008-09-11
Try going to synaptic package manager, find the ktorrent-kde4 package you installed, right click,  go to properties, then check under the "Installed files" if you find the right executable file to open ktorrent-kde4.

---

### Post by foxmulder881 on 2008-09-11
> **milasch said:**
> Try going to synaptic package manager, find the ktorrent-kde4 package you installed, right click,  go to properties, then check under the "Installed files" if you find the right executable file to open ktorrent-kde4.

Thanks mate. This done it.

```
/usr/lib/kde4/bin/ktorrent
```

---

