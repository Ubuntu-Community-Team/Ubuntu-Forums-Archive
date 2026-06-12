---
title: "Getting the media card readers to work with 9.10"
date: 2009-11-06
forum: Hardware
---

### Post by jlh68 on 2009-11-06
OK, I need info on how to make the patch to make the right media drive work.  I know how to do it with GRUB but not GRUB2 which is now installed with 9.10 NR.  I know GRUB2 uses a different file for startup but I can't remember what it is.  > /boot/grub/menu.lst is the OLD GRUB stqrtup file.

I need to know the new file name to add > pciehp.pciehp_force=1 to.

---

### Post by darkshadow on 2009-11-06
I added that line into /boot/grub/grub.cfg on my system. Also the line that loads the kernel was started with was renamed to "linux"

---

### Post by jlh68 on 2009-11-06
Thanks **darkshadow**
That is exactly what I was looking for. I knew that GRUB2 used a different file for startup and I had read a post on it, I just could not remember the file name.

---

