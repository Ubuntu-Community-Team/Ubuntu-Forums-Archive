---
title: "Disable Update Manager Notifications"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by CarlosinFL on 2009-05-05
Is there any way to disable the 'Update Manager' notification window from popping up and annoying the heck out of me? I do updates every Friday on my system so I don't need to be reminded. Can someone please tell me how I can disable this notification process?

---

### Post by Sisophon2001 on 2009-05-05
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

You are not alone in disliking this "feature"

Garvan

---

### Post by CarlosinFL on 2009-05-05
Thanks! I think I am fairly responsible in doing updates with out having a dancing bear juggle in front of me. :P

---

