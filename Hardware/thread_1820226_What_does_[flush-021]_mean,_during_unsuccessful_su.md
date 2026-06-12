---
title: "What does [flush-0:21] mean, during unsuccessful suspend / resume?"
date: 2011-08-07
forum: Hardware
---

### Post by skief on 2011-08-07
If I run ```
ps aux
``` I see a process described as ```
[flush-0:21]
```can anyone tell me what this means? Something to do with kernel garbage collection?

My Gateway EC58 is suspending but refusing to resume. I've been logging the running processes before it suspends, and, right after the sync process initiated by pm-suspend, this "flush-0:21" process comes up.

HOWEVER: for a little while, resume was working! During that time, "flush-0:21" did NOT come up. Now, resume has stopped working again, and this process too has begun to come up again. :confused:

Thanks!

---

