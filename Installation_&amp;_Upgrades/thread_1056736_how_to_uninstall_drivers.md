---
title: "how to uninstall drivers"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by hirohitosan on 2009-02-01
Hi there.
I installed for my printer the latest driver but reading more carefully I found that I need a less recent driver.

How can I uninstall: cndrvcups-common_1.80-1_i386.deb
ans install:         cndrvcups-common_1.60-1_i386.deb ?

thanks

---

### Post by cariboo on 2009-02-01
THe way to do it using a gui application is to go to System-->Administration-->Synaptic Package Manager, type the name of the package in the quick search bar, once it shows up highlight the file, right-click and select mark for complete temoval, then clcikc apply If you want to do it in a terminal type:

```
sudo apt-get purge cndrvcups-common
```

If prefer doing it in a terminal, as the purge options removes the configuration files if any too.

Jim

---

### Post by 80aless on 2009-02-01
you can uninstall with:
dpkg -r (packagename)  
to install the other double click on the .deb

---

### Post by hirohitosan on 2009-02-01
Thanks guys ... it works :)

---

### Post by 80aless on 2009-02-01
then put SOLVED in the thread,
cheers
ale

---

