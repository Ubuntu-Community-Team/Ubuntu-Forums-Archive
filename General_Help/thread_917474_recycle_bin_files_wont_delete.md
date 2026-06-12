---
title: "recycle bin files wont delete"
date: 2008-09-11
forum: General Help
---

### Post by ayet on 2008-09-11
WHy is that i cant empty my recycle bin files?
and when i delete those files manualy inthe recycle bin its says

"Error removing file: Permission denied"

please give me the procedure in solving this thanks.

---

### Post by iaculallad on 2008-09-11
> **ayet said:**
> WHy is that i cant empty my recycle bin files?
and when i delete those files manualy inthe recycle bin its says

"Error removing file: Permission denied"

please give me the procedure in solving this thanks.

In your terminal:

```
sudo rm -r ~/.local/share/Trash/files/*
```

---

### Post by ayet on 2008-09-11
thanks problem solved

---

