---
title: "Change GRUB meny"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by enurtav on 2007-08-13
How do I change the GRUB default boot.
If I want to change which OS version who is booting, how do I change he GRUB booting sequence?

---

### Post by merlinus on 2007-08-13
```

gksudo gedit /boot/grub/menu.lst

```

Look for a line near the top that says default 0 and change it to the OS you wish to be the default minus one.

For example, if windows is the fifth stanza, then change to

default 4.

-merlin

---

### Post by enurtav on 2007-08-13
Thanks for a quick answer. :):)

---

