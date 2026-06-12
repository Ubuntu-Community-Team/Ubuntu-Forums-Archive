---
title: "Can't use sudo"
date: 2005-11-15
forum: General Help
---

### Post by Ocxic on 2005-11-15
whenever i try to run something as "sudo" nothing happens

$: sudo nano /etc/fstab <enter>
$: Password; *****  <enter>
$:   <- i come back to this and nothing happens, the password is correct.

And the same thing happens when i try to run anything else in Gnome desktop that requires my password, it askes for the password, and then nothing.
any ideas on what causes this?  this is a fresh intall of ubuntu 5.10 also

---

### Post by Kyral on 2005-11-15
The sudo password is your user password

---

### Post by Ocxic on 2005-11-15
$: sudo nano /etc/fstab <enter>
$: Password; *****  <enter>
***$:   <- i come back to this and nothing happens, the password is correct.***

---

### Post by Joe_lurker on 2005-11-15
Did you choose to do an 'expert' install?

-Joe

---

### Post by Ocxic on 2005-11-15
Yes, so i could make / and /home 2 seprate partitions

---

### Post by Joe_lurker on 2005-11-15
Since you did an expert install sude doesn't work correctly.  However you can fix this assuming you have a root password.  Open a terminal and enter the following commands:
```
su -
Password: ***** <-root password
visudo
```
When the editor opens up add a line to the bottom:
```
%admin    ALL=(ALL) ALL
```
just like the root entry above it.  Now exit your su to root environment and try sudo again.

-Joe

---

### Post by Ocxic on 2005-11-15
i did that, and it says now "admin is not allowed to run sudo on localhost. this incident will be reported."

---

### Post by Joe_lurker on 2005-11-15
I believe that you can do 'expert' partitioning with the default install.  I don't remember the exact terminology but I there is an option to manually edit the partition table.  But that's another thread.

-Joe

---

### Post by Joe_lurker on 2005-11-15
Lets make sure the group admin is setup.  Enter the command in a terminal:
```
less /etc/group | grep admin
```
You should get output similar to this:
```
lpadmin:x:104:user
admin:x:106:user

```
If you don't see the admin group you need to add it.  su - to root again and enter the following command:
**EDIT:** added the group name - sorry.
```
groupadd -g 106 admin
```
Then you need to add yourself to this group.  I like to edit the file /etc/group manually.  Just enter your name after the last colon (see above 'user').

-Joe

---

### Post by ed_d on 2005-11-15
Vi /etc.sudoers. Go to the "root" near the bottom. "yyp" the line and "cw" to your user name. then <Esc> w!, then <Esc> q
thats all.

---

