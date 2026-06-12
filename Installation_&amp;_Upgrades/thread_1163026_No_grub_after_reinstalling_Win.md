---
title: "No grub after reinstalling Win"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by donmor on 2009-05-18
After I reinstalled Win on a dual boot system, can't get the grub to work so I can log in.  Just goes straight to Win. Can someone direct me to some information on rebuilding the grub or whatever I would have to do.

Thanks

Don

---

### Post by udippel on 2009-05-18
That's a well-known 'feature' of Windows: It will always overwrite the Master Boot Record (MBR) of the drive. You need to write it back. I for one always have a Supergrubdisk lying around for this purpose. But the Live-CD should be able to do the trick as well; actually any medium that has grub as boot loader, because you can go always interrupt the boot menu and type 'C' for a command line. 
Then google a bit, and find the lines that you need to type, something like 'find (hd...', 'root (hd...', and 'setup (hd...'. (What needs to be typed at the dots depends on your system. Tab-completion is supported by grub!)

---

