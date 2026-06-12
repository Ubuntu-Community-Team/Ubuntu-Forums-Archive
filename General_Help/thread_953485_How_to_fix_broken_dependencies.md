---
title: "How to fix broken dependencies?"
date: 2008-10-20
forum: General Help
---

### Post by Anarchid on 2008-10-20
So, here's a question: I've managed to thrash my dependency tree by installing a newer version of libc6. Now, the system refuses to install any new packages until it's fixed, and synaptic offers to "fix" it by uninstalling six broken packages. And everything else that depends on those: that means *everything else*. How do i fix myself without levelling and reinstalling, counting that i have no internet access? Will upgrading to Intrepid via alternate cd do the thing?

---

### Post by redzheb on 2008-10-20
try this:

sudo apt-get -f install

---

### Post by oldos2er on 2008-10-20
> **redzheb said:**
> try this:

sudo apt-get -f install

 Won't work without internet access.

 To the OP: Trying to fix dependency issues on a stand-alone machine is a nightmare. If there's anyway possible to get net access on this machine, you should try doing that first.

---

