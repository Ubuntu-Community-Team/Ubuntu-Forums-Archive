---
title: "Preventing automatic upgrade of kernel packages"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by kyllikki on 2008-12-21
I need to prevent my kernel packages from getting overridden whenever automatic updates are ran due to a patch that I applied.  I have read that you can 'lock' kernel packages in Synaptic and have attempted to do so but the kernel packages still get overridden.

How can I still retain these custom kernel packages yet be able to run automatic updates without deselecting the kernel packages each time? (Perhaps I was doing something wrong with the locking process.)

---

### Post by Sucrac on 2008-12-21
Find your kernel in synaptic, select it and go to Package>Lock Version. (Also try unchecking Automatically Installed?)

---

### Post by kyllikki on 2008-12-27
As I mentioned in my previous post, I have already tried locking.  I verified that the 'Automatically Installed' tick-box was unchecked on the locked packages.  Any ideas?

---

