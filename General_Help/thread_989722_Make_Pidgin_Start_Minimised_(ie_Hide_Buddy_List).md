---
title: "Make Pidgin Start Minimised (ie Hide Buddy List)"
date: 2008-11-21
forum: General Help
---

### Post by jerremy-tamlin on 2008-11-21
This thread is a follow on from this one [http://ubuntuforums.org/showthread.php?p=6227378#post6227378](http://ubuntuforums.org/showthread.php?p=6227378#post6227378) which has been marked solved.

Unfortunately the solution didn't work for me, so I'm starting a new thread, that's not marked solved.


Solutions Tried:
Installed pidgin-extprefs and configured plugin to start hidden
Installed pidgin-plugin-pack and configured "Buddy List Options"
Created Startup script to make pidgin wait for a bit before starting
```
#!/bin/bash
sleep 20
/usr/bin/pidgin
```
Script must be executable.

Have noticed that at uni where the network connection is slower than pigion to startup, the buddy list starts hidden.
Also at home when I log out and log back in (without restarting my PC) the buddy list is already hidden.
But when starting up my system at home the buddy list always appears.:confused:

Any other suggestions are greatly appreciated.

Thanks.

---

### Post by ottabaub on 2012-01-25
I'm running Ubuntu 10.10 and before that 10.04. The script doesn't work. My script waits for 60 seconds before starting Pidgin and, even though I've installed the extended preferences 0.7 and selected "Hide buddy list on startup", it just doesn't matter. Even if I disable Pidgin on startup and run it manually the ^%$^##^ Buddy List still appears. This is really annoying.

---

### Post by BlinkinCat on 2012-01-25
> **ottabaub said:**
> I'm running Ubuntu 10.10 and before that 10.04. The script doesn't work. My script waits for 60 seconds before starting Pidgin and, even though I've installed the extended preferences 0.7 and selected "Hide buddy list on startup", it just doesn't matter. Even if I disable Pidgin on startup and run it manually the ^%$^##^ Buddy List still appears. This is really annoying.

This is a very old thread - maybe that is why you can't get result - :)

---

### Post by overdrank on 2012-01-25
Please start a new thread with your issues. Back to sleep thread. Thread closed.

---

