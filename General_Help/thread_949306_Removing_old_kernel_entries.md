---
title: "Removing old kernel entries"
date: 2008-10-16
forum: General Help
---

### Post by parampreet on 2008-10-16
I recently upgraded the kernel to 2.6.24-21 through the Update Manager. After the upgrade a entry for the new kernel was added to /boot/grub/menu.1st. I checked in /boot and noticed that there were files with prefixes "System.map", "initrd.img" and "vmlinuz" bearing versions all the way from 2.6.24-16 to 2.6.24-21. 

Apart from the latest version (2.6.24-21), can I safely delete the older files to free up disk space ?

---

### Post by sparky-steve on 2008-10-16
Is this what you're after?

[http://www.cyberciti.biz/faq/proper-way-to-remove-old-linux-kernels/](http://www.cyberciti.biz/faq/proper-way-to-remove-old-linux-kernels/)

[http://ubuntuforums.org/showthread.php?t=22812](http://ubuntuforums.org/showthread.php?t=22812)

Hope it helps.

SS

---

### Post by iaculallad on 2008-10-16
You can use Synaptics Package Manager to safely delete those files. You only have to search for the 'linux-image' string (w/o quote) and mark the kernels you want remove for "Complete Removal". Click on the Apply option when you're done selecting what kernels you want to remove. This will automatically update your /boot/grub/menu.lst file for you.

Note: It's better if you leave an older kernel for a backup just in case.

---

### Post by fooman on 2008-10-16
apart from those methods...you can use synaptic to remove the old kernels.  once i am sure that the latest is stable,  i usually keep that and the one previous to it....then delete the rest.

---

