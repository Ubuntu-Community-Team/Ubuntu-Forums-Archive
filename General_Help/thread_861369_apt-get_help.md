---
title: "apt-get help"
date: 2008-07-16
forum: General Help
---

### Post by theboytony on 2008-07-16
hi just installed ubuntu 7.10 desktop and i am trying to get apache to install but when i type

$ sudo apt-get install apache2

all i get is the following,i'm not behind a proxy and i can surf the internet with firefox

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package apache2
$

can anyone help

thanks

---

### Post by rossjman1 on 2008-07-16
do apt-cache search apache2, and you will find that it's not there. Apt-get can't find that package.

---

### Post by tamoneya on 2008-07-16
call update before to make sure the servers havent changed around on you.```
sudo apt-get update
sudo apt-get install apache2
```

---

### Post by jimv on 2008-07-16
If that doesn't work, post the contents of /etc/apt/sources.list

---

### Post by theboytony on 2008-07-16
ok tried the above but didn't work, had a look in sources.list and none of the tickboxes for downloadable from the internet were checked, so i checked them all and it said out of date and started downloading, then it failed. did apt-get update again then apache nd it appears to be working

thanks

---

