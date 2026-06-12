---
title: "Weird errors at the end of my dmesg"
date: 2008-08-07
forum: General Help
---

### Post by MatthijsL on 2008-08-07
Could someone help me with understanding what they mean?

[http://pastebin.ubuntu.com/35141/plain/](http://pastebin.ubuntu.com/35141/plain/)

Could it be that it has something to do with the FAT32 Recovery partition my packard bell computer uses (running a dualboot with Windows XP and Ubuntu 8.04

Thanks in advance

---

### Post by tamoneya on 2008-08-08
its possible can we see the output of ```
sudo fdisk -l
```  That way we may be able to figure out which partition those block numbers belong to.

---

