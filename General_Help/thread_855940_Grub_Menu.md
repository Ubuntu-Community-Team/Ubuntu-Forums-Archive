---
title: "Grub Menu"
date: 2008-07-11
forum: General Help
---

### Post by The Doell on 2008-07-11
Just a random question...Does anyone know why the grub menu leaves the old versions of Ubuntu in menu.lst?

---

### Post by iaculallad on 2008-07-11
> **The Doell said:**
> Just a random question...Does anyone know why the grub menu leaves the old versions of Ubuntu in menu.lst?

To give the user an option of booting to old kernel when something goes wrong with the system when using the new kernel version update.

---

### Post by Victormd on 2008-07-11
Because when you update the kernel, it does not remove the previous kernels, therefore you can boot to any existing kernel, and grub picks up on that and displays all available versions.

---

### Post by The Doell on 2008-07-11
Ahhh well that all makes sense...I should have thought about that.  Thanks :)

---

### Post by mcduck on 2008-07-11
You can just uninstall the old kernels with Synaptic, and their menu entries will be automatically removed fro Grub.

It's usually a smart idea to keep the old kernel for a while after kernel update until you have confirmed that the new kernel works fine for you.

---

