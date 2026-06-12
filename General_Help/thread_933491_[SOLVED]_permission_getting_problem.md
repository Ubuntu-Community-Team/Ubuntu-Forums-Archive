---
title: "[SOLVED] permission getting problem"
date: 2008-09-29
forum: General Help
---

### Post by suhaib1thariq on 2008-09-29
i am using vmware in ubuntu .i connected a network drivve in that using samba...i copied a oracle software in my network folder in linux...and i opened a folder in virtual windows in vmware... when i opened the folder and open the folder it says you don't have permisson to open
i set
    'chmod 755 foldername'
          and the folder is open now
and then inside it many folders...it is not also opening...it says no permissions...
how to get permission for all documents and folders inside a folder

---

### Post by tCarls on 2008-09-29
Try "chmod -R 755 foldername" to change permission of the directory and everything inside it.

---

