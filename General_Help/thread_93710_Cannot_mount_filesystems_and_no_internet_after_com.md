---
title: "Cannot mount filesystems and no internet after compiling kernel"
date: 2005-11-22
forum: General Help
---

### Post by Dinchamion on 2005-11-22
Hello everyone,

I have a problem. I just installed Breezy, and I decided to compile a custom kernel for myself. It went good, I used the working (!) .config from my older distros (for the same computer), just tweaked it a bit.

It compiles flawlessly, and could install it with no problem. The problem is, that when I reboot into the new kernel, I'm not able to mount up my Windows partitions (which were automatically mounted by default), and I can't connect to the internet.

I checked my settings twice, and recompiled the kernel like about 4 times now, but I'm not a Linux-expert, and now I have no idea what went wrong.

Any ideas?

---

### Post by ranf on 2005-11-22
[QUOTE=Dinchamion]
I have a problem. I just installed Breezy, and I decided to compile a custom kernel for myself. It went good, I used the working (!) .config from my older distros (for the same computer), just tweaked it a bit.
[/QUOTE]
As a config to start with use the Ubuntu one. It is in /boot/config-`uname -r`.

---

