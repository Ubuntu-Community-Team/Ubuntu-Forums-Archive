---
title: "File .dmrc Being Ignored"
date: 2008-08-08
forum: General Help
---

### Post by RATM_Owns on 2008-08-08
Every time I need to log in (I usually keep the computer locked) it gives me a message about file .dmrc being ignored and home needs to have 644 permissions and not be writable for anyone else.

So I made a little fix script for it
```
#!/bin/bash

sudo chown -hR andy:andy /home/andy
```

So I just log into the failsafe terminal and run that.

But is there a way so that never happens anymore?

---

### Post by x1a4 on 2008-08-08
Hi,

Do what the message says and set permissions of ~ to 644
```
chmod 644 /home/andy
```

---

