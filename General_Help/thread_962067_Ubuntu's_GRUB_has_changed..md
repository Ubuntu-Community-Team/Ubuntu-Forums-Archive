---
title: "Ubuntu's GRUB has changed."
date: 2008-10-28
forum: General Help
---

### Post by grullon on 2008-10-28
Hi.
My problem is that the grub in ubuntu which at starting showed something like this

Ubuntu, kernel.....
Ubuntu, kernel ....(recovery mode)
...
Windows XP

Now shows something like this

Debian, kernel ....
Debian, kernel ....
...
Windows XP

My question is: Is it just a name change or something else happened?

People often say that modifying menu.lst we can change the names to be show for kernels in the grub. However, I ONLY MODIFIED the lines in menu.lst following the instructions posted in one thread so that my grub looked like a suse grub. The thread is [http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)
There weren't any problem with the first theme I downloaded (message.ubugrey) so it showed the normal names for kernels. After that I tried other themes and sincerely I didn't pay attention to anything else but only the graphical themes, so I don't know if trying those themes caused the change.

---

### Post by Partyboi2 on 2008-10-29
I think changing the themes changed it. Easy way to find out is use a theme that uses Ubuntu, kernel..... and see if grub says Ubuntu, kernel..... then try one of the other themes that say  Debian, kernel .... and see what grub says.

---

### Post by Helge on 2008-10-30
Can you post the menu.lst file here?

Each line in the final boot menu (each choice) has a corresponding title line in the file. It tells explicitly how the boot menu looks. Take a look in the file yourself. /boot/grub/menu.lst.

When a new kernel package is installed, corresponding lines are "automagically" added to the menu.lst file. Have you added a kernel from a package you compiled yourself from source? Have you added a kernel from the Debian repository, rather than from Ubuntu? Old kernels are not necessarily removed when newer are added, which means that the boot menu grows. In that case, you should have both Ubuntu and Debian items. Is that the case? Or has the word Ubuntu simply been replaced by Debian? The part of the title line that you have omitted is the kernel version. I would assume it has changed, which means that more than the name has changed.

---

