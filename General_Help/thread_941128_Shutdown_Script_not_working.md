---
title: "Shutdown Script not working"
date: 2008-10-07
forum: General Help
---

### Post by myth01 on 2008-10-07
I'm trying to get a temporary web server to power on and off routinely as I can't have it running overnight.  Powering up is fine and taken care of with wakeonlan from my main PC, but I want to run a script on the server at startup that will automatically shut it down at midnight so that I don't have to touch it again.

The script I think is fine and I've made it executable

```

#!/bin/bash
echo "Shutdown scheduled for 23:59"
sudo shutdown -h 23:59

```

and I've edited the sudoers

```

matt ALL = NOPASSWD: /sbin/shutdown

```

but it doesnt work.  If I run the script nothing happens.  If I run any of these
```

sudo shutdown -h now
shutdown -h now

```
at the terminal I'm still asked for a password.  Googling  turned up the solutions above but they all suggested this should be enough......

---

### Post by myth01 on 2008-10-07
Bump.  I'd really like to go to bed (0105GMT+1) but my usual stubborness rules and won't let me rest until this is sorted....!

---

### Post by myth01 on 2008-10-07
Is this in the right place?  Would it be better in a different category?

---

