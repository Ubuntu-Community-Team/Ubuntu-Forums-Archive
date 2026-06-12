---
title: "[SOLVED] explorer.exe in my ubuntu...?"
date: 2008-09-20
forum: General Help
---

### Post by ronz0o on 2008-09-20
Firefox crashed on me, so I brought up system monitor to check and see what the problem was. why is explorer.exe running on my system...? I have no windows connection to this computer. =)

pic is self explanatory

---

### Post by ronz0o on 2008-09-20
I do have wine installed, and use it from time to time. Could an unclean exit of wine cause this?

---

### Post by hyper_ch on 2008-09-20
what does
```

ps aux | grep explorer

```
return?

---

### Post by ronz0o on 2008-09-20
ronzo    18508  0.0  0.0   3004   752 pts/0    R+   17:43   0:00 grep explorer

---

### Post by hyper_ch on 2008-09-20
I think it's wine related.

---

### Post by ronz0o on 2008-09-20
ok, ty. I just thought it was odd seeing explorer.exe running. I always just see wine whenever I look in the system monitor

---

