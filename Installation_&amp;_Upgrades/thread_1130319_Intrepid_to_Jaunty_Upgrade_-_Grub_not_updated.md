---
title: "Intrepid to Jaunty Upgrade - Grub not updated"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by ittiam on 2009-04-19
I did an upgrade to stable release of jaunty but still the grub does not get updated. Neither did the new kernel show up nor the ubuntu version got updated. I had to manually edit the /boot/grub/menu.lst file and then it worked. Is this a known issue with the stable release?

EDIT: Before posting I did google but the same problem was reported occurring only with the alpha release.

---

### Post by ittiam on 2009-04-26
Is this anyway related to grub or grub2? I do not use grub2, so is that the problem?

---

### Post by jkonrad on 2009-05-21
I had this problem too, except I am not sure how to update my menu.lst manually. How do I know all the kernel numbers and file locations?

thanks

---

### Post by logos34 on 2009-05-21
if you've downloaded and installed the kernels, and they're sitting in /boot, run

> sudo update-grub

this will automatically scan /boot and add menu.lst entries for all the vmlinuz and initrd.img kernel images

---

### Post by jkonrad on 2009-05-21
Thank you. I found another post that was similar. I needed to first rm the existing menu.lst file. Then the update worked. Now I am using the correct kernel and the menu is correct. Thank you.

---

### Post by logos34 on 2009-05-21
> **jkonrad said:**
> Thank you.

cool.  enjoy

---

