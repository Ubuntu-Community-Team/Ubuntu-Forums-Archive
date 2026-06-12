---
title: "How do I repartition hardrive"
date: 2009-08-02
forum: Hardware
---

### Post by cquigley on 2009-08-02
Hi everyone-

I have recently installed ubuntu jaunty 9.04. everything is running great. However when I try to install packages or apps I am out of room on the /home drive.

I have a 80 gb harddrive, and in vista it is partition as C: with 32 gig about 10gig of free space. and D: 35 gigs with about 33 gigs of free space. How do I repartition the hardrive to give the /home directory more remove so I can install the packages I need for apps.

thx,
  cquigley

---

### Post by x33a on 2009-08-02
actually softwares aren't installed under the /home directory. only config files for the installed software are stored there.

maybe you gave too less space to the root partition.

post the output of
```
sudo fdisk -l
df -h
```

---

