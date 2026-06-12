---
title: "ddclient Daemon Does Not Auto-Start"
date: 2008-10-14
forum: General Help
---

### Post by thegodfaza on 2008-10-14
On my server I am running ddclient. It doesn't run at boot unless I put it into rc.local. The daemon works if I manually stop it and start it. It has a symbolic link in /etc/rc2.d/. I tried moving it up to 99 from being 20 and still no luck. I would like the daemon to work instead of having to run ddclient through rc.local.

EDIT: I lowered the ttl in ddclient and it works on the second call. When it's in rc.local it works on the first call.

---

