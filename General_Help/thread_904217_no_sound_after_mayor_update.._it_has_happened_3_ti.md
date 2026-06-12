---
title: "no sound after mayor update.. it has happened 3 times already"
date: 2008-08-29
forum: General Help
---

### Post by Mia_tech on 2008-08-29
guys need help restoring my sound, that is gone after doing an update what I think it was a kernel update, and it has knock down my sound for the 3rd time, in the past I've fixed it with this guide
[http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install)
but I've tried same approach with no luck...any help appreciated


thanks

---

### Post by iaculallad on 2008-08-29
> **Mia_tech said:**
> guys need help restoring my sound, that is gone after doing an update what I think it was a kernel update, and it has knock down my sound for the 3rd time, in the past I've fixed it with this guide
[http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install)
but I've tried same approach with no luck...any help appreciated


thanks

Try installing the linux-generic file:

```
sudo aptitude install linux-generic
```

---

### Post by Crafty Kisses on 2008-08-29
If that doesn't work try reverting to a older kernel.

---

