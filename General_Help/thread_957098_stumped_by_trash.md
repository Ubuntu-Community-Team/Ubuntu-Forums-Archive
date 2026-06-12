---
title: "stumped by trash"
date: 2008-10-23
forum: General Help
---

### Post by joexboxer on 2008-10-23
i put something in the trash and it wont delete. i get errors. it simply says 'there was an error deleting"
i copied a comic dvd to the HD & then wanted to delete it. what do i do now???
any help appreciated. it is hogging 4.7 gigs....


thanks
Joe

---

### Post by drs305 on 2008-10-23
I wrote a tutorial about the trash system. Here is the link:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

The trash may be owned by root and you will need to use administrative privileges to delete it - either by using sudo in the command line or 'gksudo nautilus' to find and delete it. Normally user trash is in /home/username/.local/share/Trash and root trash is in /root/.local/share/Trash but it can be scattered in several places on your system. I recommend looking at the link.

---

