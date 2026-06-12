---
title: "What failed on start-up? I can't read that fast."
date: 2008-09-13
forum: General Help
---

### Post by Neo_The_User on 2008-09-13
Is there a file / program that tells me what failed while Ubuntu was loading? I compiled the 2.6.26.5 kernel and something right below, "Activating Swap" failed and I couldn't exactly read this but it says something about Aarmor or something. If Ubuntu makes a copy of the start-up logs somewhere in the System, could somebody tell me where that is?

Thank you so much in advance.

---

### Post by 1/0 on 2008-09-13
Log files are stored in */var/log*. You will probably find the info in */var/log/dmesg* or */var/log/syslog*.

---

### Post by Neo_The_User on 2008-09-14
Thank you.

---

### Post by cdtech on 2008-09-14
Just type in a terminal:
```
dmesg | more
```

---

### Post by Neo_The_User on 2008-09-14
cdtech, all your posts are incredibly helpful and useful. Thanks again!

---

### Post by cariboo on 2008-09-14
You could always press the Pause/Break key to stop things while you check out an error message.

Jim

---

### Post by cdtech on 2008-09-14
> **Neo_The_User said:**
> cdtech, all your posts are incredibly helpful and useful. Thanks again!

Your very welcome.

Good luck.......

---

