---
title: "Ubuntu will only load login with terminal and then stays as terminal"
date: 2008-09-30
forum: General Help
---

### Post by mcberg182 on 2008-09-30
I had done restarted my computer after making some changes to my audio drivers when this happened. It will start off with the normal loading screen with the loading bar, but then switch to terminal. How can I fix this?

---

### Post by zvacet on 2008-09-30
```
startx
```

or 

```
sudo /etc/init.d/gdm start
```

---

### Post by Ryadt on 2008-09-30
Try to boot in recovery mode and fix xserver from there.

---

### Post by mcberg182 on 2008-09-30
Thank you! The first code worked when I tried it.

---

