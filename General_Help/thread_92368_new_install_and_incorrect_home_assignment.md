---
title: "new install and incorrect home assignment"
date: 2005-11-19
forum: General Help
---

### Post by ces001 on 2005-11-19
Just finished installing Ubuntu.  I am dual booting and I created a FAT32 partition to share b/w Ubuntu and Win XP.  When I was installing, it would not accept my password and user name.  I suspected it wasn't gettting written to the proper location. I was in a never ending loop of entering user, password, and real name.  

I bypassed that and finished the install.  Now, of course I can't log in because the user doesnt exist.  I tried to create a user at root, with no luck.  I used startx and created a user in Ububtu and that worked. However, under disk management, I saw that /home was the access point for my shared FAT partition and was not on the same partition as Ubuntu.

I manually created a /home/"username" as root and disabled the shared FAT32 partition. THis time it recognized the user and password, but it wouldnt let me log in because the $HOME something didnt have the proper permissions.  

Could anyone help me get /home put back in the right place and get this straightened out?  I would really appreciate it.

---

### Post by campusloop on 2005-11-19
As root you can put proper permissions for the home directory using 

chown -R username:username /home/username.


If you still have problems, you can start from scratch by deleting /home/"username" and deleting the user (you can use users-admin ). Then create the new user using users-admin.

---

### Post by gapplewagen on 2005-11-19
It sounds like you may have to reapply the default permissions to all of /home, not just /home/username.  The default permissions are 755 and ownership is root.

sudo chown -R root:root /home

sudo chmod -R 755 /home

---

### Post by gapplewagen on 2005-11-19
Oops... also for the user have you created you will need to set ownership on their directory (/home/username) or you won't be able to write to it.

sudo chown -R username:username /home/username

---

