---
title: "VLC 0.9.2 won't start after some upgrades"
date: 2008-09-25
forum: General Help
---

### Post by webaake on 2008-09-25
Did some upgrades the other day, libc6 amongst them, and now VLC 0.9.2 won't start. I uninstalled it and reinstalled from backport repos.

Edit: Starting from terminal I get 'Segmentationfault'

I suspect it is lib6-2.7-10 that is the culprit.

Solution:

Solved it!

It was rather simple; started a film from terminal with parameter -vv and saw that the seg fault happend when trying to update.
Edited vlcrc and changed to 199 days interval for updating and set notification to 0 (zero).

Worked!

---

