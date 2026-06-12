---
title: "how to disable swap?"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by melquiades on 2006-03-18
guys,
      Just a quick newbie question, how is swap disabled? Just heeding some power-saving advice since I don't get to use swap at all.

Thanks in advance

---

### Post by klahjn on 2006-03-18
[QUOTE=melquiades]guys,
      Just a quick newbie question, how is swap disabled? Just heeding some power-saving advice since I don't get to use swap at all.
Thanks in advance[/QUOTE]

Personally, not having a swap partition is not necessarily the best idea in the world.  If you google it, you should find some directions in how to disable your swap partition, but you would be wise to keep it, for problems may arise once that partition is removed.  Not that i'm trying to scare you into keeping it, but i think the gremlins that live inside your computer would not be very happy!

---

### Post by melquiades on 2006-03-18
I'm also suspecting that it is somehow connected with my inability to restart under ubuntu, since it has difficulty unmounting swap during shutdown.  But there are also times when my ubuntu can reboot successfully; I was jusn't quick enough to notice the console messages when it did.

---

### Post by jd65pl on 2008-01-21
Turning off swap can be a good idea if the kernel you are using is aggressively swapping i.e. swapping when there is still free memory only to swap back in moments later. You will need to remove the swap line in fstab too.

```
nano /etc/fstab
```

---

