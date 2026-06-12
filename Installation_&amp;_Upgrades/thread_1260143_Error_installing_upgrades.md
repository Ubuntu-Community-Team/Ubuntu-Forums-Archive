---
title: "Error installing upgrades"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by haleybee on 2009-09-07
The following error appears whenever I try to install upgrades. Please help!

We failed to fetch: 
[http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.59.26_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.59.26_i386.deb) 
404 not found 
[IP:91.189.88.40 80] 

We failed to fetch: 
[http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.59.26_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.59.26_all.deb) 
404 not found 
[IP:91.189.88.40 80]

---

### Post by oldos2er on 2009-09-07
Which version of Ubuntu are you running?

---

### Post by haleybee on 2009-09-07
Many thanks for your reply.
It's 7.10. I guess this is the one that's not supported any more.
So - Is it possible to upgrade or must I download a new version?

---

### Post by oldos2er on 2009-09-07
That's correct, 7.10 reached its end-of-life last April. You could try this: [http://old-releases.ubuntu.com/releases/gutsy/](http://old-releases.ubuntu.com/releases/gutsy/)

 I'm not sure if you can run an upgrade on a release that's no longer supported. I suppose you could try running **update-manager -d** in a terminal. Back up any sensitive data first.

---

