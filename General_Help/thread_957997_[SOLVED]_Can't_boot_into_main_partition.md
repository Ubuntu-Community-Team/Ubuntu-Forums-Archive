---
title: "[SOLVED] Can't boot into main partition"
date: 2008-10-24
forum: General Help
---

### Post by YAOMTC on 2008-10-24
I have two partitions on my computer: One with Kubuntu 32-bit, which I mainly use, and one with Kubuntu 64-bit, which I formerly just used when I wanted to use Cinelerra. Right now, I can't boot into my 32-bit partition; every time I enter my login and password a dialog comes up saying something like "the system is going down for halt in 3 minutes!" and then when I close that, the login screen tells me my login info was wrong. I suspect it has something to do with me shutting down without closing my shutdown script:
```
#!/bin/bash
sudo shutdown -h 01:00
```
Plus I shut down shortly before 1.

Anyone know of a solution to this? Think there may be a different problem?

EDIT: I booted into recovery mode, and restarted, and now for some reason it works. Huh.

---

### Post by YAOMTC on 2008-10-25
.

---

### Post by YAOMTC on 2008-10-25
.

---

