---
title: "[SOLVED] FStab mounting help"
date: 2008-11-11
forum: General Help
---

### Post by Zeratul021 on 2008-11-11
Hi, I have following lines in my fstab file (along others):

#Database mount to home partition (for safety reasons)
/home/mysql /var/lib/mysql auto bind,auto,noexec 0 0

#Study materials for better access from win NTFS partition
/home/user/SCHOOL  /dev/sda3/SCHOOL  auto  bind,rw,auto,user  0  0

My question regards the second record. I would like to shortcut with mounting my SCHOOL folder on ntfs win drive to a same-named folder in my ubuntu home. The error i get is:

mount: mount point /dev/sda3/SCHOOL is not a directory

If I need a whole ntfs drive sda3 I mount it but that occurs seldom.
My home is already mounted from a different partition than a root partition is. Basically I want to achieve same effect as with the first record but I dont know how to get past the directory addressing on hardware device.
Thanks for your ideas, with regards,

Marek

---

### Post by Coreigh on 2008-11-11
```

DEVICE          MOUNTPOINT          TYPE    OPTIONS           BUMP PASS

/dev/sda3      /home/user/SCHOOL    auto    bind,rw,auto,user 0    0

```

---

### Post by Zeratul021 on 2008-11-11
> **Coreigh said:**
> DEVICE || MOUNTPOINT || OPTIONS

/dev/sda3 /home/user/SCHOOL auto bind,rw,auto,user 0 0

Well, not regarding the order of the first two arguments /dev/sda3 is not enough, I need to referrence a folder behind this, question was aimed to ask:
Is that possible?

And because

/home/mysql /var/lib/mysql auto bind,auto,noexec 0 0

binds a content of /var/lib/mysql to a fictive user folder /home/mysql

so I am not sure about the dependency of ordering as well.

Thanks, regards

Marek

---

### Post by Coreigh on 2008-11-11
I see now. OK. Mount the partition as an obscure mount like /mnt/Windows. Then in your home folder link to the SCHOOL folder.
```
sudo ln -s /mnt/Windows/SCHOOL /home/user/SCHOOL
```

SCHOOL is a link not a folder. And if you cd to your home folder before you make the link then it is just ./SCHOOL not the full path.

---

### Post by Zeratul021 on 2008-11-11
Thanks for your help ;)

---

