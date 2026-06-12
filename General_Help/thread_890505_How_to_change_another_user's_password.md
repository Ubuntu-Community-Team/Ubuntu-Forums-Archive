---
title: "How to change another user's password?"
date: 2008-08-15
forum: General Help
---

### Post by anderssl on 2008-08-15
Hey,

I recently installed Ubuntu 8.04 Hardy Heron on a computer that both me and my girlfriend use - and she immediately forgot her password. Is there any way I can reset her password for her?

Regards,
Anders Sundnes Løvlie

---

### Post by iaculallad on 2008-08-15
> **anderssl said:**
> Hey,

I recently installed Ubuntu 8.04 Hardy Heron on a computer that both me and my girlfriend use - and she immediately forgot her password. Is there any way I can reset her password for her?

Regards,
Anders Sundnes Løvlie

Boot in recovery mode:

```
passwd your_girlfriend's_username
```

and input your GF's new password.

OR try System->Administration->Users and Groups

---

### Post by sisco311 on 2008-08-15
> **anderssl said:**
> Hey,

I recently installed Ubuntu 8.04 Hardy Heron on a computer that both me and my girlfriend use - and she immediately forgot her password. Is there any way I can reset her password for her?

Regards,
Anders Sundnes Løvlie
If you have admin rights, then type:
```
sudo passwd *username*
```in a terminal

---

