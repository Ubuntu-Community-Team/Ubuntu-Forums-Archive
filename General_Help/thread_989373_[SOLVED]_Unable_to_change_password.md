---
title: "[SOLVED] Unable to change password"
date: 2008-11-21
forum: General Help
---

### Post by bismark on 2008-11-21
I'm running a fairly clean install of 8.10 amd64 and I'm trying to change my password.

When I run chpasswd as my user I get the following:
```

$ chpasswd
chpasswd: can't lock password file

```

If I try it with sudo it just hangs.  What's going on here?

---

### Post by sisco311 on 2008-11-21
the command to change your password is:
```
passwd
```

---

### Post by bismark on 2008-11-21
> **sisco311 said:**
> the command to change your password is:
```
passwd
```

duh ](*,)

---

