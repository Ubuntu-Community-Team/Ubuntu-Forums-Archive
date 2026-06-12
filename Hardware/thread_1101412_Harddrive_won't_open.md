---
title: "Harddrive won't open"
date: 2009-03-20
forum: Hardware
---

### Post by Supermime on 2009-03-20
Ok I don't know if this is in the right section, but I need help with this.

Before I installed Ubuntu, I had Windows Vista Home Premium. My computer 

had 3 harddrives. One of them was about 10 GBs and was already full.

The other two had around 300 GBs each. After installing Ubuntu, I couldn't 

open the second 300 GB harddrive and the 10 GB one was no where to be found.



If you guys need anymore info or some pics, I'd gladly post them.

---

### Post by taurus on 2009-03-20
To access a harddrive, you first need to mount it.  Have you mounted any of those two drives in Ubuntu?

Open a terminal and post the outputs of these commands, running one at a time.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

