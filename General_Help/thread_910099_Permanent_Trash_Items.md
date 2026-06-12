---
title: "Permanent Trash Items"
date: 2008-09-04
forum: General Help
---

### Post by Bladerunner0324 on 2008-09-04
I emptied the trash bin after putting a folder with some contents in and while it was deleting it i opened it. Now i can not delete it or move it out of the trash bin. "Error removing file: Permission denied" Is there any way to remove it?

---

### Post by drs305 on 2008-09-04
Trash owned by root cannot be removed with normal methods. Essentially you have to assume administrator privileges to be able to delete this Trash.

I have written a tutorial which covers most of the questions you probably have. Check the link in my signature for ways to find and remove all the Trash hiding on your system.

---

### Post by porchrat on 2008-09-04
go to terminal and do this:

```
cd /home/YOUR_USERNAME/.local/share/Trash/files
sudo chown YOUR_USERNAME:YOURUSERNAME *
```

YOUR_USERNAME is the username of the user who has the stuff stuck in his trash.

You then should be able to delete whatever is in your trash

---

### Post by Bladerunner0324 on 2008-09-04
Thanks so much, ALL FIXED

---

