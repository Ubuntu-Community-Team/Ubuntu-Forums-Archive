---
title: "problem with synaptic"
date: 2008-08-28
forum: General Help
---

### Post by dlm4849 on 2008-08-28
For some reason when I start synaptic, it says that its starting without administrative privileges instead of asking for my password. Whats going on here?

Dave

---

### Post by iaculallad on 2008-08-28
Try:

```
sudo usermod -a -G admin your_username
```

then, retry accessing Synaptics.

---

### Post by dlm4849 on 2008-08-28
Thanks

What would have caused that?

Dave

---

### Post by iaculallad on 2008-08-28
> **dlm4849 said:**
> Thanks

What would have caused that?

Dave

For some unknown reasons to me, you're not included on the privilege user group so we opt to execute the command I posted above to add you to the Admin group.

EDIT: I just don't know what had happened if you had executed first "gksudo synaptic" prior to adding you to the Admin group.

---

