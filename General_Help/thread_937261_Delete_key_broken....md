---
title: "Delete key broken..."
date: 2008-10-03
forum: General Help
---

### Post by superbenny on 2008-10-03
I check gconf-editor to make sure that the run_command_screenshot was set to "print" and it was, which makes me think that somehow, the delete key is mapped to the print key. In xev, my delete key brings event 59.
Here's a bit from my "xmodmap -pke"
```

keycode 107 = Delete
keycode 108 = KP_Enter
keycode 109 = Control_R
keycode 110 = Pause Break
keycode 111 = Print Sys_Req
```

---

