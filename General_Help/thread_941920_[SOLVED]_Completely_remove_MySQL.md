---
title: "[SOLVED] Completely remove MySQL"
date: 2008-10-08
forum: General Help
---

### Post by prem1er on 2008-10-08
I want to complete remove MySQL and start from scratch.  I tried ```
apt-get remove mysql-server-5.0
```

but it kept the password file for my root user.  How can I remove everything that MySQL used for a fresh start?

---

### Post by spiderbatdad on 2008-10-08
maybe```
sudo apt-get remove --purge mysql-server-5.0
```

---

### Post by prem1er on 2008-10-08
> **spiderbatdad said:**
> maybe```
sudo apt-get remove --purge mysql-server-5.0
```

w00t! Thanks.

---

