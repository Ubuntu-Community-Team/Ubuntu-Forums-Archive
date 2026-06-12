---
title: "can't i access the root"
date: 2008-07-17
forum: General Help
---

### Post by masoud23 on 2008-07-17
Hi

Why can't i access the root? i write: su root and then i write password by i get this message: su: Authentication failure
Sorry.

i write right password but still no access.

---

### Post by jonian_g on 2008-07-17
To use root, use "sudo <command>" in terminal.

ex., to run gedit in root, "sudo gedit"
and it will prompt you for your password.

To become root type:

```
sudo su
```

---

### Post by iaculallad on 2008-07-17
Or you could:

```
sudo -i
```

and input your password.

---

### Post by dentaku65 on 2008-07-17
> **masoud23 said:**
> Hi

Why can't i access the root? i write: su root and then i write password by i get this message: su: Authentication failure
Sorry.

i write right password but still no access.

Well... you don't need it  :-)
Basically sudo command acts like root and is safer to use this way expecially for unexperienced users, this does not means that is not possible to use su command of course.

---

