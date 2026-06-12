---
title: "Changed my login screen and cant remember my login name"
date: 2008-11-16
forum: General Help
---

### Post by ubundf on 2008-11-16
Hi A very new user to Ubuntu here.

I have been using 8.04 for a few weeks now.

I use the ultimate v 1.9. 

All was OK until I changed the login Screen.

After initial install My surname and firstname appeared on the left side of the login box. I would click this and enter my password and login.

But in the new login (its the one with the big sunflower in the bottom right corner) there is no list with my surname and firstname on it and Im not sure of the short name I used.

Is there a way to reset the login to the old one without knowing my account or showing the accounts on the new login that are on the machine so I can choose mine.

D

---

### Post by mgol on 2008-11-16
If You have a LiveCD (for example this one You installed Ubuntu from ;)), You can run it and check what names folders in /home have. One of them is Your login name.

To mount Your hard drive from LiveCD session, You have to check what is the name of this HDD by:
```
sudo fdisk -l
```
Probably Your disk will be seen as /dev/sdb (or maybe /dev/sda). Let's say, for the convenience, that /dev/sdb is right. Then the partition You look for is one of /dev/sdb1, /dev/sdb2 etc. Create a folder for it and mount:
```
sudo mount /dev/sdbX /folder
```
If You're not sure, You can mount all of them. ;) You should look then for /home folder and check it contents - that's all.

---

