---
title: "Doesnt update properly."
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by noveus on 2009-10-04
This is the what went wrong. Please help me out, and thanks for your help

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 103, in _process_transaction
    self.commit_packages(**self.trans.kwargs)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 146, in commit_packages
    self._commit_changes()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 429, in _commit_changes
    self._cache.commit(fetch_progress, inst_progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 311, in commit
    res = self._fetchArchives(fetcher, pm)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 234, in _fetchArchives
    raise LockFailedException("Failed to lock %s" % lockfile)
LockFailedException: Failed to lock /var/cache/apt/archives/lock

---

### Post by ermeyers on 2009-10-04
What was the command, and were you root at the time?  Did you sudo?

---

