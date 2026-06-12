---
title: "[SOLVED] what is the default permissions for /usr/bin"
date: 2008-07-25
forum: General Help
---

### Post by lsd33 on 2008-07-25
what is the default (out of the box) permissions for /usr/bin... I stupidly changed some stuff around, broke my machine, and "fixed" everything by changing the permissions for /usr/bin to 777 which I know is *not good*.

---

### Post by tamoneya on 2008-07-25
755 and owned by root:root
```
drwxr-xr-x   2 root root 49152 2008-07-25 10:28 bin

```

---

### Post by lsd33 on 2008-07-25
..and that would be chmod 755 if Im not mistaken?

---

### Post by tamoneya on 2008-07-25
you are correct.  You will need a sudo though making it ```
sudo chmod 755 -R /usr/bin
```

---

### Post by lsd33 on 2008-07-25
thanks very kindly. lol, I locked myself out of sudo when I changed /usr/bin's permissions so I am now more aware than ever that sudo precedes all important commands.

---

### Post by tamoneya on 2008-07-25
> **lsd33 said:**
> thanks very kindly. lol, I locked myself out of sudo when I changed /usr/bin's permissions so I am now more aware than ever that sudo precedes all important commands.

thank you for marking as solved.

---

