---
title: "[SOLVED] $home/.dmrc being ignored"
date: 2008-11-01
forum: General Help
---

### Post by charonred on 2008-11-01
I'm using 8.04.1 and on startup, just before normal logon screen, I'm getting a message saying something like;

*$home/.dmrc is being ignored and that the user should be the owner and that permissions should be 644* (from memory)

it just started doing this yesterday.

Following the advice of some other posts I changed the permissions to rxr-r- (I think that's 644); however I'm still getting the message and have to click OK before my PC completes its startup.

---

### Post by charonred on 2008-11-01
sorted it out - used this to fix the problem, rebooted and started as normal with no 'error' message :)

> chmod 700 /home/username/

chmod 644 /home/username/.dmrc

---

