---
title: "[SOLVED] Deleting certain files in a protected folder w/o removing all files"
date: 2008-10-27
forum: General Help
---

### Post by eatdirt001 on 2008-10-27
I installed a bunch of GIMP brushes in the pathway '/usr/share/gimp/2.0/brushes'. The problem is that there are a certain set of brushes with a common name that I want to remove but I can't just drag the file to the trash because it won't let me. I know I can do something like 'sudo rm file.gbr', but there are just too many files to delete them individually. The files are name such as "file1.gbr, file2.gbr, etc" so is it possible to delete files with a certain name all at once?

---

### Post by ad_267 on 2008-10-28
You can press Alt+F2 and run "gksu nautilus" to get a file browser with root permissions and then just select all the files.

Or from the terminal you can use:
```
cd /usr/share/gimp/2.0/brushes/
sudo rm file*.gbr
```

The * matches any characters repeated any number of times (including 0)

---

