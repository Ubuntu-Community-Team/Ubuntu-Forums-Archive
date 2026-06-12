---
title: "Intrrupted Upgrade"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by sandy4linux on 2009-08-29
Hi all,
:P

We have installed Ubuntu 8.10 successfully in my friend's PC. When we tried to upgrade from 8.10 to Ubuntu 9.04, there was a DSL connection trouble and it had stopped. 

Now, we are unable to open any of these- Home folder, Music, Documents,Pictures and video folders. It shows following error..
-----------------------------------------------
Could not open the location //home/Music
No application is registered as handling this file
------------------------------------------------

 The upgrade was stopped when it was 3% completed.

I would like to use my ubuntu 8.10 for now, untill I upgrade it. Please help us...........

Regards

"LINUX- Revolutionary Human chain"

---

### Post by Partyboi2 on 2009-08-29
Try booting into recovery and from the terminal
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by sandy4linux on 2009-09-03
Thanx for your reply..I have upgraded to Jaunty. It works fine.

---

