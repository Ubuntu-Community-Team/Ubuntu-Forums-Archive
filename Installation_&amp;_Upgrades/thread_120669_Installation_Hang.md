---
title: "Installation Hang?"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by tom56012 on 2006-01-23
Hi

When I boot the breezy badger 5.10 cd it says press enter to boot but it loads to packages and then jus crashes with a flashing cursor in the top right. I have tried most of the boot options, but with no difference.

I have also tried a previous edition of Ubuntu and that is the same.

I have Suse 9.2 installed at the moment but want to overwrite that.

Thanks for any help

---

### Post by Luke771 on 2006-01-23
Maybe the problem is tryng to install without deleting the previous install:
Try backing up your data, delete the OS partition and install in the free space.

Or maybe you have a bad hard drive
Boot from a Linux Live CD (or from your current Linux install if that still works) and run
```

grep hd /var/log/messages

```

if you get lots of errors, you have a bad hdd and need to replace it.
If you dont get any errors, then I dont'know, should be sopmething else

---

