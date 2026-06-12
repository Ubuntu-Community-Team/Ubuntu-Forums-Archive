---
title: "umask not working?"
date: 2008-11-08
forum: General Help
---

### Post by 50words on 2008-11-08
I have a file server used by two people. I since everyone needs to be able to access and use all the files, I need every file to be created with group rw permissions.

So I set the umask to 002, which should result in permissions of rw-rw-r-- for all files created.

But when saving files from Firefox or from XP in Virtualbox, they end up as rw------

Is there any way to fix this?

---

### Post by 50words on 2008-12-22
Does anyone have a solution to my problem? I could really use the help, since it is a pain to have to keep running chmod g+rw every time my law clerk cannot access a file.

---

