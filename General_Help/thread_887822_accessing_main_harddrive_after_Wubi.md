---
title: "accessing main harddrive after Wubi"
date: 2008-08-12
forum: General Help
---

### Post by EmanuelMagana on 2008-08-12
Is there to access the main windows harddrive after using Wubi to install Ubuntu?

---

### Post by spike.robinson on 2008-08-12
> **EmanuelMagana said:**
> Is there to access the main windows harddrive after using Wubi to install Ubuntu?

Yes, look under /host in a terminal. 

Or on the Desktop, from the Places menu go to -> Computer -> Filesystem -> Host

---

### Post by itsjareds on 2008-08-12
type this into the terminal:

```
nautilus /host
```

It will bring up the file browser for your Windows partition. I added it to my shortcuts and named it "Windows".

---

