---
title: "Help in how to upgrade Hardy to Jaunty ??"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by pappo on 2009-06-16
I currently have Hardy 8.04 installed.  See my lsb-release:

# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"

How do I got about upgrading this to 9.04 ?

Any help would be appreciated.

pappo

---

### Post by ptn107 on 2009-06-16
Your supported upgrade path is 8.04.2 -> 8.10 -> 9.04.  So to get to jaunty you must upgrade to intrepid first.

1. Select 'System -> Administration -> Software Sources'.  Click on the 'Updates' tab.  At the bottom change Show new distribution releases to 'Normal Releases'.  Click close.

2. Now open the update manager 'System -> Administration -> Update Manager'.  Click check and install any updates that remain.  After all available updates are applied to hardy the update manager will prompt that a new distribution release '8.10' is available.  Click upgrade.

After it's complete you'll use update manager again to upgrade to 9.04.

---

### Post by pappo on 2009-06-16
> **ptn107 said:**
> Your supported upgrade path is 8.04.2 -> 8.10 -> 9.04.  So to get to jaunty you must upgrade to intrepid first.


Ok.  thanks for the reply.  I will go upgrade to 8.10 now and 9.04 later.

---

