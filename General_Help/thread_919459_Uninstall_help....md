---
title: "Uninstall help..."
date: 2008-09-14
forum: General Help
---

### Post by HafDoc on 2008-09-14
How do I uninstall Ubuntu 7.10 from my laptop?  I want to remove the partition and restore my computer to just Windows XP.

---

### Post by cyclobs on 2008-09-14
reinstall windows

---

### Post by lisati on 2008-09-14
1 Do you have a Windows disk or a recovery partition on your computer?

2 Are you running a dual-boot system?

---

### Post by cdtech on 2008-09-14
Do you have windows installed now? (using dual boot perhaps)

If so, you could use the Live CD to reformat the Ubuntu to a fat file system so windows will see the unused space. Then you'll need the windows install disk to repair the MBR.

---

### Post by HafDoc on 2008-09-14
I have the Windows CD that came with my laptop.  Windows XP is installed on my laptop also.  Yeah, I have the option of starting through Windows XP or Ubuntu when I turn my laptop on.  How do I remove the Ubuntu partition and how do I fix the MBR?

---

### Post by cdtech on 2008-09-14
Boot using your Live CD. When you get to the desktop open "gparted" (System > Administrator > Partition editor). Once you have it opened just select the partition Ubuntu is installed on and select "format as".

---

