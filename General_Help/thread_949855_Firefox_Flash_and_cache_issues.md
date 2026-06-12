---
title: "Firefox Flash and cache issues"
date: 2008-10-16
forum: General Help
---

### Post by JakeWatkins on 2008-10-16
OK - two more things. = )

Whenever I play the online game, RuneScape, I should keep a cache, and it made the folder to, but everytime I close Firefox, it deletes the cache...

any help with that?

And my flash still doesn't seem to work... I was trying skreemr.com and it didn't.

---

### Post by aysiu on 2008-10-16
For the first problem, try this:

**Step 1**
Close Firefox

**Step 2**
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R jake:jake ~/.mozilla
```

**Step 3**
Start Firefox and play RuneScape. See if the problem persists.

For the second problem, can you be more specific? What exactly happens when you try that site? Does Flash work for other sites? Which Flash did you install?

---

### Post by JakeWatkins on 2008-10-16
Well, not really sure if that fixed it or not, because now Java only loads half the screen for RuneScape. :p

---

