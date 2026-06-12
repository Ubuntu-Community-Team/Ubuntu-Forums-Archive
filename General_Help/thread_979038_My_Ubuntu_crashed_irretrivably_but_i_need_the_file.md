---
title: "My Ubuntu crashed irretrivably but i need the files"
date: 2008-11-11
forum: General Help
---

### Post by Cpt.Jack on 2008-11-11
I am running a home built PC and when I installed some more RAM (it was the correct one I am certin) Ubuntu wouldnt let me log on to any of my accounts I check the error codes at a freinds house and he informs me it is a known (if not common error) he also told me I couldnt get Ububtu running again but I had all my music and such on there. I need a way to access it from  my XP partiton which I am using now. Any and all help is appericiated.

---

### Post by spibou on 2008-11-11
Have you tried removing the extra RAM?

---

### Post by baeksu on 2008-11-11
To access it from Windows XP, you have to install the driver for ext2/ext3 filesystems, available here: [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html).

After that you can access the partition and copy off the files.

---

### Post by Envergure on 2008-11-11
Can't you just use your liveCD?

---

### Post by Cpt.Jack on 2008-11-12
Thanks guys Ill try them know

---

### Post by Cpt.Jack on 2008-11-12
I tried it but the only only option I have is to reformat the partition?

---

### Post by john183 on 2008-11-12
You seem to be familiar with computers, so i offer this advice. Take out the harddrive that you need information off of and put it in an external HDD case (properly connected and all) and attach it to another computer to access your files. As said before if you need to access the linux partion the ext2/3 fs driver will have to be installed on the second machine if it is a win system. but then you should be able to copy your file to another external drive or on the the second computer. I have had to do this for many of my friends who have managed to botch their OS (windows, linux and MacOS alike).

---

