---
title: "sudo gdm start for GUI?"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by slinkey1981 on 2008-12-02
OK, clean install of 8.04, did the "173 updates available" and now my computer will not boot into X without me typing

```
sudo gdm start
```

I guess it's not a huge problem, but it does get annoying having to type my password three times in three seconds...

1. failsafe terminal screen.
2. sudo gdm start (password)
3. Finally at the Ubuntu Login screen....

It's odd.

---

### Post by cariboo on 2008-12-02
It seems that somehow gdm is not starting automagically to repair this problem in a terminal type:

```
update-rc.d gdm start 30 2 3 4 5 . stop 70 0 1 6 .
```

Gdm should autmagically start after the next reboot.

Jim

---

### Post by slinkey1981 on 2008-12-02
> **cariboo907 said:**
> It seems that somehow gdm is not starting automagically to repair this problem in a terminal type:

```
update-rc.d gdm start 30 2 3 4 5 . stop 70 0 1 6 .
```

Gdm should autmagically start after the next reboot.

Jim

Thank you for the reply, after entering the above code, I was given

```
System startup links for /etc/init.d/gdm already exist.
```

and upon restart the issue persists.

---

