---
title: "Mounting nfts drive"
date: 2008-08-02
forum: General Help
---

### Post by fedex1993 on 2008-08-02
Okay well i just got a new hard drive well actually a while ago and i used it on windows at first and i have been trying to use it on linux. The problem is ubuntu is failing to mount the nfts drive. Is there like something special that i half to do to get it mounted?

---

### Post by Diabolis on 2008-08-02
Add the mount point in your fstab file.
```
sudo gedit /etc/fstab
```

[a how to]("http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)")

---

### Post by fedex1993 on 2008-08-02
doesnt do any good. This is the error i am getting. 
saying that it was an unclean shutdown. It usually mounts on bootup for some reason right now it is not.

---

