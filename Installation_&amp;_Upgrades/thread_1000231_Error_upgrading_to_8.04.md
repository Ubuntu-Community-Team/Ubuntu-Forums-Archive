---
title: "Error upgrading to 8.04"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by Ricardus on 2008-12-02
Hi,

 I just got done upgrading from 7.10 to 8.04, and there were a few packages that didn't install properly along the way, and at the very end of the upgrade it said that it was going to abort, and that the system might be in an unusable state.

 Well, the upgrade tool exited gracefully, and I rebooted to see what was up, and everything booted OK, and when I queried ubuntu at a terminal as to what version it was running, it said 8.04.1.

 SO, I guess my question is... what to do next.  I planned on upgrading to 8.1 but I'm not sure if I should because I'm not entirely sure that this update went properly.

 Any advice?

---

### Post by Partyboi2 on 2008-12-02
In a terminal 
```
sudo dpkg --configure -a
```
```
sudo apt-get update && sudo apt-get upgrade
``` and see if there is any packages still needing configuring  and if its fully upgraded.

---

### Post by Partyboi2 on 2008-12-02
deleted

---

### Post by Ricardus on 2008-12-02
I ran the commands you suggested, and here was the final output:

Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libgtk1.2
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by Ricardus on 2008-12-03
Hi,

I just got done upgrading from 7.10 to 8.04, and there were a few packages that didn't install properly along the way, and at the very end of the upgrade it said that it was going to abort, and that the system might be in an unusable state.

Well, the upgrade tool exited gracefully, and I rebooted to see what was up, and everything booted OK, and when I queried ubuntu at a terminal as to what version it was running, it said 8.04.1.

SO, I guess my question is... what to do next. I planned on upgrading to 8.1 but I'm not sure if I should because I'm not entirely sure that this update went properly.

Another use suggested I run these commands:

sudo dpkg --configure -a

 -and-

sudo apt-get update && sudo apt-get upgrade


 And I did.  This is what the final output said:


Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
libgtk1.2
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


 So how can I install the missing libgtk package (it's greyed out in my package manager so it won't let me check it to install it), and how do I know if my system is ready to do the 8.10 update?

---

### Post by kellemes on 2008-12-03
You did a dist upgrade?
```
apt-get dist-upgrade
```

---

### Post by bapoumba on 2008-12-03
Threads merged.

---

### Post by Ricardus on 2008-12-03
I just tried the dist upgrade, and here was the result:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libgtk1.2
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by bapoumba on 2008-12-04
Please post your sources.list file:
```
cat /etc/apt/sources.list
```

---

