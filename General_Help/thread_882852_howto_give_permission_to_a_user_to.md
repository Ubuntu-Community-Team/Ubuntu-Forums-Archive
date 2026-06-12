---
title: "howto give permission to a user to"
date: 2008-08-07
forum: General Help
---

### Post by adhg on 2008-08-07
Hi there,

I have a user that I wish to upgrade to be part of a 'sudo' group and another user where I wish to remove from the 'sudo' group, how can I achieve this?

Thank you!

---

### Post by cariboo on 2008-08-07
Have a look at this page:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You should find all the info you need.

Jim

---

### Post by LitusMayol on 2008-08-07
Hey man!

Not such difficult.
Go to "*System>Administration>Users and Groups*". A window will be opened. There you mut press "*Unlock*" (it will request you the sudo password). And finally press on "*Manage Groups*" or "*Groups Managing*" (I've catalan as language, so I don't know how it is in english). 

Hope it helps!

---

### Post by drs305 on 2008-08-07
> **LitusMayol said:**
> 
Go to "*System>Administration>Users and Groups*". A window will be opened. There you mut press "*Unlock*" (it will request you the sudo password). And finally press on "*Manage Groups*" or "*Groups Managing*" (I've catalan as language, so I don't know how it is in english). 

To carry it to conclusion: 
Once you have 'unlocked' it, you can go to Manage Groups, scroll to 'Admin' and tick or untick each user; or you can select each user, then Properties, User Privileges tab. Sudo is the "Administer the system" block.

---

### Post by sisco311 on 2008-08-07
from the terminal:
```
sudo adduser *username *admin
sudo deluser *username *admin
```

---

