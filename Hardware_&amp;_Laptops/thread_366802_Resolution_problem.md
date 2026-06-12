---
title: "Resolution problem"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by mthakur2006 on 2007-02-21
hi all,
i can't get my laptop screen resolution to go above 1024 x 768 in ubuntu, although it does 1200 x 960 (or something like that) easily in suse 10.2.....
i have got intel 915 GMA shared graphics (Lenovo 3000 C100 0761 D7A)

Any ideas?
Thanks,
:popcorn:

---

### Post by I922sParkCir on 2007-02-21
you need to use 915resolution

make sure the community repositories are enabled, then type in this command:

> sudo apt-get install 915resolution
then
> sudo 915resolution 38 1200 960

---

### Post by mthakur2006 on 2007-02-21
thanks, m8, but it doesnot do anything! any ideas?

---

