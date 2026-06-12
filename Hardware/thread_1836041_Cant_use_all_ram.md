---
title: "Cant use all ram"
date: 2011-08-30
forum: Hardware
---

### Post by tsagi on 2011-08-30
I use Ubuntu 11.04 64bit on a notebook with 4gb of ram. The problem is that I seem to use only 1.8 of 4 gb. 

the output of  ~$ free -m is
                   
                     total       used       free     shared    buffers     cached
Mem:          1852       1678        173          0        144        802
-/+ buffers/cache:        731       1120
Swap:         5960          0       5960


any help please?

---

### Post by amauk on 2011-08-30
are you sure you have 4GB of RAM? (and not 2GB)

Some RAM is probably being siphoned off for an integrated graphics chip, but that won't be anywhere near 2GB

*edit*
Just FYI,
you can query exactly what memory your machine has by using
```
sudo lshw -C memory
```

---

