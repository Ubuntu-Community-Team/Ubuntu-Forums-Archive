---
title: "Can't read files on DVD ROM drive"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by rmbsept on 2007-06-05
I have a Dell Latitude D510 with Ubuntu 7.0.4. I am trying to open files on my CD which I loaded in my DVD ROM drive. The icons have a X on them. When I double click them I get the message Access to /media/cdrom0/... was denied. Any thoughts on the problem here would be helpful. Thanks.

Richard

---

### Post by DagMan on 2007-06-05
before mounting the CD, try doing this, but substituting username for your username:
```
sudo chown username:username /media/cd*
sudo chmod 777 /media/cd*
sudo chown username:username /dev/cd*
sudo chmod 777 /dev/cd*
```
then do 
```
ls -l /dev/cdr*
```
and whatever the pointer thing -> is pointing at, run this at and for example I'll use /dev/sg0 as something to illustrate.
```
sudo chown username:username /dev/sg0
sudo chmod 777 /dev/sg0
```
Except that in all of the above you want to substitute your username for wherever I typed username and substitute whatever the ls -l /dev/cd* pointed at instead of /dev/sg0

Hopefully that will solve it, and if it does not, please paste the exact output from the terminal.

---

