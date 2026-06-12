---
title: "Please help with installation of a program (3 hours trying to fix it heh)"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by Tirips214 on 2009-05-16
Hello ubuntu peeps!

I'm desperately trying to install hellanzb... I have followed several how to guides on the .net and after hours of finally getting to the .config section I have run into a huge problem.

The step tells me to use gedit to change the .config file in /etc/ and I have.  I opened gedit, put the changed I needed and hit the save icon.  Now when I start the program it still seems to be using the default .config because none of my changed seem present.

Some notes, I noticed that in /ect/ there are only the two files .config and .config.sample but when I used the open icon in gedit there are 4.. the two in the folder and then two with the exact name except they have a ~ at the end of there name.  I didn't know if that was the problem

Also when I reopen the .config file to see if the changed were saved, they were!  So I don't understand why the problem wont use the changed I've made.   Please help!

---

### Post by oldos2er on 2009-05-17
Use this command to edit hellanzb.conf:
```
gksu gedit /etc/hellanzb.conf
```
 then your changes should be saved.

---

### Post by cariboo on 2009-05-17
The ~ symbol behind a file means that it is a backup. You can safely remove them.

---

