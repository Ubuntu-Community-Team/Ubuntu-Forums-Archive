---
title: "How do I format Ubuntu's partition and reinstall it on dual boot system?"
date: 2008-08-28
forum: General Help
---

### Post by Timberwolf5578 on 2008-08-28
I want to reinstall Ubuntu.  It's on the same harddrive as my Windows XP.  I tried to just put the Ubuntu disk in an restart, but the partition wizard thing seems to want to keep the old installation of Ubuntu on 1.8gb of my harddrive, and I want to use all 100% of that partition for the new install, and it's only letting me use 99%.  I don't know much about partitioning, so what should I do?  Please explain.

Thanks

---

### Post by Elfy on 2008-08-28
It's tryingto make room for 2 :)

Instead of using the wizards you need to use manual. Once it's started you will have a list of the partitions available on your drives - pick the partition which currently has ubuntu installed on it, then use the edit button; you will get a new menu - there is a use-as dropdown menu - pick ext3, then find the mountpoint dropdown menu and pick /

Close the edit tool and you will be back at the partition list - check that you have used the right partition and go Next

---

