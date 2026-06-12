---
title: "Fresh install, previous /home partition issue"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by D1ZZ4ZZT3R on 2009-11-05
ok so, i upgraded to 9.1 from 9.04 and began having issues. i reinstalled 9.1 fresh and only formatted / and swap. everything went fine except the previous /home partition needs to be mounted before i have access to it unlike before. for example, when i go to 'places' the music, video, pictures folders etc. have nothing in them. instead, i have to mount the home folder that is now a separate filesystem. is their anyway to re-integrate to make it as it was before? or, do i have to lose everything and reinstall completely anew?

---

### Post by jjcv on 2009-11-05
During the install you could have selected your existing /home to be used and then made sure that it was not formated I think.

Anyway, you will need to:

1. add your old /home filesystem to /etc/fstab 
2. move the current /home /home.old  (sudo mv /home /home.old) 
3. sudo mkdir /home
4. reboot

Once rebooted and you are happy with everything you can remove /home.old

---

### Post by D1ZZ4ZZT3R on 2009-11-05
2,3, and 4 seem self explanatory but, how do i do number 1? i tried going to the /etc folder and searched for /etc/fstab and i'm told it is not a folder. also, will i be able to move my old /home (about 500 gigs) to the other partition (about 10 with 5 free left)? this may be too complex for me.

---

### Post by michy99 on 2009-11-05
What is the output of these commands?```
sudo fdisk -l
cat /etc/fdisk
```

---

