---
title: "Moving an installation from external to internal drive"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by AnthonyPapillion on 2009-10-23
I recently installed Ubuntu 9.04 on my external hard disk and have a dual boot set up between Windows (on my internal drive) and Ubuntu on my external. Because of the performance issues with external drives, I'd like to move my Ubuntu installation to my internal disk.

Is there a way to do that without disturbing the Windows installation? 

Thanks!
Anthony

---

### Post by rippin on 2009-10-23
> **AnthonyPapillion said:**
> I recently installed Ubuntu 9.04 on my external hard disk and have a dual boot set up between Windows (on my internal drive) and Ubuntu on my external. Because of the performance issues with external drives, I'd like to move my Ubuntu installation to my internal disk.

Is there a way to do that without disturbing the Windows installation? 

Thanks!
Anthony

You could use the dd command after partitioning the internal drive and execute grub-install/update. Probably easier to install Ubuntu directly on the internal and mount the external later to copy any files you need to the internal drive, tho'.

---

### Post by AnthonyPapillion on 2009-10-23
Yeah, you're right. Much less involved just to reinstall and move things over.
Thanks!

---

