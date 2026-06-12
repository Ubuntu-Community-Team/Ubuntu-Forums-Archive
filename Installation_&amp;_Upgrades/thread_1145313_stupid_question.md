---
title: "stupid question"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by anw0625 on 2009-05-01
I am new to ubuntu and trying to install a program.  I have devede on my comp. in a folder and trying to figure out how to install it.  Can anyone help?  Thanks.

---

### Post by taurus on 2009-05-01
Devede is in the repos.  Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install devede
```
It now should be in Applications -> Sound & Video.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by stretch427 on 2009-05-01
I can try:
You have to locate the folder I.E. 
/home/Documents/file_you_want_to_install_name

the location with probably be different for you
open up terminal and type:

sudo apt-get install /full_file_path

for me it would look something like 

sudo apt-get install /home/Documents/devede

Good luck

---

### Post by anw0625 on 2009-05-01
Thanks Guys!!!!!!!!!!!!!

---

