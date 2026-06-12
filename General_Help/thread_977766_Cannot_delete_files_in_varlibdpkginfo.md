---
title: "Cannot delete files in /var/lib/dpkg/info"
date: 2008-11-10
forum: General Help
---

### Post by daiwai on 2008-11-10
Today, I booted a Kubuntu Feisty installation on an old computer for the first time since many months. Now there are some packages that can't be upgraded. An "operation not permitted" error is returned from dpkg when it tries to unpack and install the archive.

I think the cause of this is, that in the /var/lib/dpkg/info directory there are some files, that cannot be modified or deleted, even as su/root. ls -l for those files shows something like:

?--------- 18014 root 25563 0 1970-01-01 10:13 adept-common.postrm

All attempts to change the owner/group, move or delete the file result in operation not permitted errors.

Any ideas how to solve this? :confused:

---

### Post by phillik747 on 2008-11-10
No luck as root hummmm....

Have you tried it in recovery mode?

---

### Post by daiwai on 2008-11-11
> **phillik747 said:**
> No luck as root hummmm....

Have you tried it in recovery mode?

Yes, same results. :(

---

### Post by -Zeus- on 2008-11-11
wow, that's impressive.  have you tried running running sudo chmod 700 /var/lib/dpkg/info/* ?

---

### Post by daiwai on 2008-11-15
Yes, tried that. It always gives "operation not permitted".

---

