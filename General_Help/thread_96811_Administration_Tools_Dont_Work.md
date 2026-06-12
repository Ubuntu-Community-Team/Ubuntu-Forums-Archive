---
title: "Administration Tools Dont Work"
date: 2005-11-29
forum: General Help
---

### Post by k0ontz on 2005-11-29
Hi, 

I recently installed Ubuntu on a laptop, and everything was fine untill i tried to use the graphic administration tools under the "preferences" menu on the Gnome  bar. It accepts my password, and I see the it trying to start up, then *nothing* happens, no error message, they just dont appear, or respond when I try again.

Any help is really appreciated, I dont want to reinstall, all im doing right now is acctivating the ethernet, but later ill be running services etc.

PS. As the computer Ubuntu dosent have a connection to the internet, how can you install/update packages?

Thanks allot.

---

### Post by Specialsauce on 2005-11-29
well, if your administration applets wont open, its gonna be awful hard to connect to the internet.  had this exact same problem, though, and i tried quite alot of stuff, but the only thing that worked was a reinstall.....

---

### Post by k0ontz on 2005-11-29
Im never ever ever ever going to connect the Ubuntu machine to the net. The laptop will only be part of LANs to experiment with different disto's and learn how to use an OS other that Windows.

Im going to give it one more shot tommorow, then im going to reinstall.

---

### Post by detyabozhye on 2005-11-29
I think your problem is that your user name is not in the super user list, I'll BRB with a better explanation.

---

### Post by detyabozhye on 2005-11-29
In the termianl, type in: su
type in the root password (if you installed ubuntu using the defaults it will be same as yours)
then type in: gedit /etc/sudoers
scroll to the bottom and see if there's a line like this under "root	ALL=(ALL) ALL": [your user name]	ALL=(ALL) ALL
If there isn't, then add that, then save the file, and you should be good to go.

---

