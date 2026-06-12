---
title: "Programs closing on resuming from hibernate"
date: 2008-08-25
forum: General Help
---

### Post by goeagles520 on 2008-08-25
I installed uswsusp to control the hibernation of my m1330 on Hardy. It gos into hibernate just fine, but when I result from hibernate, all the windows I had open in firefox are closed and firefox is not running. Additionally, thunderbird and pidgin are no longer running even though they were running before I went into hibernate. Anybody have any thoughts on this?

---

### Post by goeagles520 on 2008-08-26
Hello all,

After a bit of finagling, I found that yhis problem can be fixed by opening up /etc/uswsusp.conf and changing "shutdown method = platform" to "shutdown method= shutdown"

---

### Post by -Zeus- on 2008-08-26
cool.  Please mark the thread as solved.

---

