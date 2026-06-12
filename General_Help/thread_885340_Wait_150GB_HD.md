---
title: "Wait? 150GB HD?"
date: 2008-08-10
forum: General Help
---

### Post by HBBFrum on 2008-08-10
Well, my dell computer has a stock, 5600rpm 80GB harddrive.

Now, I am wandering as to why, Ubuntu says it is a 150GB harddrive? Does ubuntu just compress files in a different way, making the files take up less space or what?

Because if it got this wrong, then I have a feeling it got allot of other things wrong also.

---

### Post by p_quarles on 2008-08-10
What is the result of the following terminal command?:
```
df -h
```

---

### Post by prshah on 2008-08-10
> **HBBFrum said:**
> computer has 80GB harddrive.
Ubuntu says it is a 150GB harddrive

Open a terminal (Applications-Accessories-Terminal) then post the output of ```
sudo fdisk -l
sudo lshw -C disk
```

Have you set any custom geometry for the hard disk in either the BIOS and/or kernel startup options? (If you don't know what this is, then you haven't!)

---

### Post by cariboo on 2008-08-10
You are also adding gvfs to your hard drive Id you are using the Disk Usage Analyzer. If you type in a terminal:

```
df -h
```

You will see the true disk usage.

Jim

---

