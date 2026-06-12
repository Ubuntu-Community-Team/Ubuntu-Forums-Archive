---
title: "Grub Error 2"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by qscomputing on 2007-06-04
Hi,

I am helping a friend install Feisty on his laptop, which is a Sony Vaio VGN-AR190G.

Installation went smoothly, but at first boot Grub stage 1.5 gave an error 2. Some googling turned up two possibile explanations for error 2:

([http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html) says it means "Selected disk doesn't exist"
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html) says it means "Bad file or directory type"

I know that there is something unspecified which is strange/exotic about the harddisk in this machine, as some other distros couldn't even detect it when booting their installers.

Right now, my plan of action is to try as many different distros as possible and hope I find one that works. In the meantime, I would like some suggestions of other things I can try - one error code is hardly going to be enough to diagnose the problem completely, but if there is anything else I ought post, please let me know.

Thanks,
  QS.

---

### Post by uteck on 2007-06-04
Press esc to make grub show the menu.  From there, select the first boot option and press 'e' for edit mode.  Try changing the grub root device (0,1) to (1,1), or if it is a 1, change it to a 0.  Then press return and then 'b' to boot it with your changes.  You might have to make changes to the kernel line also, but only 1 change at a time. 
Once you get if booted, you have to edit /boot/grub/menu.list at the system defaults area, and for each item.

---

### Post by qscomputing on 2007-06-04
I would try that, but I get an error code before the Grub menu is displayed. Is the bootloader on the Live CD grub as well - will the same procedure work from there?

---

