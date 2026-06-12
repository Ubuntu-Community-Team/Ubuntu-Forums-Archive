---
title: "[SOLVED] what is this? and why is there 2 ubuntus?"
date: 2008-11-04
forum: General Help
---

### Post by reinaldistic on 2008-11-04
im the only one who uses ubuntu on this computer, and i only installed 1 ubuntu: 8.10
but when grub loads up it gives me 5 ubuntu choices:
ubuntu 8.10 2.6.27-7 generic
ubuntu 8.10 2.6.27-7 generic (recovery mode)
ubuntu 8.10 2.6.24-19 generic
ubuntu 8.10 2.6.24-19 generic (recovery mode)
ubuntu 8.10 memtest86+

i know the recovery mode is the (safe mode) version of ubuntu of each of those 2 and i also know what the memtest is, but why is there two diferent normal ubuntus there?: 2.6.27-7 and 2.6.24-19???
should i be worried? they are not taking a diferent partition, so what is it?

---

### Post by ad_267 on 2008-11-04
Those are previous versions of the Linux kernel. They are kept there so that you can still boot into Ubuntu if you can't boot into a new kernel or have other issues.

You can remove them by searching in synaptic for linux-headers and linux-image and removing the older versions.

---

### Post by reinaldistic on 2008-11-04
ooh a failsafe? nice ok, just needed to know i wont remove it

---

### Post by ad_267 on 2008-11-04
Yeah, I usually start removing some of mine if I get three or four different kernels. Usually just one extra is enough :). Also I should have said linux-image, not linux-kernel in my fist post, I've changed it now.

---

