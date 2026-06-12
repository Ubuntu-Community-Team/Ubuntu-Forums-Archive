---
title: "Deleting xorg.conf"
date: 2008-10-09
forum: General Help
---

### Post by jerlinux on 2008-10-09
I have generated several backup copies of xorg.conf while attempting to figure out a resolution problem.  How can I delete these files?

Thanks

---

### Post by WWSmith36 on 2008-10-09
You can open root nautilus by hitting ALT+F2 and typing gksudo nautilus.

Be careful with this because you will be logged into nautilus with root privileges, and will have the ability to delete anyfile.

You can now go to /etc/X11 folder, and CAREFULLY select the reduntant xorg files.  I suggest you also keep one backup of your current xorg.conf

---

### Post by jerlinux on 2008-10-10
Thanks

I will delete the extra files.  And, when I am ready to be stepped on again, I will try to put the hard drive back into the box with nvidia.  This will likely generate some more bad words and extra xorgs.

---

