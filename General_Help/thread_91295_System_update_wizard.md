---
title: "System update wizard"
date: 2005-11-16
forum: General Help
---

### Post by Marcussen on 2005-11-16
I tried to run the system update wizard (adapt updater)
it asks for root password (KDE SU) 
does not recognize password
user password returns 
conversation with su failed
root password returns
conversation with su fails

same problem with Package manager (adapt) and user manager (kuser)

something is wrong as I know the root password and user password are both correct.

Any ideas

---

### Post by feathers on 2005-11-17
Are you the user that was created during install? Then you should use your password.

---

### Post by tonysathre on 2005-11-17
try using sudo apt-get update
sudo apt-get upgrade

---

### Post by Marcussen on 2005-11-17
[QUOTE=Marcussen]I tried to run the system update wizard (adapt updater)
it asks for root password (KDE SU) 
does not recognize password
user password returns 
conversation with su failed
root password returns
conversation with su fails

same problem with Package manager (adapt) and user manager (kuser)

something is wrong as I know the root password and user password are both correct.

Any ideas[/QUOTE]

I fixed the problem I logged in as root and edited the sudoers list
using visudo the only entry was 

root   ALL=(ALL)  ALL
so I added (as the last entry)
ray     ALL=(ALL)  ALL

I believe when installing in expert mode it asks for a root password, when a root is in the system it screws up the sudoers file since the root becomes the first user. And Sudo only applies to the first user without editing the sudoers file.

Now when root access is required it allows me to use the user password not root password.

I don't know if this is a bug or what.

---

### Post by ElllisD on 2005-12-25
Yes, I would agree this is a bug. It's not right & needs to stop happening.
It seems that expert mode is the only way to install without reformatting a partition. 
In my case I had formatted the partition I wanted Ubuntu on with -O dir_index over in tty2 before I let the installer have at it.
Undoubtedly you've saved alot of people alot of time posting the fix, so thank you.

---

