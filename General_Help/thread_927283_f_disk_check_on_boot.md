---
title: "f disk check on boot"
date: 2008-09-22
forum: General Help
---

### Post by enchesss on 2008-09-22
When i boot, the f disk shows an error and locks up. can reboot by cntrl + D and then skip fdisk check by pressing esc and everything ok. How can i fix this so boot works?

---

### Post by Pro-reason on 2008-09-22
> **enchesss said:**
> When i boot, the f disk shows an error and locks up. can reboot by cntrl + D and then skip fdisk check by pressing esc and everything ok. How can i fix this so boot works?

I would boot from a live CD and do a full fsck (filesystem check) of all drives.

---

### Post by enchesss on 2008-09-23
that sounds like fun but is there a way to do a system check after booting up? (having pressed escape to be able to log in)

Also - what will the system check do? is it likely to fix the problem without much use input because i have been unable to find any instructions about this on the forums

also do you have any further advice as to why this happened and what to do to stop it happening?

---

### Post by cariboo on 2008-09-23
You can't run fsck on a mounted drive, unless you plan on reinstalling after it is done. Do as the previous poster suggested and use the live cd to run fsck. The system check should repair any minor problems with your hard drive. To find out more about fsck in a terminal type:

```
man fsck
```

Jim

---

### Post by enchesss on 2008-09-25
Good news:
After attempting many different uses of the live cd to no avail - I simply ran fsck after the command line appeared during boot and then several options to fix weree given and it was fixed.

Bad news:
during this fiasco i decided to reinstall windows and this has stuffed the grub loader.

See new post

---

