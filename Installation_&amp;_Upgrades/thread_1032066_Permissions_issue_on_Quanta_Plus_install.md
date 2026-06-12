---
title: "Permissions issue on Quanta Plus install"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by DarkSoul1984 on 2009-01-06
When I install quanta plus, either through apt-get or Add/Remove on the menu, I get permissions errors when I try to run it.

When I run it using sudo from the terminal, it runs fine.

Here is the terminal printout of errors:

Session management error: None of the authentication protocols specified are supported
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
Qt: Session management error: None of the authentication protocols specified are supported
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/tmp-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/tmp-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/tmp-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/tmp-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/tmp-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
kdialog(20146): Failed to lock file "/home/abaldwin/.kde/cache-abaldwin-laptop/kpc/kde-icon-cache.lock" , last result = 2 
kdialog(20146): Couldn't create index file "/home/abaldwin/.kde/cache-abaldwin-laptop/kpc/kde-icon-cache.index" 
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/tmp-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/socket-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/socket-abaldwin-laptop: Permission denied
kdeinit: Aborting. No write access to '/home/abaldwin/.ICEauthority'.
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/tmp-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/socket-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/socket-abaldwin-laptop: Permission denied
kdeinit: Aborting. No write access to '/home/abaldwin/.ICEauthority'.
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
ICE default IO error handler doing an exit(), pid = 20120, errno = 11
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/share: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/cache-abaldwin-laptop: Permission denied
trying to create local folder /home/abaldwin/.kde/tmp-abaldwin-laptop: Permission denied
KCrash: Application 'quanta' crashing...
Warning: connect() failed: : Permission denied
KCrash cannot reach kdeinit, launching directly.

Any ideas?

---

