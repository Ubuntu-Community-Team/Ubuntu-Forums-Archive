---
title: "Howto: Perform job at shutdown?"
date: 2008-08-23
forum: General Help
---

### Post by mrmorris on 2008-08-23
I'd like to perform some basic backing up when I shut down my computer and/or put it into hibernation. How can I install such a hook? Most automatic jobs seems to revolve around cron but that's not really what I need.

Thanks in advance,
Casper

---

### Post by kjohansen on 2008-08-24
you should be able to put a script into /etc/acpi/suspend.d to run when it hibernates.

---

### Post by mrmorris on 2008-08-24
Found a solution, the answer lies in hooking into the runtime levels:
[http://ubuntuforums.org/showthread.php?t=185261](http://ubuntuforums.org/showthread.php?t=185261)

---

