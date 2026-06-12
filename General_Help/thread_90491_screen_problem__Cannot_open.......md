---
title: "screen problem  Cannot open......"
date: 2005-11-15
forum: General Help
---

### Post by i0h on 2005-11-15
Hi, i have a huge problem.. i have added a new user (for remote via ssh)

and i need to use screen on that user :/ this is the output..

$ screen <hit enter>
Cannot open your terminal '/dev/pts/0' - please check.

any idea?

have tryed making other users and it still dont work it only works with my main account and root(sudo)

have tryed to add the new user to the main users group ..  really need this to work

---

### Post by nagilum on 2005-11-15
When you log in or open a terminal with your main user the said file (/dev/pts/0) will be created and the user becomes the owner of it. If you then su to another user he has no permissions on that file and screen can't access it.
To solve this you can either change the permissions of that file each time you want to start screen or add the other user (for which you call 'su') to the 'tty' group. 'tty' has by default write permission to the /dev/pts/X files.

---

### Post by i0h on 2005-11-15
the problem is that i want another user to do it.. without su..

and its not just pts/0
its all that... normaly when i starta a screen it take next if one is used..

---

