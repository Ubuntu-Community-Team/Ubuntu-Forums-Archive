---
title: "Can't create user in installation"
date: 2005-11-07
forum: General Help
---

### Post by greg_mci on 2005-11-07
Every time I want to create the user in the ubuntu 5.10 installation (i386 CD), i got the same problem. Already restarted installation 3 times:

I first insert my name and login name, then the passwort once and again. when i press enter then, I'm asked to insert my full name again, without any errror message. 

When i skip this part of the installation, finish the setup and try to boot up ubuntu, a similar input will appear, not working either.

What should I do? I desperately want Ubuntu back on my machine!



Nice greetings, 
Greg

---

### Post by taurus on 2005-11-07
I believe the order is

full name:  John Doe
user id:  jdoe
password:  j-doe
re-type password:  j-doe

---

### Post by Bachstelze on 2005-11-08
I had the same problem and I still don't know what caused it. But after partitioning my hd differently, it worked fine.

Is your /home/user/ directory mounted on a FAT32 partition ? If so, try mounting your partition to /home/user/something ant let the /home/user/ directory on the ext3 fs.

---

### Post by greg_mci on 2005-11-08
Thank you very much, HymnToLife!

That exactly was the problem, would have never thought of that. Just formatted everything with ext3, because I won't really need the FAT.

It works. :D

---

