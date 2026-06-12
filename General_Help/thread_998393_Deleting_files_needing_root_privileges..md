---
title: "Deleting files needing root privileges."
date: 2008-11-30
forum: General Help
---

### Post by vancedus on 2008-11-30
Hi,

I accidentally backed up my system in my filesystem to /media and /var/backup instead of my external harddrive.  These files are seen as root so I assume I need root privileges to delete them.  I'm not sure how to do this.  Please help, they are taking up a ridiculous amount of my Ubuntu partition.

---

### Post by doas777 on 2008-11-30
alt + F2 and enter
```
gksu nautilus
```

enter password.

a window should pop up. it will be running as root so be careful with it.

have fun

---

