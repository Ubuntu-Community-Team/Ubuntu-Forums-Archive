---
title: "can't login after using gparted"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by Aboelnour on 2009-07-19
peace upon u:
after Using Gparted to expand my space on Ubuntu problem occurs :(
after i finish i reboot my system and the grub work but when i choose Ubuntu this message appear :

> run-init: /sbin/init: Not a directory
[9.610618 ]Kernal panic - not syncing: Attemped to Kill init
thanks in advance :)

---

### Post by Aboelnour on 2009-07-19
?????

---

### Post by merlinus on 2009-07-19
It is possible that the UUID for your ubuntu partition changed due to moving/resizing.
```

blkid
```

will show what it is, and then compare the results with the entries in /boot/grub/menu.lst.

---

### Post by Aboelnour on 2009-07-19
> **merlinus said:**
> It is possible that the UUID for your ubuntu partition changed due to moving/resizing.
```

blkid
```

will show what it is, and then compare the results with the entries in /boot/grub/menu.lst.

i try it but the UUID is the same

---

### Post by Aboelnour on 2009-07-21
help needed please :)

---

