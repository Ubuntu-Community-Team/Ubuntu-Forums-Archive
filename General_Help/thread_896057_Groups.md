---
title: "Groups"
date: 2008-08-20
forum: General Help
---

### Post by Mhurst1 on 2008-08-20
How do you change what groups a user belongs to in Ubuntu?

---

### Post by y-lee on 2008-08-20
Does this help : [Managing Ubuntu Linux Users and Groups]("http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups")

---

### Post by cdtech on 2008-08-20
usermod - Add an existing user or modify a user's existing group

To see the users associated groups, just type:
$ groups username

Add existing user "robert" to the ftp supplemental group with usermod command using the -a option to add and the -G for the supplemental group:

# usermod -a -G ftp robert

To change the existing user "robert"'s primary group to www use the small -g:

# usermod -g www robert

**P.S.**
You could just modify the "group" file (sudo pico /etc/group).

---

