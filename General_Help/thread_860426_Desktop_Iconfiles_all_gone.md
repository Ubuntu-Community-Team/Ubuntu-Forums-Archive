---
title: "Desktop Icon/files all gone"
date: 2008-07-15
forum: General Help
---

### Post by nearownkira on 2008-07-15
Today after I log in, I found that my icon on the desktop all gone.I checked using nautilus under the /home/desktop folder , the files is still there. I also tried to put it on the desktop but failed.How to change it back?

I am using Ubuntu hardy

---

### Post by markharding557 on 2008-07-15
do they reappear if you restart the desktop

---

### Post by Execute_Method on 2008-07-15
Try this:

Open terminal & type:

```
gconf-editor
```

Navigate to apps --> nautilus --> preferences and on the right-side look for “show_desktop”.  Toggling this will toggle your desktop icons/files.

---

