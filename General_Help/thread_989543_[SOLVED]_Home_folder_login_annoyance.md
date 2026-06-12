---
title: "[SOLVED] Home folder login annoyance"
date: 2008-11-21
forum: General Help
---

### Post by L337_K3y5 on 2008-11-21
After I changed some settings on .wine folder in my home directory, whenever I log into my account, it goves me this opoup that says I need to chmod the .dmrc file using chmod 644.  I did what it said and it still gives me the same problem, and says that it will not save the language and session options.  Also, finally, it says that no one besides me should be able to write to my home directory - how do I fix this because I've uninstalled wine.....:confused:

---

### Post by taurus on 2008-11-21
Applications -> Accessories -> Terminal
```
chmod 755 ~
chmod 644 ~/.dmrc
```

---

