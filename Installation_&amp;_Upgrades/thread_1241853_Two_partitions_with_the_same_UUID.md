---
title: "Two partitions with the same UUID?"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by Jose Catre-Vandis on 2009-08-16
I needed to move my current xubuntu install from a primary partition into an extended partition as a logical partition, so I used gparted to do the copy and paste.

When checking for the requirements to enter into grub, it became apparent that the newly copied partition had the same UUID as the original!

For grub, this is easily overcome by using /dev/sd* in the stanza, but I was surprised that a new UUID was not issued. Can this be resolved with a command somewhere?

---

### Post by Keith Hedger on 2009-08-16
You can use the tune2fs command to set a new uuid ie:```

sudo tune2fs -U time /dev/sda7
```

---

### Post by Jose Catre-Vandis on 2009-08-16
> **Keith Hedger said:**
> You can use the tune2fs command to set a new uuid ie:```

sudo tune2fs -U time /dev/sda7
```

How did you know it was on /dev/sda7 :) LOL

Thanks for the tip

---

### Post by Keith Hedger on 2009-08-17
Whoops!

---

### Post by Soul-Sing on 2009-08-17
:lolflag:

---

