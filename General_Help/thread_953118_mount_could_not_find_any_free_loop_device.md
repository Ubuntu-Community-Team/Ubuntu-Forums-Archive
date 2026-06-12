---
title: "mount: could not find any free loop device"
date: 2008-10-19
forum: General Help
---

### Post by zephyrus17 on 2008-10-19
So, I've been mounting .iso(s) onto /media/cdrom to install a game, but when it asks me to swap a cd again, it says mount: could not find any free loop device. So how do I free it up?

---

### Post by shawnrgr on 2008-10-20
you installing a game through wine? if so, open a terminal

```
wine eject
```

if not, you exausted the free loop devices. Free one (umount any in use) and try again. You can see what is being used by a loop device with losetup:

```
# losetup /dev/loop0
```

---

### Post by zephyrus17 on 2008-10-21
But after I see what's there, how do I free up the loop space?

---

### Post by shawnrgr on 2008-10-21
unmount it

> **shawnrgr said:**
> if not, you exausted the free loop devices. Free one **(umount any in use)** and try again. You can see what is being used by a loop device with losetup:

```
# losetup /dev/loop0
```

---

