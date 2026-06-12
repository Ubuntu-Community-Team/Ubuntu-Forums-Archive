---
title: "How to clean cash/unused files?"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by vickoxy on 2009-07-22
Hi,
i installed some games (nexuiz...) and removed it-done all that through synaptic (checked "totally remove"), but my harddisk show that is still loaded with so many MB as i downladed it. So i made "search" and found this packages in /var/cache/apt/... How can i become my harddisk space back? Or how long stay these files/packages in cache? Is there some autocleaning option?

---

### Post by wojox on 2009-07-22
From the terminal:

```
sudo apt-get autoclean
```

or 

```
sudo apt-get clean
```

---

### Post by dk06 on 2009-07-22
[http://ubuntuforums.org/showthread.php?t=251771](http://ubuntuforums.org/showthread.php?t=251771)

---

### Post by vickoxy on 2009-07-22
SOLVED: Just have 1GB back-Thanks a lot!!!

BTW: How to mark the thread as solved?

---

