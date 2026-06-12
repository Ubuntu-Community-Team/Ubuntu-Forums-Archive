---
title: "strange alert on login"
date: 2008-11-30
forum: General Help
---

### Post by lametike on 2008-11-30
i forgotten when this started to happen but i feel it is abit strange.Every time i tried to logon to ubuntu,they would show this when i confirmed my password:
User's $HOME/.dmrc file is being ignored.This prevents the default session and language from being saved.File should be owned by the user and have 644 permissions.User's $HOME directory must be owned by user and not writable by other user.
i ignored this warning but it never stop show so i want to ask how to get rid of this and reading it,
i dont understand these 2 things:
it prevents to save the session which it always does,any error with the saving ?
and what does it mean to have 644 permission?

---

### Post by shafi on 2008-11-30
> **lametike said:**
> i forgotten when this started to happen but i feel it is abit strange.Every time i tried to logon to ubuntu,they would show this when i confirmed my password:
User's $HOME/.dmrc file is being ignored.This prevents the default session and language from being saved.File should be owned by the user and have 644 permissions.User's $HOME directory must be owned by user and not writable by other user.
i ignored this warning but it never stop show so i want to ask how to get rid of this and reading it,
i dont understand these 2 things:
it prevents to save the session which it always does,any error with the saving ?
and what does it mean to have 644 permission?

Did you upgrade or install a new version of ubuntu?
I had the same problem, but it solved automatically after some days.

---

### Post by nikgare on 2008-11-30
open a terminal and run this commands:
Code:
```

sudo chown -R $USERNAME: $HOME
chmod 755 $HOME
chmod 644 $HOME/.dmrc
```

---

