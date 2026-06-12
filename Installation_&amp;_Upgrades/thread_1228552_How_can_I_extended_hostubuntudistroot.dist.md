---
title: "How can I extended host/ubuntu/dist/root.dist"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-08-01
my host/ubuntu/dist/root.dist is 97 % full, I have more free disk space on other partitions on my computer, so I want to extend the full partition. I have just run update manager but I can not install the new updates because there isn't enough place on that partition.
I will like to know if there is a console command to do this. or any other way.
I mean this part of the harddisk is full, this is where I have installed ubuntu 9.04

---

### Post by prshah on 2009-08-01
> **hoboy said:**
> my host/ubuntu/dist/root.dist is 97 % full I have more place on so I want to extend it. 

Assuming that you are using a Wubi (within windows) installation, you can resize it using the lvpm tool. [Instructions and program are here]("http://lubi.sourceforge.net/lvpm.html").

---

