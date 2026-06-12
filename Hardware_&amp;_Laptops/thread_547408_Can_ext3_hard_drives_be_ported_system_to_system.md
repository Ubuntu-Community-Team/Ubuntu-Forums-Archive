---
title: "Can ext3 hard drives be ported system to system?"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by msonders on 2007-09-10
Under Ubuntu 7.04, I have an external hard drive I've formatted with ext3. WIth some hacks in these forums, it mounts now, and I can write to it.

The permissions - the owner - is me - msonders. But when/if I reinstall Ubuntu or try another distro, does that mean that the files on the hard drive will not be accessible or writable to me? Is my user profile tied in a way that would prevent me from using the hard drive on another install?

Example: Let's say I install...Debian or PCLinuxOS. If I plug in the hard drive, will I have access to it? *Can* I get access to it? Or will it look for the same msonders that created it? What if the user name is different?

Thanks so much! I appreciate the help!!!

---

### Post by kidders on 2007-09-11
Hi there & welcome,

> **msonders said:**
> Under Ubuntu 7.04, I have an external hard drive I've formatted with ext3. WIth some hacks in these forums, it mounts now, and I can write to it.That's odd. No hacks should be necessary. :confused:

Without knowing more about what "hacks" involves, it's hard to be 100% sure, but in general...

Ext3 filesystems (and almost all others) store UIDs & GIDs, not user or group names, so with the exception of certain conventions (eg UID 0 = "root"), file ownerships only make sense in the context of the operating system that set them in the first place. So, for example, if you were to take a filesystem from a Mac and plug it into a Linux box, you would expect to have to re-map all file ownerships to accounts that exist on the Linux box.

For example...```
$ id -u
1013
```If I create a file on any filesystem on my box, it will be marked as being owned by "1013". On your box, however, there is no way to know who user 1013 might be (or whether he even exists), so if I plug my hard disk into it, none of my file ownerships will mean anything. Of course, you would simply overwrite them all with something sensible.

---

### Post by perce on 2007-09-12
If you install several Linux distributions on the same computer, you should check that you have the same user ID on all of them. If you do, there is no problem. If you don't, you can always move the files as root, doable but annoying.

---

