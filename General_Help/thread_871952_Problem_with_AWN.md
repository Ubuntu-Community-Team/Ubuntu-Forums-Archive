---
title: "Problem with AWN"
date: 2008-07-27
forum: General Help
---

### Post by thewolf32 on 2008-07-27
I have a little issue with AWN, and it's the only thing that annoys me in it.

The dock works very well as laucnher, but when it comes to task manager, there is this issue: When I maximize and minimize a window, sometimes it closes from the dock, for a few seconds it turns into a "No name" icon and then appears again at the right of the dock, and stays there.

It happens many times and it's really annoying. Does anyone knows what could be causing this?

Thanks.

**Here is a video that shows better what the problem is:**

[http://rapidshare.com/files/132885251/out.ogg.tar.gz.html](http://rapidshare.com/files/132885251/out.ogg.tar.gz.html)

---

### Post by Mgiacchetti on 2008-07-27
the non use of Cairo Dock as a dock bar??

---

### Post by thewolf32 on 2008-07-27
> **Mgiacchetti said:**
> the non use of Cairo Dock as a dock bar??

It's not Cairo dock, it's Avant Window Navigator.

I added a video that shows a lot better what the problem is.

---

### Post by thewolf32 on 2008-07-27
Anyone?

---

### Post by thewolf32 on 2008-07-28
*bump*

---

### Post by moonbeam on 2008-07-28
> **thewolf32 said:**
> I have a little issue with AWN, and it's the only thing that annoys me in it.

The dock works very well as laucnher, but when it comes to task manager, there is this issue: When I maximize and minimize a window, sometimes it closes from the dock, for a few seconds it turns into a "No name" icon and then appears again at the right of the dock, and stays there.

It happens many times and it's really annoying. Does anyone knows what could be causing this?

Thanks.

**Here is a video that shows better what the problem is:**

[http://rapidshare.com/files/132885251/out.ogg.tar.gz.html](http://rapidshare.com/files/132885251/out.ogg.tar.gz.html)

This is a known issue that appears to be related to issues wtih libwnck signals.  It is expected to be resolved somewhere in the 0.4 - 0.6 timeframe.

In the meantime if it really bothers you there are always standalone-launcher / standalone taskmanager applets which do not have this issue (they will not be back in the awn-testing PPA until vala 0.3.5 is released).  If you do try them out I _STRONGLY_ suggest you read [http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1495](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1495)

---

