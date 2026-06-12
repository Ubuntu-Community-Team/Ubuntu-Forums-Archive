---
title: "Bad partition size"
date: 2008-11-07
forum: General Help
---

### Post by peter07 on 2008-11-07
Something is wrong with my 8.10 installation. Ubuntu gets bad system partition /dev/sda2 size: 

```
~$ df -h
System plików            rozm. u&#380;yte dost. %u&#380;. zamont. na
/dev/sda2             9,7G  9,6G     0 100% /
```

I'm almost sure, that I have few GBs free space there, so I decide to check it using baobab from LiveCD. Analyse result show 5GB free space on /dev/sda2. It is really strange. I try fsck, resize2fs with no positive result :/

What is going on?

---

