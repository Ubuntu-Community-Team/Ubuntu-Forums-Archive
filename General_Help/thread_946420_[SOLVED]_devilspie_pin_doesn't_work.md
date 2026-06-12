---
title: "[SOLVED] devilspie pin doesn't work"
date: 2008-10-13
forum: General Help
---

### Post by jazzgossen on 2008-10-13
I want to use devilspie to make all Pidgin conversations always show on the current desktop.

I wrote the following file ~/.devilspie/gaim-conversations.ds
```

(if
    (or
     (is (application_name) "gaim")
     (is (application_name) "pidgin")
     )
    (begin
        (pin)
    )
)

```

I run "devilspie -d" and it seems to read the file allright, but when I open a Pidgin conversation, it doesn't get pinned.

Any ideas why?

---

### Post by jazzgossen on 2008-10-13
Sorry. I just had to change "piding" to "Pidgin". Now it works.

---

