---
title: "[SOLVED] system doesnt remove kernels automaticly."
date: 2008-08-12
forum: General Help
---

### Post by The Squig on 2008-08-12
Im runnig ubuntu 8.04 with all updates.

The problem im having is that ubuntu doesnt remove the old kernels after updating. At time ive had 4 different kernel versions listed in grub.

When this happens I remove the old kernels and run the update-grub command. Is there a way for ubuntu to do this automaticly?  I can see the need to maybe keep the last working one but seriously, saving all of them?

---

### Post by snowpine on 2008-08-12
> **The Squig said:**
> IM runnig ubuntu 8.04 with all updates.

THe problem im having is that ubuntu doesnt remove the old kernels after updating. At time ive had 4 different kernel versions listed in grub.

Ive removed them manually but is there a way for ubuntu to do this automaticly?  I can see the need to maybe keep the last working one but seriously, saving all of them?

There is no reason not to keep them, really. They take up very little space on your drive, and being able to boot into an older kernel is occasionally useful when troubleshooting.

That being said, you can remove them using Synaptic, and you can also change which kernels are displayed in Grub by editing your /boot/grub/menu.lst file. For example, you can change the behavior so that only the most recent (or most recent 2) is displayed.

---

### Post by The Squig on 2008-08-12
> For example, you can change the behavior so that only the most recent (or most recent 2) is displayed. 

hmm well this seems to be what im after since whats really bothering me is grub clogging up. ty.

---

### Post by ggaaron on 2008-08-12
Several hundreds of MB is not very little space for some...

Easy way is to search for linux version in synaptic - like 2.6.24-4 - or something and purge all installed packages, grub entries will be auto-removed.

---

### Post by alzie on 2008-08-12
Install "StartUp-Manager from the repositories.  It will let you set the number of kernels to keep.  I have it set at 2.

I hope this helps

---

### Post by The Squig on 2008-08-12
installed startup manager. Looks good, well see if it works when I reboot later. Ty to all replies.

---

