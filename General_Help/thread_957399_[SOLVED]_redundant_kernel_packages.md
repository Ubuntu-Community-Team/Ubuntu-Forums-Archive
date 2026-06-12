---
title: "[SOLVED] redundant kernel packages?"
date: 2008-10-24
forum: General Help
---

### Post by EvilBro on 2008-10-24
Today I was uninstalling some unwanted packages with synaptic package manager. While I was doing that, I noticed I have the following packages:

linux-headers-2.6.24-18
linux-headers-2.6.24-19
linux-headers-2.6.24-21

linux-image-2.6.24-16-generic
linux-image-2.6.24-18-generic
linux-image-2.6.24-19-generic
linux-image-2.6.24-21-generic

As far as I know, I only use the latest of the versions listed (2.6.24-21). Can I safely remove the other packages or are they used in some way?

---

### Post by 505 on 2008-10-24
You can remove those packages if you want to. Although it is adviced to keep the current kernel + one older kernel that you know for sure. In case a kernel update screws things up, you can still boot the older kernel.

---

### Post by Rocket2DMn on 2008-10-24
I think you should keep at least 3 kernels around that you know work.  If you want to get rid of one of the older kernels, mark the appropriate linux-image for complete removal.

---

### Post by Arabiest on 2008-10-24
Thanks gents for the advise...

---

### Post by EvilBro on 2008-10-24
With recovery in mind, is it wise to leave at least one startup option with an older kernel in menu.lst?

---

### Post by Rocket2DMn on 2008-10-24
Yes the existing kernels on your system should be in menu.lst and thus available from the GRUB menu.  When you remove older kernels, they should be automatically removed from menu.lst.

---

### Post by EvilBro on 2008-10-24
> **Rocket2DMn said:**
> When you remove older kernels, they should be automatically removed from menu.lst.
After some bad experiences with this feature, I don't allow this to happen automatically. I'll update my menu.lst manually.

---

