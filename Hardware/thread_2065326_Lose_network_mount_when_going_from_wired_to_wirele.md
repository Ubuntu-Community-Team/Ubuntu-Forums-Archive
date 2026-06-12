---
title: "Lose network mount when going from wired to wireless"
date: 2012-10-01
forum: Hardware
---

### Post by jwillar on 2012-10-01
I'm running Xubuntu 12.04 on my pavilion laptop with four NAS shares mounted using 'nfs' in fstab.  Everything works until I disconnect the wired network cable and switch to wireless, then the nfs mounts fail.  Although this is normal thing to do with a laptop, losing the nfs mounts seems abnormal.  I have a work-around where I run umount the nfs mounts before disconnecting the wired network cable then mount the nfs mount once on wireless.  Using both launcher does save me from rebooting my laptop but losing the mounts like this normal behavior?  I can provide more details if needed but wanted to try the question in general terms first. 

jwillar

---

### Post by The Cog on 2012-10-01
I think it probably is normal. You almost certainly change IP address, so the server thinks it's a new connection from a different host. I can't think of an easy way round this.

---

