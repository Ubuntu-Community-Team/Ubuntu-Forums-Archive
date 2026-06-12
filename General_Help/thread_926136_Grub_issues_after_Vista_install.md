---
title: "Grub issues after Vista install"
date: 2008-09-21
forum: General Help
---

### Post by vital101 on 2008-09-21
Hey everyone,

I've recently installed Vista on to a 2nd partition on my hard disk.  I know that the preferred way to get a dual boot setup going is Vista first, Ubuntu 2nd, but that wasn't possible in my case.

Anyways, I expected that grub would be wiped out by the Vista boot loader (and it was).  So, I consult online documentation on how to restore grub so that I might get back at by Ubuntu install.

I perform the following commands from the Ubuntu live cd:
```

grub> find /boot/grub/stage1
 (hd0,0)

grub> root(hd0,0)

Error 27: Unrecognized command


```

If the root command hadn't failed, I would have followed with setup(hd0).

My question is, why am I getting this Error 27?

Thanks,
vital101

---

### Post by fooman on 2008-09-21
try a space between root and (hd0,0):

```
grub> root (hd0,0)
```

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

