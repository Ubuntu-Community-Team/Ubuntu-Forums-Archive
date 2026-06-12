---
title: "migrating to Linux Mint?"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by Cam42 on 2009-07-27
How hard would it be to change my system over to Linux mint? I need to keep all my documents... How would I do this?
EDIT: the reason being, is that I'm having issues with nonfree plugins, ie: Flash. Mint has these plugins by default, right?

---

### Post by eekie on 2009-07-27
If you don't have a separate data partition you better create one and transfer all your data to this partition. 
You have to install gparted the ubuntu partition manager first, than resize your main partition (make it smaller) and create a new ext3 partition with mount point /home. Then you can copy/paste al your data and happily install Mint over your old ubuntu

---

