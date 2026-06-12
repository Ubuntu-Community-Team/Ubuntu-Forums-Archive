---
title: "Restoring Home Folder"
date: 2008-11-19
forum: General Help
---

### Post by WaddleDee on 2008-11-19
Hello! I have a friend that has a Hardy install, and I want him to do a fresh install upgrade to Intrepid, but he does not want to loose his settings. Now I know I can copy the home folder and restore it on a new install, but it is put as someone's owership, and can't login.

Can you walk me thru this?

---

### Post by taurus on 2008-11-19
You can boot into recovery mode and change the ownership of new $HOME back to his username.

```
mv /home/new_home /home/**username**
chown -R **username**:**username** /home/**username**
```
Replace **username** with his actual login name.

p.s.  Also, make sure the entry in /etc/passwd points to the new $HOME.

---

