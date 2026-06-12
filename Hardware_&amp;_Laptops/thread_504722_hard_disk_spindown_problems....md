---
title: "hard disk spindown problems..."
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by roots on 2007-07-19
hi,

i've got an "old" western digital 80gb ide hdd serving as a once-in-a-long-while storage that i want to automatically spin down after a given period of idle time.

so what i do is set

```
sudo hdparm -S20 /dev/hdc
```

but - the drive stays up no matter what timeouts i choose. with my other hard drives this works without problems.

now what i can do is

```
sudo hdparm -y /dev/hdc
```

which makes the drive spin down immediately, so it is obvious that spinning down to standbye is in fact supported by the drive.

now - does anyone know how to "force" the timed spindown or any workaround to make the drive go to standbye automatically?


cheers,
roots.

---

