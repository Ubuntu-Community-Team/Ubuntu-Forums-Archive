---
title: "How can I tell what settings my x server is using?"
date: 2008-10-09
forum: General Help
---

### Post by joe56 on 2008-10-09
ubuntu's xorg.conf is sparse and most of the settings seem to be auto-detected behind the scenes. 

Is there any way I can see exactly what settings my x server is using for ubuntu right now? I'm trying to write a xorg.conf for another distro. Thank you.

---

### Post by ModelM on 2008-10-09
Everything that X detects, decides, enables, disables, etc. can be found in the log file.

The log file for the current session is```
/var/log/Xorg.0.log
```

The log file from the previous session is```
/var/log/Xorg.0.log.old
```

The easiest way to view the current log is probably to use the log file viewer.

System > Administration > System Log

And just select the Xorg log in the box on the left.

---

### Post by joe56 on 2008-10-09
Thank you.

---

