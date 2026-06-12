---
title: "No cdrom"
date: 2008-11-30
forum: Hardware
---

### Post by jamil_1 on 2008-11-30
Ubuntu doesn't show my CDROM

---

### Post by fauna on 2008-12-01
I have the same problem and no one seems that interested.Tried many of the solutions on line but it seems my cdrom is not being recognized by Ubuntu and I can't figure out how to get lined up.I am very new to Linux and this does not help.   tom o  Fauna

---

### Post by cariboo on 2008-12-01
What is the output of:

```
dmesg | tail -n 10
```

when you insert a cd in the drive. The above command must be entered in a Applications-->Accessories-->Terminal. The above command will print out the last 10 lines of dmesg and may help in troubleshooting your problem.

Jim

---

