---
title: "Grub 17 Error!"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by denis1982 on 2007-05-04
]Hi
I installed ubuntu linux on my acer travelmate 2400 series laptop. It was a dual boot system with XP pro. When I tried to log in to ubuntu however, my password was not recognised. So I logged on to XP and formatted the hard disks with ubuntu on them. Now when I try to reboot my pc, I get a grub eror 17.
Also before, I used to get a screen saying " press F2 to get to setup" but now I don't get it.
Could anyone help??

Denis

---

### Post by yerke on 2007-05-04
I had that problem when merging two partitions on Windows. After a successful format I rebooted and got the message GRUB ERROR 17..

So I have just come up with this problem guiding from the following link
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

Udachi!

---

### Post by psusi on 2007-05-04
You blew away linux and grub, but grub's MBR is still on the disk.  You will need to put windows' one back in place by booting from a windows cd, getting into the recovery console, and issuing a FIXMBR command.

---

