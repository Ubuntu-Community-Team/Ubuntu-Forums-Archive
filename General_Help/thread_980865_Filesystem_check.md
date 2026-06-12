---
title: "Filesystem check"
date: 2008-11-13
forum: General Help
---

### Post by ykcirt on 2008-11-13
Is there a method or command to check which filesystem I used for my installation? I can't use the partition manager on the LiveCD (just to check which one I have, not to reinstall the whole installation again) because there isn't a DVD-rom player connected to my system right now, and I don't have one laying around either.

I want to try out the ext3 filesystem boost tweak since I never had problems with my power supply before. But for that to work I have to know if I even use ext3. I let Ubuntu choose the default during reinstallation a few days ago.

---

### Post by pedro_orange on 2008-11-13
```
df -T
```

---

### Post by geirha on 2008-11-13
I take it the Ubuntu installation is working ok? If so, open a terminal and type ```
mount
``` to list all currently active mounts. Most likely your partitions have ext3 filesystems, since that's what the installer uses by default.

EDIT: You can also find this information under System -> Administration -> System Monitor

---

### Post by ykcirt on 2008-11-13
Thanks guys. Appreciated.

---

