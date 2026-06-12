---
title: "reset K menu"
date: 2008-07-27
forum: General Help
---

### Post by brett611 on 2008-07-27
If I've overcustomized what is/is not in the K Menu how do I restore it to the default setting/display?  That is, I want it to show all applications

thx

---

### Post by iaculallad on 2008-07-27
> **brett611 said:**
> If I've overcustomized what is/is not in the K Menu how do I restore it to the default setting/display?  That is, I want it to show all applications

thx

Try:

```
sudo rm ~/.config/menus/applications-kmenuedit.menu
```

and do a logout then log back in.

---

### Post by brett611 on 2008-07-28
Thanks.  That did it.  Also found this link when googling your suggestion (can't be too sure when it comes to rm)

[http://ubuntuforums.org/showthread.php?t=204828](http://ubuntuforums.org/showthread.php?t=204828)

---

