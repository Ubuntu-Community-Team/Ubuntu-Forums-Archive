---
title: "[SOLVED] deleted items folder"
date: 2008-09-24
forum: General Help
---

### Post by kadafi69 on 2008-09-24
there seem to be some files and folders stuck in my deleted items folder, i cant seem to get rid of any of them it just asks me to skip them. any ideas?

---

### Post by tuxxy on 2008-09-24
Open terminal and run nautilus as sudo to delete them 

```
gksu nautilus /root/.local/share/Trash
```

Obviously you would replace the /root/.local/share/Trash with your trashs location, as that would bring up the root trash folder.

---

### Post by kadafi69 on 2008-09-24
many thanks.

---

