---
title: "Partitioning problems"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by OllieGab on 2008-12-06
After a couple of failed attempts to install Ubuntu via a magasine CD (it failed to resize/partion my hard drive) I resized my harddrive with a Windows tool to about 100G (of 160) hoping I would be able to to use the "left overs" for Ubuntu.
However, the Linux install program seems to not want to use to free part of the HD but wants to resize the "new" 100G, place Ubuntu of what is left on those 100G and leave the rest empty.
Why doesn't the install programme take the 60G I've got free on the disk and install Linux there?

---

### Post by utnubuuser on 2008-12-06
Did you try to select "Guided, -use largest continuous free space"?

---

### Post by Pumalite on 2008-12-06
Did you format that space? Ubuntu cannot be installed in 'unallocated' space. Once you format it; go 'Manual' at the partitioning stage of the installer and choose the space you want.

---

