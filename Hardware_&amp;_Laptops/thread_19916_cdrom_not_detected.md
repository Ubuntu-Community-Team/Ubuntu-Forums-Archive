---
title: "cdrom not detected"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by tiiim on 2005-03-14
hey guys

everytime i run ay linux distro on my comp the installation always says no cdrom found!

On some linux distro it works on the second cd rom drive (cos i have too) but then it cant get to the disk partition cos' of windows. I  know newer distro have a ntfs paritioner but these are the ones where the cd dont work. Why earlier ones work but then the paritioner wants to format the whole hard drive.

Any ideas?

---

### Post by lorap on 2005-03-14
hi friend!
i'd the same problem with my usb cdrom.
donno if it's good in your case but that's what i've done to solve this difficulty:
create new directory say "/media/cdrom1"
after what go to the "/mount/fstab" & add this line:"/dev/hcd1(or 2 depending on the first cdrom device number) /mount/cdrom1 udf,iso9660.noauto,user,ro,0 0"
but look as your first cdrom drive's line's defined to be more sure.
tha's all :-)
hope it'd help you friend.
have a good luck!
pavel

---

### Post by tiiim on 2005-03-14
[QUOTE=lorap]hi friend!
i'd the same problem with my usb cdrom.
donno if it's good in your case but that's what i've done to solve this difficulty:
create new directory say "/media/cdrom1"
after what go to the "/mount/fstab" & add this line:"/dev/hcd1(or 2 depending on the first cdrom device number) /mount/cdrom1 udf,iso9660.noauto,user,ro,0 0"
but look as your first cdrom drive's line's defined to be more sure.
tha's all :-)
hope it'd help you friend.
have a good luck!
pavel[/QUOTE]

thanks the only prob is i cant actually install linux to do that :O it fails at the installation..... anybody else?

---

