---
title: "removing old kernels"
date: 2005-11-23
forum: General Help
---

### Post by termite on 2005-11-23
I installed the updates today as I was told by update manager.  It upgraded the kernel from 2.6.12-9-k7 to 2.6.12-10-k7, but left the former in the GRUB menu, so it is presumebly still installed.  How do I get rid of it?

Thanks

---

### Post by Pablo_Escobar on 2005-11-23
You can uninstall it via synaptic - look for "linux-image"
But it's safe to keep 2 kernels at bay in case one of them has some malfunction :)

---

### Post by termite on 2005-11-23
I currently have four kernels, 2.6.12-10-k7, 2.6.12-10-386, 2.6.12-9-k7, and 2.6.12-9-386.  The two 10's are newly installed, the 9-k7 I installed a couple of days ago to replace the 9-386 and it seems to be running fine.  What's your advice regarding keeping/uninstalling some of these?

---

### Post by Pablo_Escobar on 2005-11-23
Heh, I'd decide between k7 and 386 (in favour of k7 as it seems You're running an AMD machine) and remove both of 386 ones (only if k7 works without a hitch) thus keeping both versions of k7 kernel.

---

