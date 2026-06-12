---
title: "how to change login window resolution?"
date: 2008-07-27
forum: General Help
---

### Post by emi23sgh on 2008-07-27
I had some problems from the begging with the monitor and resolutions because it did not let me to change higher than 1024X768/50-55 Hz and i changed the type of monitor on the same manufacturer but different model because my model was not listed. After doing this my resolution is how i wanted it 1280X1024/75Hz and can go higher also so no problem here but the problem is in login window where the resolution is as i think 1600X1200 and the log appears weird. So if someone had same problem and solved it i would appreciate some help on it....thx

---

### Post by buixuanduong1983 on 2008-07-27
Hi, to change the resolution of the start up screen can you try this:
sudo gedit /etc/usplash.conf
then change/add this 2 line:
xres=1280
yres=1024
(according to your desired resolution)
then save the file and then run:
sudo update-usplash-theme usplash-theme-ubuntu

Hope this help.

---

### Post by emi23sgh on 2008-07-27
it worked...thx

---

