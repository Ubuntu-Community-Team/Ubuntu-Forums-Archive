---
title: "[SOLVED] &amp;quot;Shred&amp;quot; Firefox3 private data"
date: 2008-09-02
forum: General Help
---

### Post by DapperMe17 on 2008-09-02
Hi,


Just wondering if someone knows a hack or extension that "overwrites", and then deletes Firefox's private data(cookies, browsing hx, etc) when the browser closes?

By default, you can do a simple delete. However, wondering about a "secure" delete.

Thanks!

---

### Post by kidders on 2008-09-05
Hi there,

There are plenty of shredder applications around ... or you could roll your own by writing & writing & writing to the same files over and over ... however I'm not sure how easy it would be to get something like that to happen reliably, after Firefox closes.

In theory, executing one command after another is a matter of ...```
firefox ; shred /path/to/cookies
```
I suspect, however, that there are situations where Firefox may return control to a terminal while it's still running.  I don't have a copy handy at the moment, so I can't test that for you.

If I'm right, the answer to your question is a little more complicated ... but it's still very doable. For example, you could run a daemonised process that sits & waits for the number of running Firefox instances to drop to zero, and shreds your private data.

**Question:** How important is it that your browser gets destroyed when the browser *closes*? Would it be acceptable to wait until you log out ... or even better ... until you shut down your computer?

You see, depending on the level of security you require, one possible (and quite easy) approach might be to store your browser data in RAM, rather than on disk.

---

### Post by DapperMe17 on 2008-09-05
kidders,

Thanks for taking the time to reply!

Rather than dabble in endless script, I've come accross exactly what you have mentioned. 

It's a Firefox extension called "Distrust".

Rather than writing private data to disk, it only runs it in memory. Then, those files "evaporate", and therefor, no need to clearing as they never made it on to the HD in the first place.

---

