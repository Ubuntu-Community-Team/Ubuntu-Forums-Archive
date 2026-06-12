---
title: "xmodmap for latin accents in hardy heron"
date: 2008-08-01
forum: General Help
---

### Post by esanchez on 2008-08-01
Hi everybody...
I used to type the following command to get accents in festy and gutsy:

xmodmap -e "keycode 113=Multi_key"


With that, I could use latin accents with the combination 

Alt + ' + <vocal (a,e,i,o,u)>

Seems that this is no longer working on Hardy Heron...

Any advices?

thanks in advance,
regards,
 -eduardo s.m.

---

### Post by pauper on 2008-08-01
:-k

```
xmodmap -e "keycode 113 = Multi_key"
xmodmap -e "keysym Multi_key = Multi_key Meta_R"
xmodmap -e "keysym Multi_key = Multi_key Alt_R"
```

Note: _=_ ?

---

