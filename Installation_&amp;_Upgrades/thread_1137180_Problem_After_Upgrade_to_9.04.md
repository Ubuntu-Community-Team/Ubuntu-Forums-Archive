---
title: "Problem After Upgrade to 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by mitchellcipriano on 2009-04-25
I upgraded to 9.04 last night and everything appears to work except for these two issues:

Tracker says the index is corrupted and asks me if I want to reindex, but nothing I do seems to fix this. The only way to get rid of the notices is to pause all indexing

If i run update manager I get the partial upgrade notice. If I say do the partial, it identifies two packages to be removed:

libdb4.5-java
powermanagement-interface

It identifies two packages to be installed:

libdb4.6-java
libdb4.6-java-gcj

And one package to be updated:

liblucene2-java

If I tell it to do the partial, nothing appears to happen. Any ideas?

---

### Post by Kakteed on 2009-04-25
This fixed the tracker issue for me:

sudo apt-get install tracker-utils
tracker-processes -r

---

### Post by blue_bullet on 2009-04-25
Bryan McClellan posted a workaround for the tracker issue.

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560)

It worked for me.

---

### Post by blue_bullet on 2009-04-25
I also had the same issue on the partial on both my desktop and my laptop.

---

### Post by mitchellcipriano on 2009-04-25
> **Kakteed said:**
> This fixed the tracker issue for me:

sudo apt-get install tracker-utils
tracker-processes -r

Thanks, this seems to have solved my Tracker problem. I still seem to have an issue with update.

---

### Post by guruchomp2 on 2009-04-25
I had the same problem with libdb4.5-java after updating to 9.04. I fixed it by going into Synaptic Package Manager, searching for libdb4.5-java and marking it for complete removal. Synaptic then automatically selected libdb4.6-java to install/upgrade.

---

### Post by mitchellcipriano on 2009-04-25
> **guruchomp2 said:**
> I had the same problem with libdb4.5-java after updating to 9.04. I fixed it by going into Synaptic Package Manager, searching for libdb4.5-java and marking it for complete removal. Synaptic then automatically selected libdb4.6-java to install/upgrade.

Excellent solution, I wish I would have thought of myself and saved a couple hours. It worked perfectly.

Thanks.

---

