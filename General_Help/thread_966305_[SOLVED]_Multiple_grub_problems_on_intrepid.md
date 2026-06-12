---
title: "[SOLVED] Multiple grub problems on intrepid"
date: 2008-11-01
forum: General Help
---

### Post by Zalbor on 2008-11-01
Hello, I just "upgraded" Hardy to Intrepid (actually I reinstalled, preserving my home partition) and I have some grub issues...

As always after installing a new version of Ubuntu, I changed the menu.lst file to use some preferences:
1)Added an md5 encrypted password
2)Removed the "quiet" instruction from the kernels, keeping the "splash" instruction there.
3)Added a splashimage (the same one I used in previous versions).

Now the following problems appeared:
1)When in the grub menu I press 'p' to enter my password, the prompt already has 3 asterisks! And no matter what I do, my password (which I've re-entered in menu.lst to be sure) doesn't work. It won't work if I delete the 3 asterisks and enter my password from the beginning, it won't work if I assume that the 3 asterisks are the first 3 letters of my password and enter the rest, and it won't work if I type my password in addition to the 3 characters already there.

2)When booting the kernel, one of the following things might happen:
a)It will boot as if I've removed the "splash" option as well, and only show text output (the most common)
b)It will try to boot but will produce an error (so far either my computer has started beeping or strange lines appear on the screen)
c)It will boot with the normal usplash and the text output below it (like it's supposed to).
In any case, when shutting down (or rebooting) the usplash and the text appear normally.

3)There is no error concerning the splashimage I added, but the image doesn't appear behind the menu. The menu is simply in text mode, like no splashimage is there. The way I added the image is to cp splash.xpm.gz to /boot/grub and then ran "sudo update-grub", so the line was added automatically. (Similarly, I removed the "quiet" option by editing the commented lines and letting update-grub change the kernels).

Does anyone else have these issues? Any idea on how to fix them?

---

### Post by Zalbor on 2008-11-02
Sorry for the bump...

---

### Post by Zalbor on 2008-11-06
Does anyone know anything about that?
There was a kernel update today but none of that was fixed.

---

### Post by Zalbor on 2008-11-16
The password issue was because of the splashimage line, which apparently doesn't work in 8.10. I'm marking this as solved and making a new thread about the rest, which I now know aren't grub-related.

---

