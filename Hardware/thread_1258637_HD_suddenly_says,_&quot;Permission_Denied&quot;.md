---
title: "HD suddenly says, &quot;Permission Denied&quot;"
date: 2009-09-05
forum: Hardware
---

### Post by jeffdunn on 2009-09-05
I have a 13 gig HD slaved to my master. I usually mount it by clicking on it in the Places menu and entering my password.
Suddenly, although I can mount it as usual, I am unable to create folders or documents in it (the menu is grayed-out) and I can't drag stuff from the desktop onto it (permission denied), and I can't save files from an application to it (permission denied).
What can I do? What did I do? What can YOU do?
Thanks in advance for any kind assistance.

---

### Post by ithinkitschad on 2009-09-05
> **jeffdunn said:**
> I have a 13 gig HD slaved to my master. I usually mount it by clicking on it in the Places menu and entering my password.
Suddenly, although I can mount it as usual, I am unable to create folders or documents in it (the menu is grayed-out) and I can't drag stuff from the desktop onto it (permission denied), and I can't save files from an application to it (permission denied).
What can I do? What did I do? What can YOU do?
Thanks in advance for any kind assistance.

maybe open a terminal

'sudo chown username:username /media/disk/

switch username with yours and "/media/disk/" with where it mounts.

btw it probably mounts in /media
this is all a guess though, i dont know that much about linux. try it though

---

### Post by jeffdunn on 2009-09-05
> **ithinkitschad said:**
> maybe open a terminal

'sudo chown username:username /media/disk/

switch username with yours and "/media/disk/" with where it mounts.

btw it probably mounts in /media
this is all a guess though, i dont know that much about linux. try it though

Thank you 'ithinkitschad' you solved my problem now permission is granted, create folder no longer grayed out, able to drag and drop. All is normal.
For a guy that says, so modestly, I don't know much...etc, you sure helped me and I appreciate it.
Cheers

---

### Post by ithinkitschad on 2009-09-07
Well I'm glad I could help.

---

