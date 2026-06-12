---
title: "No Permision?"
date: 2008-08-27
forum: General Help
---

### Post by Wickd on 2008-08-27
Hi there

I have a 222gb partition that I want to use for all my music files and so forth, but for some reason I cannot access it via Ubuntu, apparently I do not have the permissions to access it

An ideas?

Thanks in advance

---

### Post by Dr Small on 2008-08-27
Try opening nautilus as root:
```
gksudo nautilus
```

And then browsing to it. Apparently, it was mounted with the wrong owner, etc.

Dr Small

---

### Post by Wickd on 2008-08-28
> **Dr Small said:**
> Try opening nautilus as root:
```
gksudo nautilus
```

And then browsing to it. Apparently, it was mounted with the wrong owner, etc.

Dr Small
Okay when I execute the command as root it tells me that user sharing is not enabled. So where do I set this command?

Thanks

---

