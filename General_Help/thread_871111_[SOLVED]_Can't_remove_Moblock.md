---
title: "[SOLVED] Can't remove Moblock"
date: 2008-07-26
forum: General Help
---

### Post by Ralphie on 2008-07-26
This package is messed up and has been for a while now. It wants to update, but can't, and all I want to do is remove the whole thing.
I get this message when I try to remove it:
> E: moblock: subprocess pre-removal script returned error exit status 3

Is there an easy way that I can just log in as root and enter some command to just get rid of it?

I don't even use the application, and now that my update manager ALWAYS says there is one update, I would just like to get rid of it.

Thanks

---

### Post by jwcgator on 2008-07-26
Make sure moblock is running when you remove it.

---

### Post by Ralphie on 2008-07-26
aaah that worked!
For reference, to start moblock i ran this command in the terminal:
```
sudo moblock-control start
```

and then just did a complete removal via synaptic


Thanks so much! Weeks of frustration are done with!
;)

---

