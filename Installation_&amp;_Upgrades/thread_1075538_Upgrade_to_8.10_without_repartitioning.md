---
title: "Upgrade to 8.10 without repartitioning?"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by jmmk6 on 2009-02-20
Can a dual boot system with Win Xp on primary drive & 8.04 on secondary drive be upgraded to 8.10 without repartitioning or reformatting & retaining dual boot option ability?

---

### Post by taurus on 2009-02-20
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by jmmk6 on 2009-02-22
Thanks for the reply, but please be more specific as to where or what to look for when I follow the link provided.

---

### Post by cariboo on 2009-02-22
Start with the instructions at the top of the page and work your way through each step. If you follow the instructions exactly, you will do a sucessful upgrade. There is no need to repartition.

Jim

---

### Post by Pumalite on 2009-02-22
Don't forget to remove all third parties from your /etc/apt/sources.list, including the Medibuntu Folder if you have one.
After you do that; you can also use this:
```
sudo sed -i 's/hardy/intrepid/' /etc/apt/sources.list 
sudo apt-get update 
sudo apt-get dist-upgrade 
```

---

### Post by jmmk6 on 2009-02-23
> **cariboo907 said:**
> Start with the instructions at the top of the page and work your way through each step. If you follow the instructions exactly, you will do a sucessful upgrade. There is no need to repartition.

Jim
First try did not work for some reason.  2nd try worked - thanks to cariboo907 & taurus

---

