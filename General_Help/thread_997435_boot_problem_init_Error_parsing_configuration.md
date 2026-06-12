---
title: "boot problem: init: Error parsing configuration"
date: 2008-11-29
forum: General Help
---

### Post by si2718 on 2008-11-29
Hello all,

Ive been using ubuntu (8.10) a while, and yesterday updated to the latest kernel release and nvidia resitricted drivers. i restarted and no problems at all. Then earlier today I upgraded to the latest vmware-player (from the bundle on their site, not the package) and initially had no issues. however i just restarted and now I get:

Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
init: Error parsing configuration: Not a directory
[ xx] Kernel panic - not syncing: Attempted to kill init!

Googling shows that the kpanic is simply related to the most recent error, so the directory problem. 

I used a live CD to mount the partition in an attempt to access the initrd.img but cant work out the mount of the .img

I then tried restoring the initrd.img.old but to no avail...

any suggestions? thanks!!!

---

### Post by si2718 on 2008-11-29
I thought it was faulty RAM, but it was just that one DIMM some how popped out. So now RAM test is fine, but i still cant boot... any ideas?

---

### Post by si2718 on 2008-11-30
Does anyone know what tried to run after /scripts/init-bottom ?

thanks

---

