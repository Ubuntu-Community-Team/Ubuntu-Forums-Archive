---
title: "Owner permissions"
date: 2008-08-06
forum: General Help
---

### Post by collinge on 2008-08-06
How do I set a newly created user to owner. I cannot move files from one user to the other. I am unable to get the Owner account to load correctly.

---

### Post by spiderbatdad on 2008-08-06
If you want to change the user id of a new username to replace an old user name, so that all the files owned by the old username are now owned by the new username:

```
id bob
 usermod -l bill bob
 id bill
 id bob
```

```
id bill
 usermod -u 1000 bill
 id bill
```


It is possible to loose sudo permissions for bill. You should read the usermod man page. Of course there is a gui tool for this, where you can set a new user to administrator. Then you would manually change ownership of files and directories.

---

### Post by nbayiha on 2008-08-06
Once u create a new user , go to user privileges and check administer the system .

---

