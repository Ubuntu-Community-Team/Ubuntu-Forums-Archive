---
title: "linux kernel update..."
date: 2005-11-28
forum: General Help
---

### Post by Elrohir on 2005-11-28
did an update of the kernel (2.6.10-5-386 to 2.6.10-6-386) and now on the boot menu appears both kernels... and when trying to boot to the latest, KERNEL PANIC!! it says:

```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)
``` 
any one had this error?? what to do??

---

### Post by Weta on 2005-11-29
Hello

I did the same update, using the Smart Upgrade tool, and now my internal modem does not work.  I hope you don't mind adding this problem to your update thread.

The modem uses a Linuxant software driver (the purchased version, not the free one).  The update upgraded linux-386, linux-image-modules-386 and linux-restricted-modules-386.  It also installed linux-image-2.6.10-6-386 and linux-restricted-modules-2.6.10-6-386.

I now get FATAL errors that the following six modules are not found: hsfpcibasic2, hsfmc97ich, hsfmc97via, hsfmc97ali, hsfmc97ati, and hsfmc97sis.  There are however folders for all of these in /etc/hsfmodem/nvm

Can some one please tell me how to get the modem working again.  Do I have to "restart" it after the kernal is upgraded?  Thank you.


Weta

---

