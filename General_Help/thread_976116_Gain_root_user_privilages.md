---
title: "Gain root user privilages?"
date: 2008-11-09
forum: General Help
---

### Post by mastrgamr on 2008-11-09
How can I gain admin rights on my ubuntu account? I tried the system>>user and groups>> unlock, but it doesnt work.

I want to be able to create folders in the filesystem. I found out by trying to install Mozilla Seamonkey that I can't install it because it cant create a directory.

Im noob to linux so take it easy on the linux-lingo :)

---

### Post by m_l17 on 2008-11-09
How are you trying to install Mozilla Seamonkey?

Use the sudo prefix to gain temporary root privileges:
```
$ sudo 
```

It's not a good idea to enable the root account, but if you still want to read this [read if you don't]:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

