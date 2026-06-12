---
title: "Kernel Upgrading"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by Landus on 2005-12-29
I recently read an article that explains how to upgrade your kernel using kernel.org

My only problem is that I went to check to see what modules I had compiled, /usr/src/linux doesn't exist, and there isn't anything in the /usr/src folder.


So, how am I supposed to run 'make menuconfig'?

---

### Post by gruepig on 2005-12-30
First of all, why do you want to upgrade your kernel?  If it's just to make sure you are getting a version without any security holes, keeping your packages up to date will do this for you.

If you want to compile your own kernel because you want different config options or just to learn, then go for it.

You can download kernel source from ubuntu (look for packages named kernel-source-<version>) or from ftp.kernel.org.

I assume (haven't tried), that Ubuntu supports Debian-style kernel packages, so after 'make menuconfig', you should be able to use 'make-kpkg kernel_image', etc, and install the kernel package using 'dpkg -i'.

Ask if you need more specific instructions.

---

### Post by Landus on 2005-12-30
I'd be using something from kernel.org, but my current problem is that there isn't a symlink pointing to the current kernel I'm running.

---

### Post by gruepig on 2005-12-30
I'm not sure I understand what you are trying to do.  Can you explain in more detail what you are trying to accomplish and what you have done so far?  Are you trying to compile a kernel (and modules) or just modules?  Where do you have your source, if it isn't in /usr/src?  What are you expecting to symlink to your current kernel?

---

