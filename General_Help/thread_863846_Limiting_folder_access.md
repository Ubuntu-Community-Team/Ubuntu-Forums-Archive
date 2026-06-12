---
title: "Limiting folder access"
date: 2008-07-18
forum: General Help
---

### Post by professorchaos on 2008-07-18
How can I make it so that a User that cannot access others' home folders, only its own?

---

### Post by Mister.Vash on 2008-07-18
Change the permission on the folder

For example, if your folder name was professorchaos, you could run

chmod 700 /home/professorchaos

That would change permissions on the folder so that the owner has full permission while removing access for others

---

### Post by bodhi.zazen on 2008-07-18
change the permissions of the home directories.

chmod 770 /home/user 

If you have a number of users,

sudo bash -c "for i in `ls /home`; do chmod 770 /home/$i ; done"

---

### Post by supershin on 2008-07-18
Bodhi.zazen, you used 770 instead of 700, that gives access to the owner *and* to the group, if there is one, as well. 
professorchaos, you can browse through this page to see the reasoning behind it. Just scroll to the table with value and meaning. [http://linuxcommand.org/lts0070.php#chmod](http://linuxcommand.org/lts0070.php#chmod)

What this means is, if you had users belonging to a group called X and Y then everyone in X can access the folder since the group has permission but users in group Y can't because they don't.

---

### Post by bodhi.zazen on 2008-07-18
same thing as in ubuntu at least $HOME is owned by user.user (each user has a group) so unless you have added other users to your group you have no access.

You could 750 or 700 but for all practical purposes these permissions have the same effect, unless you change ownership of $HOME or add users to a users group.

---

### Post by supershin on 2008-07-19
Ok cool, i didn't know ubuntu made a group for each user.

---

### Post by professorchaos on 2008-07-19
Many thanks, guys.

---

