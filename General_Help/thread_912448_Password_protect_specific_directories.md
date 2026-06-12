---
title: "Password protect specific directories"
date: 2008-09-06
forum: General Help
---

### Post by nehsa on 2008-09-06
I'm curious whether it's possible to protect specific directories from sudoers?

For example,

I have a few people that are helping me configure my server (which is great).  I would like them to have complete root access with the exception of:

A) Navigating to other users /home directory
B) Any other folder that is private (it's my server :))

I am working on configuring LDAP now, can I do this through that? 

-Jesse

---

### Post by y@w on 2008-09-06
You can lock down permissions, but any sudoer can undo that if they like.

---

### Post by nehsa on 2008-09-06
The people I have made sudoers are people I trust so I don't believe I have to worry about them undoing anything that I put in place.

Are there utilities/methods to password protect a directory or partition?

For example, could I setup a partition to be unmounted by default and require a password to mount it?

-Nehsa

---

### Post by y@w on 2008-09-06
You can use zip to create an encrypted zip file and password-protect it if you want to go down that road. 'man zip' from the command line should get you in the right direction. If your data is a lot, it wouldn't be practical to do it that way but if you're talking about very little data then that would work.

---

