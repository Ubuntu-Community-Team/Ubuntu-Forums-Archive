---
title: "Will Wubi one day support hibernation?"
date: 2008-09-28
forum: General Help
---

### Post by riahc3 on 2008-09-28
Will Wubi one day support hibernation?

---

### Post by ago on 2008-09-29
you can have hibernation by creating a dedicated swap partition or by changing the suspend mechanism. uswsusp might work for instance

---

### Post by riahc3 on 2008-09-29
> **ago said:**
> you can have hibernation by creating a dedicated swap partition or by changing the suspend mechanism. uswsusp might work for instance
Remember that Wubi does NOT support hibernation. I think a workaround like this would have already been posted....


Nonetheless, please post the steps. Thanks.

---

### Post by ago on 2008-09-29
> **riahc3 said:**
> Remember that Wubi does NOT support hibernation. I think a workaround like this would have already been posted....


Nonetheless, please post the steps. Thanks.

It's not really wubi per se' that does not support hibernation, it is the current hibernation mechanism that does not support resuming off a swap file. So either you put swap in its own partition or you change the hibernation "engine".

Wubi will support hibernation as soon as the the suspend (to disk) mechanism shipped with Ubuntu will support swap files.

---

### Post by masterwillems on 2008-09-30
I find this very strange because i can use hibernation on my laptop with Ubuntu 8.0.4 Hardy and have no problems with it.
It only boots up slow when getting out of hibernation but that isnt a real problem.

---

### Post by ago on 2008-09-30
> **masterwillems said:**
> I find this very strange because i can use hibernation on my laptop with Ubuntu 8.0.4 Hardy and have no problems with it.
It only boots up slow when getting out of hibernation but that isnt a real problem.

I assume that you have a full installation on your laptop, i.e. swap is a partition. In wubi swap is file in ntfs. And that is not supported by suspend to disk. But it is not wubi specific. You can have a swap file instead of a swap partition also in standard Ubuntu, but if you did, you would also have issues with hibernation.

---

