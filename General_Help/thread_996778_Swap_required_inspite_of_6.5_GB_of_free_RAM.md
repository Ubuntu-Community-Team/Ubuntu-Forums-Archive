---
title: "Swap required inspite of 6.5 GB of free RAM ?"
date: 2008-11-29
forum: General Help
---

### Post by anjanesh on 2008-11-29
Why on earth is any swap memory being used at all when only 1.3GB of 7.7GB of RAM is being used ?

[[img]http://img262.imageshack.us/img262/1646/systemmonitorgg7yc1.png[/img]](http://img508.imageshack.us/img508/425/systemmonitorgg7.png)

---

### Post by Trebaruna on 2008-11-29
It isn't, it says it's all but empty.
You can easily disable swap if you like, by removing its entry from fstab or commenting it out. Alternately you can use swapoff to disable swap once. Please note that without swap you will not be able to hibernate. Then again, with some 8GB of RAM you do not really want to wait for that, I suppose.

By the way: please try and resize your screenshot, it makes for better viewing for people with puny laptop screens, and it doesn't really need to be that big, either.

---

### Post by anjanesh on 2008-11-29
> **Trebaruna said:**
> It isn't, it says it's all but empty.
**Shows 2.2MiB (0.1%) of 1.9GiB for swap.**
Whats stopping it from using the 2.2MB from RAM ?

---

### Post by Nepherte on 2008-11-29
It's probably some leftover from who knows what. That 0.1% can be safely considered as 0% and just because there's something in swap, doesn't always mean it's in use.

---

