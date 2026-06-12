---
title: "Emerald Randomly Quitting"
date: 2008-07-26
forum: General Help
---

### Post by ProgenitorVirus on 2008-07-26
Pretty self-explanatory, sometimes emerald will just quit, no idea why.

Compiz stays up though.  Any way to fix this?

Thanks!

---

### Post by overdrank on 2008-07-26
> **ProgenitorVirus said:**
> Pretty self-explanatory, sometimes emerald will just quit, no idea why.

Compiz stays up though.  Any way to fix this?

Thanks!

Hi is there any certain point when emerald quits? Like after screen saver, after playing a game? Could you give us some info on the graphics and I assume you are using Hardy.

---

### Post by 00arthuryu on 2008-07-27
I had this problem before I compiled compiz from git. I think it is a bug in emerald. I think it is fixed in the new emerald. But I put 
```
emerald --replace
```
into one of the custom commands in compiz (ccsm->GeneralOptions->commands) and shortcut it to shift+ctrl+E
more of a lame workaround than anything. But it is a good temporary solution.

---

