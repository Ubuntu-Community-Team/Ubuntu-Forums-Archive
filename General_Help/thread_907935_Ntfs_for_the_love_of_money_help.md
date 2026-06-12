---
title: "Ntfs for the love of money help"
date: 2008-09-02
forum: General Help
---

### Post by Kilroth on 2008-09-02
Okay, I just duel booted my system. 2 Hard drives a 400 GB and a 80 GB 
the 400GB one is Ubuntu. The other is Windows XP. The disk partition for Windows XP is NTFS. Every time I try to copy a file from Ubuntu to Windows Xp it says I don't have permission. How do I write to that disk from my Ubuntu side

---

### Post by chadeldridge on 2008-09-02
Do you have the ntfs utilities installed in Ubuntu?

```
sudo apt-get install ntfs-3g
```

---

### Post by Dougie187 on 2008-09-02
After you install that you can go to Applications->System Tools->NTFS Configuration

---

