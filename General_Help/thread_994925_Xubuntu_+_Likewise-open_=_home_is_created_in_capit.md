---
title: "Xubuntu + Likewise-open = /home is created in capital letters"
date: 2008-11-27
forum: General Help
---

### Post by Chadwill on 2008-11-27
My problem in a nutshell is that, 1 computer creates users /home in capital letters and another dosent. thus the user dont get the same /home/username folder.

my setup:

xubuntu clients that authenticates against W2K3 AD, with the Likewise-open package.

I also have a Xubuntu fileserver, with NFS share: /REMOTE

The Xubuntu clients mounts the NFS share in fstab:
*10.10.10.10:/REMOTE /home/REMOTE nfs rw,sync,hard,intr 0 0*

**Client A** is freshly installed with xubuntu 8.10, up to date and the newest Likewise package.

**Client B** was initially installed with xubuntu 8.04, but now uppgraded to 8.10.

The problem is, when a new user logs on from the **client A** the home folder is created with capital letters:
/home/REMOTE/TESTUSER1

If i log on from the other computer with a new user, it looks like this: /home/REMOTE/testuser2

So how can i get the 2 computers to use the same /home folder for each user? its the same username and uid.. just diffrent computers.

---

### Post by Chadwill on 2008-11-27
..bump

---

### Post by Chadwill on 2008-11-27
up we go..

---

### Post by Chadwill on 2008-11-28
sigh.. noone wanna reply?

---

### Post by Chadwill on 2008-11-28
anyone?

---

### Post by Chadwill on 2008-12-01
...bump again

---

