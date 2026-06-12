---
title: "Total crash at splash screen"
date: 2011-07-10
forum: Hardware
---

### Post by Buntolo on 2011-07-10
OS: Ubuntu Maverick, fully updated
mobo: GIGABYTE P43 ES3G
HD: WD WD3200AVJS-63WDA0

The crash happens at splash screen, it involves the whole pc, as nothing works anymore, like caps and scroll lock (lights don't turn on when pressed).
So the crash hit the motherboard.
It's not an hardware problem, as other OS's work fine.

Ubuntu is fully updated.
As I have an Ati 5770 I've tought it was its (or its driver) fault, but it doesn't change anything with another video card, I've updated its driver and I see they work, as splash screen became 1280x1024 (from vesa's 1024x768) and the animation works.

If I remove splash screen from grub, it crash too.
If I log as root with single user mode from grub and then I start X, all works.

So what, now?
Which log I should look?

dmesg is empty, it's full only after I've rebooted as root, so there are 2 answers:
1) the normal user can't write /var/log, only root can (this explains why it's empty after a boot&crrash as normal user)
2) it crash before writing dmesg

---

