---
title: "NFS mount problems on liveCD"
date: 2008-09-16
forum: General Help
---

### Post by MikeyCarter on 2008-09-16
This is really starting to bug me.

I've got the Ubuntu and XUbuntu liveCD's booting.   1 out of 20 retries.   The problem is when it does the NFS mount.

I get "no route to host" in the logs.   Once it drops to the busybox prompt I can do the nfs mount manually no problem.

So rather then changing the scripts in ubuntu I'm trying to tune nfs.  However the nfsroot=server:path,options  (the options) part is not working.  It tacks it on the end as if it's part of the path.   Is there a way to get this working consistently.

Is there another way of mounting the liveCD's without using nfs?  Is there a complete list of boot parameters somewhere?

---

