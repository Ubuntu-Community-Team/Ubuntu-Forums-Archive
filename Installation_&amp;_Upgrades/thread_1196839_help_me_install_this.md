---
title: "help me install this"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by gt8ost4l on 2009-06-25
can anybody here help me install ubuntu live support because when i tried to install the package an error occurred  so can anybody help me install it

---

### Post by ddrichardson on 2009-06-25
What was the error?

---

### Post by gt8ost4l on 2009-06-25
> **ddrichardson said:**
> What was the error?

everytime i try to install the package i got this error 

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/)

now its saying couldnt find the package

---

### Post by oldos2er on 2009-06-25
Are you using **sudo** in your command?
```
sudo apt-get install [package name]
```

---

### Post by gt8ost4l on 2009-06-25
> **oldos2er said:**
> Are you using **sudo** in your command?
```
sudo apt-get install [package name]
```

yes i tried that n it says that its already installed newest version but its not in the menu heres the link n see if yu can install it [https://wiki.ubuntu.com/UbuntuLiveChatSupport](https://wiki.ubuntu.com/UbuntuLiveChatSupport)

---

### Post by ddrichardson on 2009-06-25
Open a terminal and type```
dpkg --listfiles packagename
```That'll tell you what was installed and where.

---

### Post by gt8ost4l on 2009-06-25
> **ddrichardson said:**
> Open a terminal and type```
dpkg --listfiles packagename
```That'll tell you what was installed and where.

can you  try to install it n tell me what happens next

---

### Post by ddrichardson on 2009-06-25
> **gt8ost4l said:**
> can you  try to install it n tell me what happens next
No, sorry helping is one thing but I'm not putting unneeded packages on a production system. If you installed it and it isn't working as expected then you should file a bug.

---

### Post by oldos2er on 2009-06-25
> **gt8ost4l said:**
> yes i tried that n it says that its already installed newest version but its not in the menu heres the link n see if yu can install it [https://wiki.ubuntu.com/UbuntuLiveChatSupport](https://wiki.ubuntu.com/UbuntuLiveChatSupport)

 Did you try restarting X, or rebooting? Occasionally menu items will not show until X is restarted.

---

### Post by gt8ost4l on 2009-06-25
> **oldos2er said:**
> Did you try restarting X, or rebooting? Occasionally menu items will not show until X is restarted.

yes a bunch of times and still nothing

---

### Post by Sub101 on 2009-06-25
It should be installed in System ==> Help.

Have you checked there?

---

### Post by gt8ost4l on 2009-06-25
> **Sub101 said:**
> It should be installed in System ==> Help.

Have you checked there?

yea its not there and i dont know why thats why im askin yu to try to see if it doesnt work for you either

---

### Post by oldos2er on 2009-06-25
Have you tried running Gaim, and checking if the channels were added?

---

