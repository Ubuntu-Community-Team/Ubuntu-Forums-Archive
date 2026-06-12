---
title: "Not enough permision to edit file ?"
date: 2006-09-02
forum: Hardware &amp; Laptops
---

### Post by Nicarlo on 2006-09-02
Hi all, ive been trying to edit the etc/
X11/xorg.conf file but everytime i try i get an error saying i dont have enough permision. I tried to su - in terminal and i insert my password but it says that the password is incorrect. Im the only user on the system and i checked my priveliges and i have all of them selected. How would i go about getting enough permission to edit xorg.conf ?

---

### Post by catlett on 2006-09-02
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
In ubuntu you do not have a root account. To become root, you do not su to a root terminal. You use the x terminal and put sudo in front of the command. Sudo invokes root priveleges. When it prompts for a password, just enter your user password (i.e. the password you log on with).
For the xorg.conf file, enter this ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Crooksey on 2006-09-02
The handy thing about 6.06 is, that once you have used "sudo" in the current terminal session, you dont need to keep entering your password, just the "sudo" prefix.

---

