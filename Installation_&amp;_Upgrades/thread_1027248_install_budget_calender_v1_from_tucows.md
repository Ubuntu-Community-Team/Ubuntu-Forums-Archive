---
title: "install budget calender v1 from tucows"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by lantana on 2009-01-01
Hi
I would like to install this program [Budget Calendar 1.0k] into ubuntu, however have no idea where to start....any suggestions would be appreciated
Thanks lantana
Simple is good....
[http://www.tucows.com/preview/500841](http://www.tucows.com/preview/500841)

---

### Post by Partyboi2 on 2009-01-01
If you have downloaded the file to your Desktop Open a terminal (Applications>Accessories>Terminal)
```
cd ~/Desktop
```extract it
```
tar xvzf Budget-Linux-bld1.sh.tgz
```Then excute the script
```
sudo sh Budget-Linux-bld1.sh
``` This will give you a list of options, if you want to install you can use
```
 sudo sh Budget-Linux-bld1.sh -i
```then to start type
```
 /usr/local/share/Budget/Budget
``` You can make a launcher by right click on your desktop and choose "create launcher" and fill in the details 
Name: Budget Calendar
Command:  /usr/local/share/Budget/Budget
Comment: whatever or leave blank

---

