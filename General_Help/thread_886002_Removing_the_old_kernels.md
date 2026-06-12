---
title: "Removing the old kernels"
date: 2008-08-10
forum: General Help
---

### Post by dethredic on 2008-08-10
How can I remove the old kernels?

---

### Post by Shazaam on 2008-08-10
You can use Synaptic to remove them. Or you can edit menu.lst manually and comment out the offending kernel entries. Or you can install StartupManager (in the repos) and use it to modify grub.
As an aside, I always keep at least one older working kernel showing in grub as a backup in case an update/upgrade goes wonky.

---

### Post by exploder on 2008-08-10
Remove old kernels with Synaptic. Be sure to remove the old linux-ubuntu-modules first, if you do not then you will have to find them and manually delete them, so keep this in mind.

I always get rid of old kernels once I know that the new one is working fine.

---

### Post by dethredic on 2008-08-10
Ok, and If I made a bad kernel, can that be removed via synaptic as well?

---

