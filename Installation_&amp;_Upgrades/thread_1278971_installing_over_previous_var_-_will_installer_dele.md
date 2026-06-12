---
title: "installing over previous /var - will installer delete custom subdirs?"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by aim on 2009-09-30
I've got a /dev/md0 where I used to keep my /var

My primary hdd failed, so I, currently, reinstalling my system from scratch. 

Will the text-mode installer remove non-system files from my /var? 

I got /var/somthing directories created by hand, and removed everything else presented there previously.

Should I create a copy of my data (very huge, will take a long time, so I wish to skip this), or the installe deleting everything-everything from /var dir and I NEED to copy my data to make sure they are safe?

---

### Post by danns on 2009-09-30
The safe answer is to back up your custom data.  So long as you don't choose to format the partition /var is on during the install your data should be safe unless the modified files are files contained in packages.  Installation of the new package will overwrite the existing file.

---

### Post by Lars Noodén on 2009-10-01
If /var is in a separate partition, it is possible to have the installation keep it as it is.  However, it is still recommendable to back everything up first, in the event of error.

---

### Post by aim on 2009-10-03
> **danns said:**
> The safe answer is to back up your custom data.  So long as you don't choose to format the partition /var is on during the install your data should be safe unless the modified files are files contained in packages.  Installation of the new package will overwrite the existing file.

this is exatly that thing I want to clear-up. thanks!

---

