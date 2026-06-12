---
title: "Change folder permissions from root"
date: 2008-10-24
forum: General Help
---

### Post by Grimnir512 on 2008-10-24
I run Glest and I recently downloaded a mod for it, and whilst trying to put a file into a folder I was told I didn't have the permissions. I checked thefolder permissions and they were for root so I tried

```
sudo -i
```

but that didn't help. Is there any way I can allow myself to add files to the folder?

Grimnir512

---

### Post by C.S.Cameron on 2008-10-24
Try it from GUI using "gksu nautilus".
Changing permissions from root can cause problems.

---

### Post by Grimnir512 on 2008-10-24
> **C.S.Cameron said:**
> Try it from GUI using "gksu nautilus".
Changing permissions from root can cause problems.

That worked! Thanks :)

One more command to add to my repertoire too :P

---

