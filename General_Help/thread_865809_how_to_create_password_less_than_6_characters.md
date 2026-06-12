---
title: "how to create password less than 6 characters?"
date: 2008-07-21
forum: General Help
---

### Post by serendipity1276 on 2008-07-21
I need to create a user's password that is less than 6 characters.  Ubuntu is not letting me.

Anyone knows how?  Thanks.

---

### Post by iaculallad on 2008-07-21
> **serendipity1276 said:**
> I need to create a user's password that is less than 6 characters.  Ubuntu is not letting me.

Anyone knows how?  Thanks.

Try to edit the file below:

```
gksudo gedit /etc/pam.d/common-password
```

and uncommenting the line w/c says:

> # password required       pam_cracklib.so retry=3 minlen=6 difok=3

and try changing the **minlen** integer value.

---

