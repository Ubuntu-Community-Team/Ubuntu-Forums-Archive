---
title: "Script to autostart and stop a program"
date: 2008-10-14
forum: General Help
---

### Post by Jackelope on 2008-10-14
Hello everyone. I'm trying to write a script to start a program (Mint Menu), run it for 30 minutes, close it, and repeat forever. Basically it would just close and reopen the program every half hour. The reason I need this is because of a memory leak in the program which hasn't been fixed and might not be for a while. This seems like it might be a good work around. Can anyone direct me to a template for accomplishing this? Thanks!

---

### Post by scragar on 2008-10-14
I don't know the command for the mint menu, but you can replace that in the code:
```

#!/bin/bash
Mmenu="**MINT MENU**"
while [  TRUE ]; do
  $Mmenu &
  sleep 30m
  killall $Mmenu
done

```

EDIT: replace **MINT MENU** with the mint menu command, whatever that's called.

---

### Post by Jackelope on 2008-10-15
scragar, thanks for the script! Runs beautifully. I appreciate it.

---

