---
title: "CD/DVD Drive isn't working"
date: 2008-04-30
forum: Hardware
---

### Post by Uber Schwarz on 2008-04-30
I installed Ubuntu 8.04 using Wubi on my laptop but when I try to use my CD/DVD drive it says that it can't mount it. What do I do?

---

### Post by PauGNU on 2008-05-01
Try this. Open a terminal and type:
```
sudo gpasswd -a your_user cdrom
```

Restart and test if it works. It seems that your user doesn't have the right permissions, and I don't know why....

---

