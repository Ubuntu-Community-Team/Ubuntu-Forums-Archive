---
title: "ThinkPad Buttons using tpb"
date: 2013-08-01
forum: Hardware
---

### Post by Steve_Richardson on 2013-08-01
[Ray John's 2010 post]("http://ubuntuforums.org/showthread.php?t=1500556&highlight=tpb") on how to get tpb working is excellent. (tpb provides an on-screen display of volume and screen brightness as adjusted with the ThinkPad buttons.) I found, however, that I could never get a tbd daemon thread running as root. Adding entries to /etc/sudoers in an attempt to allow my user to run sudo without supplying a password did not work.  (I am certain this is operator error on my part and not the fault of Ray's great instructions.)  I added my user to group kmem, and now run tpb as a daemon thread under my user's ownership using startup applications. This appears to work, at least so far.

---

