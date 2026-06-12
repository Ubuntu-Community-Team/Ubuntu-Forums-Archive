---
title: "Can I format a drive to NTFS in Ubuntu?"
date: 2008-09-24
forum: General Help
---

### Post by Kipposaurus on 2008-09-24
Is it possible to format a hard drive to the NTFS file system from Linux? Let's not get into why I need to, not relevant to the issue ;)

If it is how?

It's a 160GB SATA.

I have done a bit of searching and found some information stating it was possible back in 2004 but experimental, some more up to date information on this would be great.

---

### Post by sisco311 on 2008-09-24
install gparted and ntfsprogs with synaptic or from a terminal:
```
sudo aptitude install ntfsprogs gparted
```

format the drive/partition with gparted
```
gksu gparted
```

---

### Post by Kipposaurus on 2008-09-24
Thanks!

---

