---
title: "addusers to usergroup"
date: 2008-10-17
forum: General Help
---

### Post by dapim on 2008-10-17
i know how to create user and groups
but i need to add user1 and user3 to group1
how can i do this?

---

### Post by Ms_Angel_D on 2008-10-17
Select System > Administration > Users and Groups. 

Select Unlock and enter your password

Then you can edit any profiles or groups you have.

---

### Post by dapim on 2008-10-17
i wanna do this in command line
coz i need to do it in a script

---

### Post by Ms_Angel_D on 2008-10-17
take a [look here]("http://ubuntuforums.org/showthread.php?p=990636") there is a reference list to some help with the terminal. Hopefully someone else will be along soon who can be of more assistence.

---

### Post by dapim on 2008-10-17
i was look in some others tutos, but they don't explain
how to add users into groups

---

### Post by sisco311 on 2008-10-17
```
sudo adduser *user* *group*
```
or
```
sudo usermod -a -G *group1,group2,...* *user*
```

---

