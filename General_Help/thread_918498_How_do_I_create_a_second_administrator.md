---
title: "How do I create a second administrator?"
date: 2008-09-13
forum: General Help
---

### Post by Maheriano on 2008-09-13
How do I create a new user that can administrate the system? I create a new user with the useradd function, then I give it a password, then I try to log into Gnome with it and it tells me there's a bad username/password. So I su to root and use adduser instead, I manage to log in but they don't have administrative privaleges to change system settings and modify other users.

---

### Post by iaculallad on 2008-09-13
In the terminal:

```
sudo usermod -aG admin username
```

---

### Post by Maheriano on 2008-09-17
Worked. Solved. Thanks.

---

