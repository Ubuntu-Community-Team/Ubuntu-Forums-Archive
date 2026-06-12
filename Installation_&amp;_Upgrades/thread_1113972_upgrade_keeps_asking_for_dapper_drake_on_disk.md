---
title: "upgrade keeps asking for dapper drake on disk"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by horseradish on 2009-04-02
My windows broke, but luckily I had ubuntu installed.

To retrieve files from my windows, I used a dapper drake ubuntu copy on cd. 

Now I am always told I have software updates, and when I click it says it will be a partial upgrade, and then when it's loading it asks for dapper drake on cd to be inserted. 

Will these software updates be genuine or is it confusing my installed ubuntu with the dapper drake cd ? Im pretty sure I have Ibex installed.

---

### Post by Partyboi2 on 2009-04-02
Open up software sources (System>Admin>Software Sources) and on the first tab make sure that the 'Installable from cd/dvd rom' box is not ticked.

---

### Post by horseradish on 2009-04-02
Thanks.

The box seemed unticked, but in the 3rd tab there was something about ubuntu dapper so I unticked that ?

---

### Post by Partyboi2 on 2009-04-03
If you are still having a problem could you please open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by horseradish on 2009-04-03
unticking the box mentioned in the 3rd tab (to do with dapper cd) seemed to work. Also let me install the new updates.

thanks for the help

---

