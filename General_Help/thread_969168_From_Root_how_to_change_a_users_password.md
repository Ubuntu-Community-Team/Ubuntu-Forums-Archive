---
title: "From Root how to change a users password"
date: 2008-11-03
forum: General Help
---

### Post by ka1eui on 2008-11-03
I have a user who has forgotten his password.  How do I log in as root and update his password?

Thanks!
KA1EUI

---

### Post by ibutho on 2008-11-03
Depending on how your system is setup, try
```
sudo passwd someuser
```
or
```
su -
passwd someuser

```
If you prefer the GUI, try the User and Group config tool somewhere in System -> Administration.

---

