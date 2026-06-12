---
title: "Unable to nfs mount"
date: 2008-11-11
forum: General Help
---

### Post by supradave on 2008-11-11
I am getting an "internal error" when I'm trying to mount an nfs share.  I have verified that the nfs server is running and I can telnet to port 2049 on the server, both locally and remotely.  But no matter how I set up /etc/exports and the mount command, I get the "internal error."  I don't see any logging in /var/log of why this might fail and $? is returning 32.

mount -t nfs server:/home/share /mount
or
mount -t nfs ipaddress:/home/share /mount

/etc/exports
/home/share   *(rw,sync)

I get warnings regard the subtree stuff when I run exportfs, but I just want to get it to mount, then deal with that.

Hours of searching gives lots of no ideas.  Any help here?

Thanks,
Dave

---

