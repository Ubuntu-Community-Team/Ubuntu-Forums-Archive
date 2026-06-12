---
title: "Syncing Pocket PC with Evolution using Opensync"
date: 2008-11-06
forum: General Help
---

### Post by wersdaluv on 2008-11-06
Has anyone managed to make this work? I installed all the required packages. Whenever I try to sync, I get this: ```
multisync0.90 
The previous synchronization was unclean. Slow-syncing
DEBUG:SynCE:Connect() called
ERROR:SynCE:connect() failed: org.freedesktop.DBus.Error.ServiceUnknown: The name org.synce.SyncEngine was not provided by any .service files
Member 2 of type evo2-sync had an error while connecting: Unable to open anything
Traceback (most recent call last):
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 131, in _CBConnectOnIdle
    ctx.report_error()
  File "/var/lib/python-support/python2.5/opensync.py", line 132, in report_error
    def report_error(*args): return _opensync.OSyncContext_report_error(*args)
TypeError: OSyncContext_report_error expected 3 arguments, got 1


```

---

### Post by u2ix on 2009-02-26
same problem here

---

### Post by bobya on 2009-04-17
I can also confirm this bug on Jaunty. If more info is needed I am willing to help, as much as I can, for resolving this issue.

---

### Post by wersdaluv on 2009-04-17
It's been years but this issue is still unresolved.

---

### Post by carstanje on 2009-05-13
Same here! It worked for one time. When you try to resync after a reboot it doesn't work anymore. Strange...

---

### Post by wersdaluv on 2009-05-13
> **carstanje said:**
> Same here! It worked for one time. When you try to resync after a reboot it doesn't work anymore. Strange...
haha. I gave up already. lolz. It's been a while eh?

---

### Post by carstanje on 2009-05-14
Don't give up to quickly! Open a new terminal window and enter: 
> synce-sync-engine
When I did this the sync continued in the new terminal. When you do this the sync works fine! At least for me it did...

So this error pops up because sync-engine isn't loaded at the time it should be. Instead of showing an error it should launch synce-sync-engine.

---

### Post by odzk on 2010-12-10
> **carstanje said:**
> Don't give up to quickly! Open a new terminal window and enter: 

When I did this the sync continued in the new terminal. When you do this the sync works fine! At least for me it did...

So this error pops up because sync-engine isn't loaded at the time it should be. Instead of showing an error it should launch synce-sync-engine.

This solves the problem. Thanks.

---

